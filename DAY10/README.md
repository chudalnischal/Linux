# 📅 Day 10: Package Management in Linux

## 🧠 What You’ll Learn Today:
Package management is the heart of Linux system maintenance. It allows you to easily install, update, or remove software without downloading files manually or compiling from source.

Topics Covered:
- Installing / Removing / Upgrading Packages
- Finding and Searching Packages
- Listing Installed Packages
- Using Package Repositories and Snap

---

## 📦 What is a Package Manager?

A **package manager** is a tool that automates:
- Downloading software from trusted sources (repositories)
- Installing and configuring software
- Managing software dependencies

Different Linux distributions use different package managers:
- Debian/Ubuntu: `apt`
- Red Hat/CentOS: `yum` or `dnf`
- Arch: `pacman`
- Universal format: `snap`

---

## 📥 Installing, Removing & Upgrading Packages (APT – Debian/Ubuntu)

### 🔹 Install a package
```bash
sudo apt install package-name
```

Example:
```bash
sudo apt install htop
```

### 🔹 Remove a package
```bash
sudo apt remove package-name
```

### 🔹 Remove package + config files
```bash
sudo apt purge package-name
```

### 🔹 Upgrade a specific package
```bash
sudo apt install --only-upgrade package-name
```

### 🔹 Upgrade all packages
```bash
sudo apt update && sudo apt upgrade
```

> `apt update` updates the list of packages. `apt upgrade` installs available updates.

---

## 🔍 Finding and Searching for Packages

### 🔹 Search for a package
```bash
apt search package-name
```

### 🔹 Show detailed info about a package
```bash
apt show package-name
```

> Includes version, size, description, and dependencies

---

## 📋 Listing Installed Packages

### 🔹 List all installed packages
```bash
dpkg -l
```

### 🔹 Filter a specific installed package
```bash
dpkg -l | grep package-name
```

---

## 📚 Understanding Package Repositories

A **repository** is a collection of software packages stored on remote servers.

### 🔹 Check list of enabled repositories:
```bash
cat /etc/apt/sources.list
```

You can add PPAs (Personal Package Archives) for additional software:
```bash
sudo add-apt-repository ppa:some/ppa
sudo apt update
```

---

## 🚀 Snap Packages

### 🔹 What is Snap?
**Snap** is a universal package system developed by Canonical (Ubuntu), which works across distributions and includes all dependencies in one package.

### 🔹 Install Snap (if not available)
```bash
sudo apt install snapd
```

### 🔹 Install a Snap package
```bash
sudo snap install package-name
```

### 🔹 List installed Snap packages
```bash
snap list
```

### 🔹 Remove a Snap package
```bash
sudo snap remove package-name
```

> Snap packages are **sandboxed**, versioned, and automatically updated.

---

## 🧪 Try It Yourself

1. Install a useful package like `tree` or `htop`:
```bash
sudo apt install tree
tree /home/username
```

2. Remove it:
```bash
sudo apt remove tree
```

3. Install and use a Snap package:
```bash
sudo snap install hello-world
hello-world
```

---

## ✅ Why This Matters

| Task | Tool |
|------|------|
| Install or remove software | `apt`, `snap` |
| Keep your system updated | `apt update && upgrade` |
| Discover new tools | `apt search`, `snap find` |
| Clean up old packages | `apt autoremove`, `apt purge` |

> 📌 Package managers make Linux user-friendly, secure, and maintainable. Without them, managing software would be a nightmare.

---

You're now equipped to install and manage apps like a Linux power user! 🧠🐧📦
