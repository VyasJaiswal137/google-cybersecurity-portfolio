# Course 4 — Module 3 Notes
## Linux Navigation, File Management & Access Control

---

## 1. Filesystem Hierarchy Standard (FHS) & System Navigation

The **Filesystem Hierarchy Standard (FHS)** defines how files and directories are organized in a Linux system. Each directory has a specific purpose, which makes it easier to navigate and manage the operating system.

### Basic Linux Filesystem Structure

```text
/ (Root Directory)
├── bin/    → Essential binary executables
├── etc/    → System configuration files
├── home/   → User home directories
│   ├── analyst/
│   └── analyst2/
├── tmp/    → Temporary files
└── mnt/    → Mount points for external storage
```

### Important FHS Directories

| Directory | Purpose |
|---|---|
| `/` | The **root directory**, which is the starting point of the entire Linux filesystem. |
| `/home` | Contains the personal directories of users, such as `/home/analyst`. The shortcut `~/` usually refers to the current user's home directory. |
| `/bin` | Contains essential executable programs required for basic system operations. |
| `/etc` | Stores system-wide configuration files. |
| `/tmp` | Stores temporary files. Because multiple users and processes may have access to this directory, it can be an important security consideration. |
| `/mnt` | Commonly used as a mount point for external drives and other filesystems, such as USB storage. |

### Directory Navigation Commands

#### `pwd`

Displays the **absolute path** of the directory you are currently working in.

```bash
pwd
```

#### `whoami`

Shows the username of the user currently logged into the session.

```bash
whoami
```

#### `ls`

Lists the files and directories in the current or specified location.

```bash
ls
```

Useful options:

```bash
ls -a
```

Shows all files, including hidden files whose names begin with `.`.

```bash
ls -l
```

Shows detailed information such as permissions, owner, group, file size, and modification time.

```bash
ls -la
```

Combines the detailed listing with hidden files.

#### `cd`

Changes the current working directory.

**Absolute path:**

```bash
cd /home/analyst/logs
```

**Relative path:**

```bash
cd ../projects
```

Here:

- `.` means the **current directory**
- `..` means the **parent directory**

---

# 2. File Operations & Content Inspection

Linux provides several commands for creating, viewing, modifying, moving, and deleting files.

## Reading File Contents

### `cat`

Displays the complete contents of a file.

```bash
cat file.txt
```

### `head`

Displays the beginning of a file. By default, it shows the first **10 lines**.

```bash
head file.txt
```

To display a specific number of lines:

```bash
head -n 5 file.txt
```

This displays the first 5 lines.

### `tail`

Displays the end of a file. It is particularly useful when checking **recent entries in log files**.

```bash
tail log.txt
```

### `less`

Opens a file in a scrollable, page-by-page viewer.

```bash
less file.txt
```

Common controls:

| Key | Action |
|---|---|
| `Space` | Move one page down |
| `b` | Move one page up |
| `↓` | Move down one line |
| `↑` | Move up one line |
| `q` | Quit the viewer |

---

## Creating, Modifying & Managing Files

### `mkdir` and `rmdir`

`mkdir` creates a new directory, while `rmdir` removes an **empty** directory.

```bash
mkdir reports
rmdir reports
```

### `touch` and `rm`

`touch` creates an empty file, while `rm` removes a file.

```bash
touch notes.txt
rm notes.txt
```

> **Note:** `rm` permanently removes the file, so use it carefully.

### `mv`

Moves a file or directory. It can also be used to rename files.

```bash
mv old.txt new.txt
```

### `cp`

Copies a file or directory to another location.

```bash
cp file.txt /home/analyst/
```

### `nano`

A simple terminal-based text editor.

```bash
nano file.txt
```

Useful shortcuts:

- `Ctrl + O` → Save the file
- `Ctrl + X` → Exit Nano

---

## Output Redirection

Linux allows the output of a command to be redirected into a file.

### `>` — Overwrite

Writes the output into a file and **replaces its existing contents**.

```bash
ls > files.txt
```

### `>>` — Append

Adds the output to the **end of an existing file** without removing its previous contents.

```bash
ls >> files.txt
```

---

# 3. Data Searching & Filtering

Linux commands can be combined to search, filter, and locate specific information efficiently.

## `grep`

`grep` searches for lines that match a particular word or pattern.

```bash
grep "error" log.txt
```

This displays lines containing the word `error`.

---

## `|` — Pipe

The pipe operator sends the output of one command directly into another command as its input.

For example:

```bash
ls /home/analyst/reports | grep users
```

Here, `ls` lists the files and `grep` filters the results to show entries containing `users`.

Think of it as:

```text
Command 1 → Output → Command 2
```

---

## `find`

`find` searches through directories and their subdirectories based on different conditions.

### Search by filename

```bash
find /home/analyst -name "*log*"
```

Searches for files whose names contain `log`. The search is **case-sensitive**.

### Case-insensitive search

```bash
find /home/analyst -iname "*log*"
```

This also finds names such as `LOG`, `Log`, or `log`.

### Search by modification time

```bash
find /home/analyst -mtime -3
```

Finds files modified within the last 3 days.

Some useful variations:

- `-mtime -1` → Modified less than 1 day ago
- `-mtime +1` → Modified more than 1 day ago
- `-mmin` → Performs a similar search using **minutes** instead of days

---

# 4. File Permissions & Access Control

Linux uses file permissions to control **who can read, modify, or execute a file**.

This is an important part of the **Principle of Least Privilege**, which means users should receive only the permissions they actually need.

## Understanding the Permission String

A typical Linux permission string looks like this:

```text
d r w x r w x r w x
│ │ │ │ │ │ │ │ │ └── Execute permission for Others
│ │ │ │ │ │ │ │ └──── Write permission for Others
│ │ │ │ │ │ │ └────── Read permission for Others
│ │ │ │ │ │ └──────── Execute permission for Group
│ │ │ │ │ └────────── Write permission for Group
│ │ │ │ └──────────── Read permission for Group
│ │ │ └────────────── Execute permission for Owner
│ │ └──────────────── Write permission for Owner
│ └────────────────── Read permission for Owner
└──────────────────── File type
```

For example:

```text
drwxr-xr--
```

The first character represents the file type:

- `d` → Directory
- `-` → Regular file

The remaining characters are divided into three groups:

```text
rwx | r-x | r--
 ↓     ↓     ↓
User  Group Others
```

Where:

- `r` = Read
- `w` = Write
- `x` = Execute
- `-` = Permission not granted

---

## Modifying Permissions with `chmod`

The `chmod` command is used to change file and directory permissions.

### Permission Symbols

| Symbol | Meaning |
|---|---|
| `u` | User/Owner |
| `g` | Group |
| `o` | Others |
| `+` | Add permissions |
| `-` | Remove permissions |
| `=` | Set exact permissions |

### Example

```bash
chmod g-rw bonuses.txt
```

This removes **read and write permissions** from members of the file's group.

The general idea is:

```text
chmod [who][action][permission] file
```

For example:

```bash
chmod u+x script.sh
```

This gives the owner execute permission.

---

# 5. Administrative Privileges & User Management

## `sudo`

`sudo` stands for **"superuser do."**

It allows an authorized user to temporarily perform commands with elevated administrative privileges.

Instead of regularly logging in as the `root` user, administrators can use `sudo` only when they need higher privileges. This reduces the risk associated with continuously using a powerful root account.

Example:

```bash
sudo command
```

---

## User Administration Commands

### `useradd`

Creates a new user account.

```bash
sudo useradd -g security -G finance,admin fgarcia
```

In this example:

- `-g security` → Sets `security` as the user's primary group.
- `-G finance,admin` → Adds `finance` and `admin` as supplementary groups.
- `fgarcia` → Username being created.

---

### `usermod`

Modifies an existing user account.

```bash
sudo usermod -a -G marketing fgarcia
```

Here:

- `-a` → Appends the new group instead of replacing existing groups.
- `-G marketing` → Adds the user to the `marketing` group.

Other useful options include:

| Option | Purpose |
|---|---|
| `-d` | Changes the user's home directory |
| `-l` | Changes the login/username |
| `-L` | Locks the user account |
| `-a -G` | Adds the user to a supplementary group |

---

### `userdel`

Deletes a user account.

```bash
sudo userdel -r fgarcia
```

The `-r` option also removes the user's home directory and its contents.

> **Use this carefully**, because deleting the home directory can permanently remove the user's files.

---

## `chown`

`chown` changes the ownership of a file or directory.

### Change User Ownership

```bash
sudo chown fgarcia access.txt
```

This makes `fgarcia` the owner of `access.txt`.

### Change Group Ownership

```bash
sudo chown :security access.txt
```

The `:` indicates that the command is changing the **group ownership** rather than the user ownership.
