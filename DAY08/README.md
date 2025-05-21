# 📅 Day 8: User Management in Linux

## 🧠 What You’ll Learn Today:
Today you’ll learn how Linux handles users and groups, how to create, delete, and modify them, and how to manage their permissions. This is a **core skill** for any system administrator, DevOps engineer, or advanced Linux user.

Topics Covered:
- Creating, Modifying, and Deleting Users
- Creating and Managing Groups
- File and Directory Permissions

---

## 👥 Why User Management is Important

Linux is a multi-user operating system. You can have many users working on the same system, and user management helps in:

- Controlling who can access what
- Securing the system from unauthorized actions
- Organizing users into roles or groups

---

## ➕ Creating Users

### 🔹 Add a new user
```bash
sudo adduser nischal
```

This command:
- Creates a new user named `nischal`
- Sets up the home directory `/home/nischal`
- Prompts for a password

### 🔹 Add user without home directory
```bash
sudo useradd -M tempuser
```

---

## ✏️ Modifying Users

### 🔹 Change username
```bash
sudo usermod -l newname oldname
```

### 🔹 Change home directory
```bash
sudo usermod -d /new/home/path username
```

### 🔹 Lock/Unlock a user account
```bash
sudo usermod -L username     # Lock
sudo usermod -U username     # Unlock
```

---

## ❌ Deleting Users

### 🔹 Remove a user (keep home directory)
```bash
sudo deluser username
```

### 🔹 Remove a user and their home directory
```bash
sudo deluser --remove-home username
```

---

## 👪 Groups in Linux

### 🔹 What is a Group?
A group is a collection of users with shared access permissions.

### 🔹 Create a new group
```bash
sudo addgroup developers
```

### 🔹 Add user to a group
```bash
sudo usermod -aG developers nischal
```

### 🔹 See groups of a user
```bash
groups nischal
```

### 🔹 Delete a group
```bash
sudo delgroup developers
```

---

## 🔒 File and Directory Permissions

Linux uses permission bits to control who can read, write, and execute a file.

### 🔹 Check permissions
```bash
ls -l file.txt
```

### 🔹 Change ownership
```bash
sudo chown username:groupname file.txt
```

### 🔹 Change permissions using numbers (chmod)
```bash
chmod 755 file.sh
```

| Number | Permissions      |
|--------|------------------|
| 7      | Read + Write + Execute |
| 6      | Read + Write     |
| 5      | Read + Execute   |
| 4      | Read only        |

### 🔹 Symbolic Mode
```bash
chmod u+x script.sh    # Add execute for user
chmod g-w file.txt     # Remove write for group
```

---

## 📁 Example: Secure a Folder

### Create a folder and allow only the user to access:
```bash
mkdir secret
chmod 700 secret
```

Only the owner can read/write/execute.

---

## 🧪 Try It Yourself

1. Create a new user:
```bash
sudo adduser testuser
```

2. Add the user to a group:
```bash
sudo addgroup testers
sudo usermod -aG testers testuser
```

3. Create a file and modify permissions:
```bash
touch file.txt
chmod 640 file.txt
ls -l file.txt
```

4. Remove the user:
```bash
sudo deluser testuser
```

---

## ✅ Why This Matters

| Task | Tool |
|------|------|
| Add users and groups | `adduser`, `addgroup` |
| Secure files | `chmod`, `chown` |
| Audit user access | `groups`, `id` |
| Delete or modify users | `usermod`, `deluser` |

> 📌 User and permission management is critical for system security and multi-user environments.

---

You're now in control of who can do what on your system! 🐧🔐
