# 👥 04 User Account Management
## 📚 Resources
- https://labex.io/linuxjourney

# 📑 Table of Contents

- [⚡ Quick Index](#-quick-index)
- [👤 Creating Users](#-creating-users)
  - [Creating a Basic User](#creating-a-basic-user)
  - [Verifying a User](#verifying-a-user)
  - [Creating a Home Directory](#creating-a-home-directory)
- [🔑 User Passwords](#-user-passwords)
  - [Setting a Password](#setting-a-password)
  - [Password Storage](#password-storage)
- [🛠️ Modifying Users](#️-modifying-users)
  - [Changing the Home Directory](#changing-the-home-directory)
  - [Changing the Default Shell](#changing-the-default-shell)
- [👥 User Groups](#-user-groups)
  - [Adding a User to a Group](#adding-a-user-to-a-group)
  - [Viewing User Groups](#viewing-user-groups)
- [🔄 Switching Users](#-switching-users)
- [🔒 Locking and Unlocking Accounts](#-locking-and-unlocking-accounts)
- [🗑️ Deleting Users](#️-deleting-users)
- [📄 Important User Files](#-important-user-files)
- [💡 Notes](#-notes)

# ⚡ Quick Index
## 👤 Creating Users

| Command | Description |
|---------|-------------|
| `sudo useradd joker` | Create a new user named `joker`. |
| `sudo useradd -m bob` | Create `bob` and create a home directory. |
| `sudo grep -w 'joker' /etc/passwd` | Verify that the user exists. |
| `id joker` | Display the user ID, primary group, and additional groups. |

---

## 🔑 Passwords

| Command | Description |
|---------|-------------|
| `sudo passwd joker` | Set or change the password for `joker`. |
| `sudo passwd -l joker` | Lock the user's password. |
| `sudo passwd -u joker` | Unlock the user's password. |

---

## 🛠️ Modifying Users

| Command | Description |
|---------|-------------|
| `sudo usermod -d /home/wayne joker` | Change the configured home directory. |
| `sudo usermod -d /home/wayne -m joker` | Change and move the home directory. |
| `sudo usermod -s /bin/bash joker` | Change the user's default shell to Bash. |
| `sudo usermod -aG sudo joker` | Add the user to the `sudo` group. |

---

## 👥 Groups and User Sessions

| Command | Description |
|---------|-------------|
| `groups joker` | Display the groups that contain `joker`. |
| `id joker` | Display detailed user and group information. |
| `su - joker` | Start a login shell as `joker`. |
| `exit` | Return to the previous user session. |

---

## 🗑️ Deleting Users

| Command | Description |
|---------|-------------|
| `sudo userdel bob` | Delete the user but normally keep their home directory. |
| `sudo userdel -r bob` | Delete the user and their home directory. |

---

# 📖 Detailed Explanations

---

# 👤 Creating Users

Linux is a multi-user operating system. Each user account has its own:

- Username
- User ID
- Primary group
- Home directory
- Default shell
- Password information
- File and directory permissions

Administrative privileges are normally required to create, modify, or delete users.

---

## Creating a Basic User

### `useradd`

The `useradd` command creates a new user account.

```bash
sudo useradd joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `sudo` | Run the command with administrator privileges. |
| `useradd` | Create a new user account. |
| `joker` | Name of the new user. |

Creating users is an administrative task. A regular user will normally receive a permission error when attempting to run `useradd` without `sudo`.

> The exact default behavior of `useradd` may vary depending on the Linux distribution and its configuration.

The command may create the account information without creating the user's home directory.

---

## Verifying a User

Linux stores basic account information in:

```text
/etc/passwd
```

To verify that `joker` was created:

```bash
sudo grep -w 'joker' /etc/passwd
```

Explanation:

| Part | Meaning |
|------|---------|
| `grep` | Search text for a matching pattern. |
| `-w` | Match the complete word. |
| `'joker'` | Text being searched for. |
| `/etc/passwd` | File containing basic user account information. |

Example output:

```text
joker:x:5001:5001::/home/joker:/bin/sh
```

The entry is divided into fields separated by colons:

```text
username:password:UID:GID:comment:home:shell
```

| Field | Example | Meaning |
|-------|---------|---------|
| Username | `joker` | User account name. |
| Password field | `x` | Encrypted password is stored in `/etc/shadow`. |
| UID | `5001` | Numeric user identifier. |
| GID | `5001` | Numeric primary group identifier. |
| Comment | Empty | Optional user information. |
| Home directory | `/home/joker` | Configured home directory path. |
| Default shell | `/bin/sh` | Program started when the user logs in. |

The presence of `/home/joker` in `/etc/passwd` does not guarantee that the directory was physically created.

Another useful verification command is:

```bash
id joker
```

Example output:

```text
uid=5001(joker) gid=5001(joker) groups=5001(joker)
```

This shows:

- User ID
- Primary group ID
- Primary group
- Additional group memberships

---

## Creating a Home Directory

Use the `-m` option to create a home directory with the user:

```bash
sudo useradd -m bob
```

Explanation:

| Part | Meaning |
|------|---------|
| `useradd` | Create a user. |
| `-m` | Create the user's home directory. |
| `bob` | Name of the new user. |

The expected home directory is:

```text
/home/bob
```

Verify the directory:

```bash
sudo ls -ld /home/bob
```

Example output:

```text
drwxr-x--- 2 bob bob 57 Jan 19 13:33 /home/bob
```

Explanation:

| Part | Meaning |
|------|---------|
| `d` | The object is a directory. |
| `rwxr-x---` | Directory permissions. |
| First `bob` | Owner of the directory. |
| Second `bob` | Group owner of the directory. |
| `57` | Directory entry size reported by the filesystem. |
| `Jan 19 13:33` | Last modification date and time. |
| `/home/bob` | Directory path. |

The exact permissions and displayed size may vary depending on the Linux distribution.

---

# 🔑 User Passwords

## Setting a Password

A newly created account may not have a usable password.

Set a password for `joker`:

```bash
sudo passwd joker
```

You will be asked to enter the password twice.

Example:

```text
New password:
Retype new password:
passwd: password updated successfully
```

Nothing appears on the screen while entering a password. This is normal and prevents other people from seeing its length.

> Use strong and unique passwords on real systems. Simple passwords should only be used inside disposable training environments.

---

## Password Storage

Basic user information is stored in:

```text
/etc/passwd
```

Encrypted password information is stored in:

```text
/etc/shadow
```

The `/etc/shadow` file has stricter permissions because it contains security-sensitive account information.

You can inspect its permissions with:

```bash
ls -l /etc/shadow
```

Reading the file normally requires root privileges:

```bash
sudo cat /etc/shadow
```

> Only inspect `/etc/shadow` in a training environment or when administration requires it. Do not copy, publish, or expose its contents.

---

# 🛠️ Modifying Users

The `usermod` command changes properties of an existing user.

---

## Changing the Home Directory

Change the home directory configured for `joker`:

```bash
sudo usermod -d /home/wayne joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `usermod` | Modify an existing user account. |
| `-d` | Set a new home directory path. |
| `/home/wayne` | New home directory path. |
| `joker` | User being modified. |

Verify the change:

```bash
sudo grep -w 'joker' /etc/passwd
```

### Important difference

The following command only changes the path configured in the user account:

```bash
sudo usermod -d /home/wayne joker
```

It does not necessarily create the new directory or move the user's existing files.

To change the path and move the existing home directory, use:

```bash
sudo usermod -d /home/wayne -m joker
```

| Option | Meaning |
|--------|---------|
| `-d` | Define the new home directory. |
| `-m` | Move the current home contents to the new location. |

It is safer to perform this change while the affected user is logged out.

---

## Changing the Default Shell

A shell interprets the commands entered in a terminal.

Common shells include:

| Shell | Description |
|-------|-------------|
| `/bin/sh` | Basic POSIX-compatible shell. |
| `/bin/bash` | Bash shell with interactive and scripting features. |
| `/bin/zsh` | Shell with additional interactive features. |
| `/usr/sbin/nologin` | Prevents normal interactive login. |

Change `joker` from `/bin/sh` to Bash:

```bash
sudo usermod -s /bin/bash joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `usermod` | Modify the user account. |
| `-s` | Set the user's login shell. |
| `/bin/bash` | New shell. |
| `joker` | User being modified. |

Verify the change:

```bash
sudo grep -w 'joker' /etc/passwd
```

The entry should now end with:

```text
/bin/bash
```

You can list valid shells registered on the system with:

```bash
cat /etc/shells
```

---

# 👥 User Groups

Groups allow permissions and administrative responsibilities to be assigned to multiple users.

A user has:

- One primary group
- Zero or more supplementary groups

---

## Adding a User to a Group

On Ubuntu and Debian-based systems, the `sudo` group normally grants permission to use administrative commands through `sudo`.

Add `joker` to the `sudo` group:

```bash
sudo usermod -aG sudo joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `usermod` | Modify a user account. |
| `-a` | Append without removing existing supplementary groups. |
| `-G` | Specify supplementary groups. |
| `sudo` | Group being added. |
| `joker` | User being modified. |

The options are commonly written together:

```text
-aG
```

### Why `-aG` matters

Using only `-G` can replace the user's current supplementary groups.

For example:

```bash
sudo usermod -G sudo joker
```

may remove `joker` from other supplementary groups.

Using:

```bash
sudo usermod -aG sudo joker
```

adds the group without removing existing memberships.

> On Red Hat-based systems, administrative access is commonly granted through the `wheel` group instead of `sudo`.

---

## Viewing User Groups

Display the groups assigned to `joker`:

```bash
groups joker
```

Example:

```text
joker : joker sudo
```

For more detailed information:

```bash
id joker
```

Example:

```text
uid=5001(joker) gid=5001(joker) groups=5001(joker),27(sudo)
```

A user may need to log out and log back in before a new group membership becomes active in their session.

---

# 🔄 Switching Users

Use `su` to switch to another user:

```bash
su - joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `su` | Switch user. |
| `-` | Start a full login shell and load the user's environment. |
| `joker` | Target user. |

You will normally be asked for `joker`'s password.

After switching, verify the current user:

```bash
whoami
```

Expected output:

```text
joker
```

To return to the previous user:

```bash
exit
```

---

## Testing Administrative Access

After adding `joker` to the `sudo` group, switch to the account:

```bash
su - joker
```

Run a harmless administrative command:

```bash
sudo whoami
```

Enter `joker`'s password when requested.

Expected output:

```text
root
```

This confirms that the user can execute commands through `sudo`.

Using `sudo whoami` is safer for testing than displaying sensitive system files.

Return to the previous account:

```bash
exit
```

---

# 🔒 Locking and Unlocking Accounts

Sometimes an account must be disabled temporarily without deleting its files or configuration.

---

## Locking an Account

Lock `joker`'s password:

```bash
sudo passwd -l joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `passwd` | Manage account passwords. |
| `-l` | Lock the password. |
| `joker` | Target user. |

Try switching to the user:

```bash
su - joker
```

Password authentication should fail.

> Locking the password does not necessarily terminate sessions that are already active. It may also not block every possible authentication method, such as an already configured SSH key.

---

## Unlocking an Account

Unlock the password:

```bash
sudo passwd -u joker
```

Explanation:

| Part | Meaning |
|------|---------|
| `passwd` | Manage account passwords. |
| `-u` | Unlock the password. |
| `joker` | Target user. |

Try again:

```bash
su - joker
```

After entering the password, the login should succeed.

Return to the original user:

```bash
exit
```

---

# 🗑️ Deleting Users

The `userdel` command removes user accounts.

We can delete the `bob` account created earlier.

---

## Deleting Only the Account

```bash
sudo userdel bob
```

This removes the user account but normally leaves the home directory and its files behind.

---

## Deleting the Account and Home Directory

```bash
sudo userdel -r bob
```

Explanation:

| Part | Meaning |
|------|---------|
| `userdel` | Delete a user account. |
| `-r` | Remove the home directory and mail spool. |
| `bob` | User being deleted. |

Verify that the account no longer exists:

```bash
sudo grep -w 'bob' /etc/passwd
```

Verify that the home directory was removed:

```bash
sudo ls -ld /home/bob
```

Expected results:

- `grep` returns no matching user.
- `ls` reports that `/home/bob` does not exist.

You can also use:

```bash
id bob
```

Expected output:

```text
id: 'bob': no such user
```

> Before deleting a real account, verify whether its files, scheduled jobs, running processes, or application ownership must be preserved.

---

# 📄 Important User Files

| File | Purpose |
|------|---------|
| `/etc/passwd` | Basic user account information. |
| `/etc/shadow` | Encrypted password and password-aging information. |
| `/etc/group` | Group definitions and memberships. |
| `/etc/gshadow` | Protected group security information. |
| `/etc/skel` | Template files copied into new home directories. |
| `/etc/shells` | List of approved login shells. |
| `/etc/sudoers` | Main configuration for `sudo` permissions. |
| `/etc/sudoers.d/` | Additional `sudo` configuration files. |

Do not edit `/etc/sudoers` directly with a normal text editor.

Use:

```bash
sudo visudo
```

`visudo` validates the configuration before saving it and helps prevent syntax errors that could break administrative access.

---

# 💡 Notes

- Linux supports multiple users with separate permissions and environments.
- `useradd` creates a user account.
- `useradd -m` also creates a home directory.
- `passwd` sets or changes a user's password.
- Password hashes are stored in `/etc/shadow`.
- `usermod` modifies an existing account.
- `usermod -d` changes the configured home directory.
- `usermod -d PATH -m` changes and moves the home directory.
- `usermod -s` changes the default login shell.
- `usermod -aG` safely adds a supplementary group.
- `groups` and `id` display group membership.
- `su - username` starts a login session as another user.
- `sudo whoami` is a simple way to test administrative access.
- `passwd -l` locks password authentication.
- `passwd -u` unlocks password authentication.
- `userdel -r` removes a user and their home directory.
- User management commands often require `sudo`.
- New group permissions may require the user to log out and back in.
- Avoid granting `sudo` access unless it is genuinely required.
- Be careful when modifying or deleting real user accounts.
- Commands and default behaviors may vary slightly between Linux distributions.