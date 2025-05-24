# 📅 Day 11: Disks and Filesystems in Linux

## 🧠 What You’ll Learn Today:
Managing disks and filesystems is a key part of system administration. Today, you'll learn how Linux handles data storage and how to manage disk space, filesystems, and swap space.

Topics Covered:
- Inodes
- Filesystems
- Mounts
- Adding Disks
- Swap
- LVM (Logical Volume Management)

---

## 📂 Inodes

### 🔹 What is an Inode?
An **inode** is a data structure used by Linux to store metadata about a file:
- File size, ownership, permissions, timestamps, etc.
- It **does not** store the file name

### 🔹 View inode info
```bash
ls -i filename
```

### 🔹 View file system usage with inode count
```bash
df -i
```

---

## 🗃️ Filesystems

### 🔹 What is a Filesystem?
A **filesystem** is how data is organized and stored on a disk. Common types include:
- `ext4` (default in most distros)
- `xfs`, `btrfs`, `ntfs`

### 🔹 View current filesystems
```bash
df -T
```

### 🔹 Check a filesystem’s type
```bash
stat -f .
```

---

## 🔗 Mounts

### 🔹 What is Mounting?
Mounting makes a filesystem accessible to the OS. Without mounting, the data on a partition or external drive is not usable.

### 🔹 View mounted filesystems
```bash
mount | column -t
```

or:
```bash
findmnt
```

### 🔹 Mount a device manually
```bash
sudo mount /dev/sdb1 /mnt
```

### 🔹 Unmount a device
```bash
sudo umount /mnt
```

> Devices are typically mounted automatically in `/etc/fstab`

---

## ➕ Adding Disks

### 🔹 View available disks
```bash
lsblk
```

### 🔹 Partition a new disk
```bash
sudo fdisk /dev/sdb
```

Follow the interactive prompts to create a partition.

### 🔹 Format a partition with ext4
```bash
sudo mkfs.ext4 /dev/sdb1
```

### 🔹 Mount it to a folder
```bash
sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data
```

> Use `df -h` or `lsblk` to confirm the mount

---

## 🔃 Swap Space

### 🔹 What is Swap?
Swap is disk space used when RAM is full. It's slower than RAM but prevents crashes.

### 🔹 Check if swap is enabled
```bash
swapon --show
```

### 🔹 Create swap file (1 GB)
```bash
sudo fallocate -l 1G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

### 🔹 Make it permanent (add to fstab)
```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

---

## 🧱 LVM – Logical Volume Management

### 🔹 What is LVM?
LVM lets you **resize**, **combine**, and **snapshot** disk partitions easily. It abstracts physical disks into flexible volumes.

### 🔹 Key Components:
- **PV (Physical Volume)** – Actual disk or partition
- **VG (Volume Group)** – Collection of PVs
- **LV (Logical Volume)** – Mountable partition created from a VG

### 🔹 Example: Basic LVM setup

1. Create physical volume:
```bash
sudo pvcreate /dev/sdb1
```

2. Create volume group:
```bash
sudo vgcreate myvg /dev/sdb1
```

3. Create logical volume:
```bash
sudo lvcreate -L 5G -n mylv myvg
```

4. Format and mount it:
```bash
sudo mkfs.ext4 /dev/myvg/mylv
sudo mount /dev/myvg/mylv /mnt
```

> Use `lsblk`, `vgs`, `lvs` to inspect your LVM layout

---

## 🧪 Try It Yourself

- View your disk layout:
```bash
lsblk
df -h
```

- Inspect inode usage:
```bash
df -i
```

- Create a swap file or format a USB drive with `mkfs`

---

## ✅ Why This Matters

| Task | Tool |
|------|------|
| View disk usage | `df`, `lsblk` |
| Format and mount drives | `mkfs`, `mount`, `umount` |
| Track filesystem structure | `inodes`, `findmnt` |
| Manage dynamic storage | `LVM` |
| Improve memory handling | `swap`, `swapon` |

> 📌 Disk and filesystem management is essential for any Linux system to perform reliably and scale over time.

---

You're now navigating the backbone of Linux storage like a pro! 🧠💽🐧
