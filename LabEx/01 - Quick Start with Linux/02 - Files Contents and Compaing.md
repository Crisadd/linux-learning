# 📖 02 File Contents & Comparing
## 📚 Resources
- https://labex.io/linuxjourney

# 📑 Table of Contents

- [⚡ Quick Index](#-quick-index)
- [📄 Viewing File Contents](#-viewing-file-contents)
  - [Display Entire File](#display-entire-file)
  - [Display with Line Numbers](#display-with-line-numbers)
- [🔝 Viewing the Beginning of a File](#-viewing-the-beginning-of-a-file)
  - [First Lines](#first-lines)
  - [First Bytes](#first-bytes)
- [🔚 Viewing the End of a File](#-viewing-the-end-of-a-file)
  - [Last Lines](#last-lines)
  - [Last Bytes](#last-bytes)
- [⚖️ Comparing Files & Directories](#️-comparing-files--directories)
  - [Compare Files](#compare-files)
  - [Compare Directories](#compare-directories)
- [💡 Notes](#-notes)

# ⚡ Quick Index

## 📄 Viewing File Contents

| Command | Description |
|---------|-------------|
| `cat file` | Display the entire contents of a file. |
| `cat -n file` | Display file contents with line numbers. |

---

## 🔝 Viewing the Beginning of a File

| Command | Description |
|---------|-------------|
| `head file` | Display the first 10 lines. |
| `head -n1 file` | Display the first line. |
| `head -c1 file` | Display the first byte (character). |

---

## 🔚 Viewing the End of a File

| Command | Description |
|---------|-------------|
| `tail file` | Display the last 10 lines. |
| `tail -n1 file` | Display the last line. |
| `tail -c1 file` | Display the last byte (character). |

---

## ⚖️ Comparing Files & Directories

| Command | Description |
|---------|-------------|
| `diff file1 file2` | Compare two files. |
| `diff -r dir1 dir2` | Compare directories recursively. |

---

# 📖 Detailed Explanations

---

# 📄 Viewing File Contents

## Display Entire File

### `cat`

Displays the complete contents of a file.

```bash
cat /tmp/hello
```

Useful for quickly viewing small text files.

---

## Display with Line Numbers

### `cat -n`

Displays the contents of a file with line numbers.

```bash
cat -n /tmp/hello
```

The `-n` option numbers every output line, making it easier to reference specific lines.

---

# 🔝 Viewing the Beginning of a File

## First Lines

### `head`

By default, `head` displays the first **10 lines** of a file.

```bash
head /tmp/hello
```

---

### `head -n1`

Displays only the first line.

```bash
head -n1 /tmp/hello
```

The number after `-n` can be changed.

Examples:

```bash
head -n5 /tmp/hello
```

```bash
head -n20 /tmp/hello
```

---

## First Bytes

### `head -c1`

Displays only the first byte (usually the first character).

```bash
head -c1 /tmp/hello
```

Like `-n`, the number can be changed.

Example:

```bash
head -c20 /tmp/hello
```

---

# 🔚 Viewing the End of a File

## Last Lines

### `tail`

By default, `tail` displays the last **10 lines**.

```bash
tail /tmp/hello
```

---

### `tail -n1`

Displays only the last line.

```bash
tail -n1 /tmp/hello
```

The value after `-n` can be any number.

Example:

```bash
tail -n5 /tmp/hello
```

---

## Last Bytes

### `tail -c1`

Displays the last byte (character) of the file.

```bash
tail -c1 /tmp/hello
```

> **Note**
>
> Sometimes no visible output appears because the last character is often a newline (`\n`).

---

# ⚖️ Comparing Files & Directories

## Compare Files

### `diff`

Compares two files.

```bash
diff file1 file2
```

`diff` shows the changes required to make the first file identical to the second.

It does **not** care which file was created first—it only compares their current contents.

---

## Compare Directories

### `diff -r`

Compares two directories recursively.

```bash
diff -r ~/Desktop ~/Code
```

The `-r` option tells `diff` to compare all files inside subdirectories as well.

---

# 💡 Notes

- `cat` displays the entire contents of a file.
- `cat -n` adds line numbers to the output.
- `head` displays the beginning of a file.
- `tail` displays the end of a file.
- Without options, both `head` and `tail` display **10 lines**.
- `-n` specifies the number of lines to display.
- `-c` specifies the number of bytes (characters) to display.
- `diff` compares the contents of two files.
- `diff -r` compares entire directory trees recursively.
```cat command to display the contents of a file:

