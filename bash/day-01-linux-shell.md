# Day 1 — Linux Shell Fundamentals

## 🎯 Objective

Understand the Linux command line, Bash shell, filesystem structure, and fundamental commands required to work effectively in a Linux environment.

---

## 1. What is a Shell?

A **shell** is a command-line interface that allows a user to interact with the operating system by entering commands.

Instead of using a graphical interface, commands can be used to:

- Navigate the filesystem
- Create and manage files
- Run programs
- Manage processes
- Inspect system information
- Automate tasks

Examples of commonly used shells include:

```text
Bash
Zsh
Fish
PowerShell
```

---

## 2. What is Bash?

**Bash (Bourne Again SHell)** is a Unix shell and command language.

Bash can be used both interactively from the terminal and as a scripting language for automating tasks.

Example:

```bash
echo "Hello, Bash!"
```

Bash is particularly useful in cybersecurity and DevSecOps because many Linux systems and security tools can be controlled and automated through the command line.

---

## 3. Terminal vs Shell

These terms are related but not the same.

### Terminal

The **terminal** is the interface/application through which commands are entered.

Examples:

```text
GNOME Terminal
Konsole
Windows Terminal
iTerm2
```

### Shell

The **shell** interprets the commands entered into the terminal.

For this learning journey, the shell being used is:

```text
Bash
```

The basic flow is:

```text
User
  ↓
Terminal
  ↓
Bash
  ↓
Linux Operating System
```

---

# 4. Linux Filesystem

Linux uses a hierarchical filesystem.

The top-level directory is:

```text
/
```

This is called the **root directory**.

Some important directories include:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── opt
├── root
├── tmp
├── usr
└── var
```

### Important directories

| Directory | Purpose |
|---|---|
| `/` | Root of the filesystem |
| `/home` | User home directories |
| `/root` | Home directory of the root user |
| `/etc` | System configuration files |
| `/tmp` | Temporary files |
| `/var` | Variable data such as logs |
| `/usr` | User applications and utilities |
| `/dev` | Device files |
| `/boot` | Boot-related files |

---

# 5. Paths

Linux uses paths to identify files and directories.

### Absolute Path

An absolute path starts from `/`.

Example:

```bash
/etc/passwd
```

It describes the complete location of the file.

### Relative Path

A relative path starts from the current directory.

Example:

```bash
documents/file.txt
```

---

## Special Path Symbols

### Current directory

```text
.
```

### Parent directory

```text
..
```

### Home directory

```text
~
```

### Root directory

```text
/
```

Example:

```bash
cd ..
```

moves one directory up.

```bash
cd ~
```

moves to the current user's home directory.

---

# 6. Basic Linux Commands

## `pwd`

Displays the current working directory.

```bash
pwd
```

Example:

```text
/home/user
```

---

## `ls`

Lists files and directories.

```bash
ls
```

Useful options:

```bash
ls -l
ls -a
ls -la
```

`-l` provides detailed information.

`-a` includes hidden files.

---

## `cd`

Changes the current directory.

```bash
cd /etc
```

Go to the parent directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

---

## `mkdir`

Creates a directory.

```bash
mkdir practice
```

Create nested directories:

```bash
mkdir -p practice/scripts/logs
```

---

## `touch`

Creates an empty file.

```bash
touch notes.txt
```

It can also update a file's timestamp if the file already exists.

---

## `cp`

Copies files or directories.

```bash
cp notes.txt backup.txt
```

Copy a directory recursively:

```bash
cp -r practice practice-backup
```

---

## `mv`

Moves or renames files.

Rename:

```bash
mv old.txt new.txt
```

Move:

```bash
mv new.txt practice/
```

---

## `rm`

Removes files.

```bash
rm file.txt
```

Remove a directory and its contents:

```bash
rm -r directory
```

### Important

`rm` normally does not move files to a recycle bin. Deleted files may be difficult or impossible to recover.

---

# 7. Viewing Files

## `cat`

Displays file contents.

```bash
cat notes.txt
```

---

## `less`

Allows a file to be viewed page by page.

```bash
less large-file.txt
```

Useful for reading large files without printing everything at once.

---

## `head`

Displays the beginning of a file.

```bash
head notes.txt
```

Display the first 20 lines:

```bash
head -n 20 notes.txt
```

---

## `tail`

Displays the end of a file.

```bash
tail notes.txt
```

Display the last 20 lines:

```bash
tail -n 20 notes.txt
```

`tail` is particularly useful when examining log files.

---

# 8. System Information Commands

## `whoami`

Displays the current username.

```bash
whoami
```

---

## `id`

Displays user and group information.

```bash
id
```

---

## `uname`

Displays system information.

```bash
uname
```

For detailed information:

```bash
uname -a
```

---

## `hostname`

Displays the system hostname.

```bash
hostname
```

---

## `date`

Displays the current date and time.

```bash
date
```

---

## `which`

Shows the location of an executable.

```bash
which bash
```

Example:

```text
/usr/bin/bash
```

---

## `type`

Shows how Bash interprets a command.

```bash
type cd
type ls
```

This is useful because some commands are external programs while others may be Bash builtins.

---

# 9. Getting Help

Linux provides built-in documentation for many commands.

## `man`

The `man` command opens a command's manual page.

```bash
man ls
```

Other examples:

```bash
man mkdir
man chmod
man grep
```

You can also use:

```bash
command --help
```

Example:

```bash
ls --help
```

---

# 10. Command History

Bash keeps a history of previously executed commands.

```bash
history
```

This is useful when:

- Reusing previous commands
- Reviewing what was executed
- Debugging
- Learning command syntax

---

# 11. Practical Work

During Day 1, I practiced navigating the Linux filesystem and managing files and directories from the command line.

### Practice structure

```text
bash-practice/
├── notes/
├── scripts/
├── logs/
└── backups/
```

Commands practiced:

```bash
mkdir
cd
pwd
ls
touch
cp
mv
rm
cat
head
tail
```

I also practiced identifying the current user and system information using:

```bash
whoami
id
hostname
uname
date
```

---

# 12. Key Takeaways

- Bash is both a shell and a scripting language.
- The terminal provides an interface for interacting with a shell.
- Linux uses a hierarchical filesystem beginning at `/`.
- Absolute paths start from `/`.
- Relative paths depend on the current working directory.
- `.` represents the current directory.
- `..` represents the parent directory.
- `~` represents the user's home directory.
- Linux provides powerful command-line utilities for system administration.
- Bash commands can later be combined to automate repetitive tasks.

---

# 🧪 Commands Learned

```text
pwd
ls
cd
mkdir
touch
cp
mv
rm
cat
less
head
tail
clear
history
man
echo
whoami
id
uname
hostname
date
which
type
```

---

# 🔐 Cybersecurity Relevance

Understanding the Linux command line is foundational for cybersecurity.

Security professionals frequently work with Linux systems to:

- Investigate files and directories
- Examine system configuration
- Analyze logs
- Inspect users and permissions
- Investigate running processes
- Troubleshoot systems
- Automate security checks
- Build security tooling

The commands learned today form the foundation for the Bash scripting and security automation covered in the following days.

---

## 📌 Day 1 Status

**Completed — Linux Shell Fundamentals**

Next:

**Day 2 — Bash Basics: Variables, Input, Output and Arithmetic**