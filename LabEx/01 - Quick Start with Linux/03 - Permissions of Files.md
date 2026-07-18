# 📖 03 File Permissions
## 📚 Resources
- https://labex.io/linuxjourney

# 📑 Table of Contents
- [⚡ Quick Index](#-quick-index)
- [👤 Ownership](#-ownership)
  - [Viewing Ownership](#viewing-ownership)
  - [Changing Ownership](#changing-ownership)
  - [Recursive Ownership](#recursive-ownership)
- [🔐 File Permissions](#-file-permissions)
  - [Understanding Permission Strings](#understanding-permission-strings)
  - [Numeric Permissions](#numeric-permissions)
- [📂 Directory Permissions](#-directory-permissions)
- [🎯 Symbolic Permissions](#-symbolic-permissions)
- [💡 Notes](#-notes)

# ⚡ Quick Index
## 👤 Ownership

| Command | Description |
|---------|-------------|
| `ls -l file` | Display ownership and permissions. |
| `chown user:group file` | Change owner and group. |
| `chown -R user:group dir` | Change ownership recursively. |
SUDO chown user:group file  | SUDO allows you to execute commands with the privileges of the superuser                     (root).|

---

## 🔐 File Permissions

| Command | Description |
|---------|-------------|
| `chmod 700 file` | Set permissions using numeric notation. |
| `chmod 755 dir` | Common directory permissions. |

---

## 📂 Directory Permissions

| Command | Description |
|---------|-------------|
| `ls -ld directory` | Show directory permissions. |
| `chmod -R 755 directory` | Change permissions recursively. |

Examples:

| Number | Meaning |
|---------|---------|
| 7 | Read + Write + Execute (4+2+1) |
| 6 | Read + Write |
| 5 | Read + Execute |
| 4 | Read only |
| 0 | No permissions |

---

## 🎯 Symbolic Permissions

| Command | Description |
|---------|-------------|
| `chmod u+x file` | Add execute permission for the owner. |
| `chmod g+w file` | Add write permission for the group. |
| `chmod o-r file` | Remove read permission for others. |
| `chmod a+x file` | Add execute permission for everyone. |

---

# 📖 Detailed Explanations

---

# 👤 Ownership

Ownership determines **who controls a file or directory**.

Each file has:

- An **owner** (user)
- A **group**

---

## Viewing Ownership

### `ls -l`

Displays detailed information about a file.

```bash
ls -l example.txt
```

Example output:

```text
-rw-rw-r-- 1 labex labex 0 Jul 29 15:11 example.txt
```

Explanation:

| Part | Meaning |
|------|---------|
| `-` | Regular file |
| `rw-rw-r--` | File permissions |
| `labex` | Owner |
| `labex` | Group |
| `0` | File size (bytes) |
| `Jul 29 15:11` | Last modified date |
| `example.txt` | File name |

---

## Changing Ownership

### `chown`

Changes the owner and group of a file.

```bash
sudo chown root:root example.txt
```

Explanation:

- `sudo` runs the command with administrator privileges.
- `chown` changes ownership.
- `root:root` means:
  - Owner → `root`
  - Group → `root`
- `example.txt` is the target file.

Without `sudo`, you'll usually receive a **Permission denied** error.

---

## Recursive Ownership

First create a sample directory structure:

```bash
mkdir -p new-dir/subdir
```

```bash
echo "Hello, world" > new-dir/file1.txt
```

```bash
echo "Another file" > new-dir/subdir/file2.txt
```

View the ownership:

```bash
ls -lR new-dir
```

Change ownership recursively:

```bash
sudo chown -R root:root new-dir
```

The `-R` option tells `chown` to change ownership for:

- The directory
- All files
- All subdirectories

Without `-R`, only the top-level directory would change ownership.

---

# 🔐 File Permissions

## Understanding Permission Strings

Example:

```text
-rw-rw-r--
```

Breakdown:

| Section | Meaning |
|---------|---------|
| `-` | Regular file |
| `rw-` | Owner permissions |
| `rw-` | Group permissions |
| `r--` | Others permissions |

Permission letters:

| Letter | Meaning |
|---------|---------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |
| `-` | Permission denied |

---

## Numeric Permissions

### `chmod`

Changes file permissions.

```bash
sudo chmod 700 example.txt
```

Permission values:

| Value | Permission |
|------:|------------|
| 4 | Read |
| 2 | Write |
| 1 | Execute |

The values are added together.


### Understanding `700`

| User | Value | Permissions |
|------|------:|-------------|
| Owner | 7 | Read, Write, Execute |
| Group | 0 | None |
| Others | 0 | None |

---

# 📂 Directory Permissions

Create a directory:

```bash
mkdir ~/test-dir
```

Give only the owner full access:

```bash
chmod 700 ~/test-dir
```

View directory permissions:

```bash
ls -ld ~/test-dir
```

Example:

```text
drwx------ 2 labex labex 4096 Jul 29 15:45 /home/labex/test-dir
```

Notice the first character:

```text
d
```

It indicates a **directory**.

Directory permissions work slightly differently.

| Permission | Meaning |
|------------|---------|
| Read (`r`) | List directory contents. |
| Write (`w`) | Create, rename, or delete files. |
| Execute (`x`) | Enter the directory (`cd`). |

---

### Common Directory Permissions

```bash
chmod -R 755 ~/test-dir
```

The `-R` option applies permissions recursively.

### Understanding `755`

| User | Value | Permissions |
|------|------:|-------------|
| Owner | 7 | Read, Write, Execute |
| Group | 5 | Read, Execute |
| Others | 5 | Read, Execute |

Result:

```text
drwxr-xr-x
```

Now:

- The owner has full access.
- Everyone else can view and enter the directory.
- Only the owner can modify its contents.

---

# 🎯 Symbolic Permissions

Instead of numbers, `chmod` can use symbolic notation.

Create a simple script:

```bash
cd ~/project
```

```bash
echo '#!/bin/bash' > script.sh
```

```bash
echo 'echo "Hello, World"' >> script.sh
```

Try running it:

```bash
./script.sh
```

You'll receive:

```text
Permission denied
```

because the file doesn't have execute permission.

Add execute permission for the owner:

```bash
chmod u+x script.sh
```

Run it again:

```bash
./script.sh
```

Output:

```text
Hello, World
```

### Symbolic Notation

| Symbol | Meaning |
|---------|---------|
| `u` | User (owner) |
| `g` | Group |
| `o` | Others |
| `a` | All users |

Operators:

| Operator | Meaning |
|----------|---------|
| `+` | Add permission |
| `-` | Remove permission |

Examples:

```bash
chmod u+x script.sh
```

Add execute permission to the owner.

```bash
chmod g+w file.txt
```

Add write permission to the group.

```bash
chmod o-r file.txt
```

Remove read permission from others.

```bash
chmod a+x script.sh
```

Give execute permission to everyone.

---

# 💡 Notes

- Every file has an **owner** and a **group**.
- `ls -l` displays ownership and permissions.
- `chown` changes ownership.
- `chown -R` changes ownership recursively.
- `chmod` changes permissions.
- Numeric notation uses values:
  - `4` = Read
  - `2` = Write
  - `1` = Execute
- `700` gives full access only to the owner.
- `755` is one of the most common directory permission settings.
- `ls -ld` displays directory permissions instead of its contents.
- Symbolic notation (`u+x`, `g+w`, etc.) modifies individual permissions without recalculating numeric values.
- Scripts need execute (`x`) permission before they can be run.
- Be careful when using `sudo`, `chown`, and `chmod`; incorrect permissions can affect system security.