# 📖 05 System Information & Monitoring
## 📚 Resources
- https://labex.io/linuxjourney

# 📑 Table of Contents

- [⚡ Quick Index](#-quick-index)
- [💻 System Information](#-system-information)
  - [uname](#uname)
  - [uptime](#uptime)
- [📊 System Monitoring](#-system-monitoring)
  - [top](#top)
- [📄 Output Redirection](#-output-redirection)

---

# ⚡ Quick Index

| Command | Description |
|---------|-------------|
| `uname` | Show the kernel name. |
| `uname -a` | Show all available system information. |
| `uptime` | Show system uptime and load average. |
| `top` | Interactive real-time process monitor. |

---

# 💻 System Information

## uname

Display the kernel name.

```bash
uname
```

### Show all available system information

```bash
uname -a
```

Example:

```text
Linux DESKTOP 6.6.87 x86_64 GNU/Linux
```

Displays:

- Kernel name
- Hostname
- Kernel version
- Architecture
- Operating system

---

## uptime

Display:

- Current time
- System uptime
- Logged-in users
- Load average

```bash
uptime
```

Example:

```text
10:50:01 up 2 days, 3:15, 1 user, load average: 0.10, 0.05, 0.01
```

### Load Average

Represents the average system load during:

- 1 minute
- 5 minutes
- 15 minutes

Lower values generally indicate that the system is less busy.

---

# 📊 System Monitoring

## top

Interactive real-time process monitor.

```bash
top
```

Shows:

- Running processes
- CPU usage
- Memory usage
- Swap usage
- Load average
- Process resource consumption

Useful keys:

| Key | Action |
|------|--------|
| `q` | Quit |
| `P` | Sort by CPU usage |
| `M` | Sort by Memory usage |
| `k` | Kill a process |

> `top` refreshes automatically every few seconds.

---

# 📄 Output Redirection

Redirect command output to a file.

| Operator | Description |
|----------|-------------|
| `>` | Create a new file or overwrite an existing file |
| `>>` | Append output to the end of an existing file |

Example:

```bash
whoami > system_report.txt
uname -a >> system_report.txt
uptime >> system_report.txt
```

The resulting file will contain:

```text
username
Linux ...
10:50:01 up ...
```