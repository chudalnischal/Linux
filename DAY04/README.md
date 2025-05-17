# 📅 Day 4: Working with Files in Linux

## 🧠 What You’ll Learn Today:
Today you’ll explore essential file operations in Linux:

- File Permissions
- Archiving and Compressing
- Copying and Renaming
- Soft Links / Hard Links

---

## 🔐 File Permissions
Linux controls who can do what with a file or folder using permissions.
Each file has three types of access:

- **Owner (User)** – The person who created the file
- **Group** – A set of users
- **Others** – Everyone else

Each of these can have:

- r – Read
- w – Write (edit)
- x – Execute (run if it's a script)

### 🔹 View Permissions
```bash
ls -l filename

# Example output:

-rw-r--r-- 1 user user 0 May 16 10:00 example.txt
```
Meaning:

rwx = owner can read, write, and execute
r-x = group can read and execute
r-- = others can only read

### 🔹 Change Permissions (numeric mode)
chmod – Change Mode
You can use either numbers or symbols to set permissions.

Number reference:

- 7 = rwx
- 6 = rw-
- 5 = r-x
- 4 = r--

``` bash
chmod 755 filename
# 7 = read + write + execute (owner)
# 5 = read + execute (group, others)
```

### 🔹 Change Permissions (symbolic mode)
``` bash
chmod u+x script.sh    # Add execute to user
chmod g-w file.txt     # Remove write from group
```

### 🔹 Change Ownership
``` bash
sudo chown username:groupname filename
```
---

## 📦 Archiving and Compressing
Archiving: Combine multiple files/folders into one file (like .tar)
Compressing: Reduce the file size (like .gz, .zip)

Linux mostly uses .tar, .tar.gz, and .zip.

### 🔹 Create a tar archive
```bash
tar -cvf archive.tar foldername/
```

### 🔹 Extract a tar archive
```bash
tar -xvf archive.tar
```

### 🔹 Create a tar.gz (compressed) archive
``` bash
tar -czvf archive.tar.gz foldername/
```

### 🔹 Extract a tar.gz archive
```bash
tar -xzvf archive.tar.gz
```

## 📂 Copying and Renaming Files

### 🔹 Copy a file
```bash
cp source.txt destination.txt
```
### 🔹 Copy a folder (recursively)
``` bash
cp -r folder1/ folder2/
```

### 🔹 Rename a file (or move it)
```bash
mv oldname.txt newname.txt
```

### 🔹 Move a file to another directory
```bash
mv file.txt /path/to/destination/
```
---

## 🔗 Soft Links vs Hard Links

### 🔹 Create a Soft (Symbolic) Link
```bash
ln -s original.txt symlink.txt
```
Like a pointer or shortcut
If the original file is deleted, the link breaks

### 🔹 Create a Hard Link
```bash
ln original.txt hardlink.txt
```
Copies the inode

Even if the original is deleted, the file data remains

### 🔹 List with Inodes (to view links)
```bash
ls -li
```
---

## 🧪 Try It Yourself
- Use chmod, chown, and ls -l to explore file permissions
- Compress and extract folders using tar
- Create symbolic and hard links and experiment with deleting the originals



## Summary

| Topic     | What Can you Learned           |
|----------------|----------------------|
| Permissions | Who can read/write/execute a file  |
| chmod/chown      | How to change access and ownership  | 
| tar | Archive/compress folders and files |
| cp/mv  | Copy or rename/move files |
| ln    |  Create links (shortcuts or duplicates)



Well done! File management is a core skill in Linux. Keep practicing! 🐧🛠️