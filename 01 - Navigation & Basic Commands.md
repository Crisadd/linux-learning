# 📖 01 Navigation & Basic Commands
## 📚 Resources

- https://labex.io/linuxjourney

# 🚀 Quick Start with Linux
> **The best way to learn Linux (and programming in general) is by doing.**
> Practice makes perfect.


# 📑 Table of Contents
- [⚡ Quick Index](#-quick-index)
- [👤 User Information](#-user-information)
- [📂 Navigation](#-navigation)
- [📄 Listing Files](#-listing-files)
- [📁 File Management](#-file-management)
  - [Creating Files](#creating-files)
  - [Creating Directories](#creating-directories)
  - [Copying Files & Directories](#copying-files--directories)
  - [Moving & Renaming](#moving--renaming)
  - [Removing Files & Directories](#removing-files--directories)
- [🧹 Terminal Utilities](#-terminal-utilities)
- [📅 Date & Time](#-date--time)
- [🧮 Calculations](#-calculations)
- [🎨 Fun](#-fun)
- [💡 Notes](#-notes)


# ⚡ Quick Index
## 👤 User Information

| Command | Description |
|---------|-------------|
| `whoami` | Show the current username. |
| `id` | Show user and group information. |
| `id -un` | Show only the username. |

---

## 📂 Navigation

| Command | Description |
|---------|-------------|
| `pwd` | Print the current working directory. |
| `cd` | Change directory. |
| `cd ~` | Go to the home directory. |

---

## 📄 Listing Files

| Command | Description |
|---------|-------------|
| `ls` | List files and directories. |
| `ls ~` | List the home directory. |
| `ls -l` | Long format listing. |
| `ls -a` | Show hidden files. |
| `ls -la` | Long listing including hidden files. |
| `ls -R` | List directories recursively. |

---

## 📁 File Management

### Creating Files

| Command | Description |
|---------|-------------|
| `touch` | Create an empty file. |
| `echo` | Print text. |
| `>` | Redirect output into a file. |
| `.filename` | Hidden files begin with a dot (`.`). |

### Creating Directories

| Command | Description |
|---------|-------------|
| `mkdir` | Create a directory. |

### Copying Files & Directories

| Command | Description |
|---------|-------------|
| `cp` | Copy files. |
| `cp -r` | Copy directories recursively. |

### Moving & Renaming

| Command | Description |
|---------|-------------|
| `mv` | Move or rename files and directories. |

### Removing Files & Directories

| Command | Description |
|---------|-------------|
| `rm` | Remove a file. |
| `rm -i` | Remove with confirmation. |
| `rmdir` | Remove an empty directory. |
| `rm -r` | Remove directories recursively. |
| `rm -rf` | Force recursive removal. | is one of the most dangerous Linux commands. Use it carefully.

---

## 🧹 Terminal Utilities

| Command | Description |
|---------|-------------|
| `clear` | Clear the terminal. |
| `Ctrl + L` | Keyboard shortcut to clear the terminal. |

---

## 📅 Date & Time

| Command | Description |
|---------|-------------|
| `date` | Show current date and time. |
| `cal` | Display a calendar. |

---

## 🧮 Calculations

| Command | Description |
|---------|-------------|
| `expr` | Perform basic arithmetic. |

---

## 🎨 Fun

| Command | Description |
|---------|-------------|
| `figlet` | Create ASCII art text. |

---

# 📖 Detailed Explanations

---

# 👤 User Information

## `whoami`

Displays the username of the current user.

Useful when working on different machines or accounts.

```bash
whoami
```

---

## `id`

Displays information about the current user and the groups they belong to.

Linux uses **groups** to determine permissions and access rights.

```bash
id
```

Example:

```text
uid=1000(user) gid=1000(user) groups=1000(user),27(sudo)
```

---

## `id -un`

Prints only your username.

```bash
id -un
```

---

# 📂 Navigation

## Home Directory (`~`)

Every Linux user has a **home directory**.

The symbol:

```text
~
```

is a shortcut for your home directory.

---

## `pwd`

Prints your current working directory.

```bash
pwd
```

---

## `cd`

Changes your current directory.

```bash
cd Documents
```

---

## `cd ~`

Go directly to your home directory.

```bash
cd ~
```

---

# 📄 Listing Files

## `ls`

Lists files and directories.

```bash
ls
```

---

## `ls ~`

Lists the contents of your home directory.

```bash
ls ~
```

---

## `ls -l`

Displays files in **long format**.

```bash
ls -l
```

Shows:

- Permissions
- Owner
- Group
- Size
- Date
- File name

---

## `ls -a`

Displays hidden files.

```bash
ls -a
```

Files beginning with `.` are hidden.

---

## `ls -la`

Combines both options.

```bash
ls -la
```

Shows:

- Hidden files
- Detailed information

---

## `ls -R`

Lists directories recursively.

```bash
ls -R
```

> **Note**
>
> `-R` (uppercase) means **recursive listing**.

---

# 📁 File Management

## Creating Files

### `touch`

Creates an empty file.

```bash
touch file1.txt
```

If the file already exists, only its timestamp is updated.

---

### `echo`

Prints text to the terminal.

```bash
echo "Hello Linux"
```

---

### Redirect Output (`>`)

Writes text into a file.

```bash
echo "Hello Linux" > file2.txt
```

If the file exists, its contents are replaced.

---

### Hidden Files

Files beginning with a dot (`.`) are hidden.

```bash
echo "Hidden file" > .hiddenfile
```

---

## Creating Directories

### `mkdir`

Creates a directory.

```bash
mkdir testdir
```

---

## Copying Files & Directories

### Copy a file

```bash
cp file1.txt file1_copy.txt
```

---

### Copy to another directory

```bash
cp file2.txt testdir/
```

---

### Copy a directory

```bash
cp -r testdir testdir_copy
```

The `-r` option means **recursive**.

---

## Moving & Renaming

### Rename a file

```bash
mv file1.txt newname.txt
```

---

### Move a file

```bash
mv file1.txt testdir/
```

---

### Rename a directory

```bash
mv testdir_copy new_testdir
```

---

### Move and rename

```bash
mv testdir/newname.txt ./original_file1.txt
```

---

## Removing Files & Directories

> ⚠️ **Warning**
>
> Files deleted with `rm` are usually **permanent**.

---

### Remove a file

```bash
rm original_file1.txt
```

---

### Remove with confirmation

```bash
rm -i file2.txt
```

The terminal will ask:

```text
rm: remove regular file 'file2.txt'?
```

Type:

```text
y
```

to confirm.

---

### Remove an empty directory

```bash
rmdir testdir
```

---

### Remove a directory recursively

```bash
rm -r testdir
```

---

### Force removal

```bash
rm -rf temp_dir
```

> 🚨 **Extreme Caution**
>
> `rm -rf` deletes files permanently without confirmation.
>
> Always verify the path before pressing **Enter**.

---

# 🧹 Terminal Utilities

## Clear the terminal

Keyboard shortcut:

```text
Ctrl + L
```

or

```bash
clear
```

---

# 📅 Date & Time

## Current date

```bash
date
```

---

## Calendar

```bash
cal
```

---

## Calendar for a specific year

```bash
cal 2025
```

---

# 🧮 Calculations

## Addition

```bash
expr 5 + 3
```

---

## Multiplication

```bash
expr 24 \* 7
```

`expr` supports:

- Addition (`+`)
- Subtraction (`-`)
- Multiplication (`*`)
- Division (`/`)

---

# 🎨 Fun

## ASCII Art

Create text using ASCII art.

```bash
figlet Linux
```

---

# 💡 Notes

- `~` always refers to your **home directory**.
- Files beginning with `.` are hidden.
- `Ctrl + L` is the fastest way to clear the terminal.
- `cp -r` copies recursively.
- `rm -r` removes recursively.
- `ls -R` lists recursively.
- `rm -rf` is one of the most dangerous Linux commands. Use it carefully.