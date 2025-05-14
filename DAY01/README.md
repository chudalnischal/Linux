
# 📅 Day 1: Linux Basics

Today, we cover some of the most foundational Linux skills: basic commands, managing files and directories, and understanding the Linux directory structure.

---

## 🧠 Topics Covered

- Basic Linux Commands
- Moving Files and Directories
- Creating & Deleting Files/Directories
- Directory Hierarchy Overview

---

## 📂 1. Basic Commands

| Command | Description | Example |
|--------|-------------|---------|
| `pwd`  | Print current working directory | `pwd` |
| `ls`   | List directory contents | `ls -la` |
| `whoami` | Shows current logged-in user | `whoami` |
| `clear` | Clears the terminal screen | `clear` |
| `history` | Shows command history | `history` |

### 📝 Explanation

- `pwd`: Shows the full path of your current directory.
- `ls`: Lists all files and folders. Use `-l` for long format, `-a` to include hidden files.
- `whoami`: Useful to know which user you're operating as.
- `clear`: Just for a clean terminal view.
- `history`: Lets you see previous commands you've run.

---

## 📁 2. Moving Files / Directories

| Command | Description | Example |
|--------|-------------|---------|
| `mv`   | Move or rename files and directories | `mv file.txt /home/user/docs/` |
| `mv`   | Rename a file | `mv oldname.txt newname.txt` |

### 📝 Explanation

- `mv`: Used both to move files and rename them. The source comes first, then the destination.

---

## 🛠 3. Creating & Deleting Files / Directories

| Command | Description | Example |
|--------|-------------|---------|
| `touch` | Create a new empty file | `touch file.txt` |
| `mkdir` | Create a new directory | `mkdir new_folder` |
| `rm`    | Delete a file | `rm file.txt` |
| `rm -r` | Delete a directory and its contents | `rm -r old_folder` |

### ⚠️ Note:

- Be cautious with `rm -r` as it can delete entire directory trees permanently.

---

## 🗂 4. Directory Hierarchy Overview

The Linux directory structure is organized in a tree-like hierarchy:

```
/
├── bin      # Essential user binaries
├── boot     # Boot loader files
├── dev      # Device files
├── etc      # Configuration files
├── home     # User home directories
├── lib      # Shared libraries
├── media    # Removable media
├── opt      # Optional application software
├── root     # Root user home
├── sbin     # System binaries
├── tmp      # Temporary files
├── usr      # Secondary hierarchy
├── var      # Variable data like logs
```

### 🧠 Summary:
- `/` is the root of everything.
- Each folder serves a specific purpose and follows the Filesystem Hierarchy Standard (FHS).

---

## ✅ Practice Task

- Use `mkdir` to create a new directory.
- Inside it, use `touch` to create 2 files.
- Use `mv` to move one file to a different directory.
- Use `rm` to delete the other file.

---

Happy learning! 🚀
