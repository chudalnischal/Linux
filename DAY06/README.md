# 📅 Day 6: Server Review – Monitoring System Health in Linux

## 🧠 What You’ll Learn Today:
Today is all about reviewing a Linux server’s health and performance. These tools and commands are crucial for **system administrators, DevOps engineers, and developers** to ensure that the system is running optimally.

Topics Covered:
- Uptime and Load
- Authentication Logs
- Services Running
- Available Memory & Disk

---

## 🕒 Uptime and Load Averages

### 🔹 What is "uptime"?
The **uptime** command shows how long the system has been running and the system load.

```bash
uptime
```

Example output:
```
10:30:45 up 5 days,  2:10,  2 users,  load average: 0.15, 0.25, 0.30
```

- `up 5 days, 2:10`: System has been running for 5 days and 2 hours
- `2 users`: 2 users are logged in
- `load average`: System load over the last 1, 5, and 15 minutes

> 📌 **Load average** measures the average number of processes waiting to run. On a 4-core CPU, a load of 4.0 means full usage.

### 🔹 Check CPU load using `top` or `htop`
```bash
top
```
- Real-time system monitoring: CPU, memory, processes

Install and run `htop` for a more interactive version:
```bash
sudo apt install htop
htop
```

---

## 🔐 Authentication Logs

### 🔹 What are Authentication Logs?
These logs record all login attempts, SSH access, and sudo usage. Very useful for **security auditing**.

### 🔹 View with `journalctl` (for systemd systems)
```bash
journalctl -u ssh
```

### 🔹 View login logs in `/var/log/auth.log` (Debian/Ubuntu)
```bash
sudo cat /var/log/auth.log | grep "sshd"
```

> 📌 Useful for detecting brute-force attacks or tracking which users accessed the server.

### 🔹 Who is currently logged in?
```bash
who
w
```

### 🔹 See recent logins:
```bash
last
```

---

## 🛠️ Services Running

### 🔹 What is a Service?
A **service** is a program (like SSH, Apache, MySQL) that runs in the background, typically managed by **systemd**.

### 🔹 View Active Services
```bash
systemctl list-units --type=service --state=running
```

### 🔹 Check a specific service status
```bash
systemctl status ssh
```

### 🔹 Start / Stop / Restart a Service
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
```

> Replace `nginx` with the name of any service (like `mysql`, `apache2`, `docker` etc).

---

## 🧠 Available Memory & Disk

### 🔹 Check Memory Usage
```bash
free -h
```
- `-h` shows human-readable format (MB/GB)
- Look at **used** vs **available** under `Mem`

### 🔹 Check Real-Time Memory Use
```bash
top
htop
```

### 🔹 See Memory Details Per Process
```bash
ps aux --sort=-%mem | head
```

### 🔹 Disk Space Overview
```bash
df -h
```

### 🔹 Disk Usage Per Directory (very useful!)
```bash
du -sh *
```

Or recursively:
```bash
du -ah /path | sort -rh | head -20
```

---

## 🧪 Try It Yourself

- Run `uptime` and `top`, observe system load
- Check who’s logged in using `who`
- Open `/var/log/auth.log` and look at SSH activity
- Use `df -h` and `free -h` to monitor memory and disk
- Use `systemctl` to view and manage services

---

## ✅ Why This Matters

These tools are crucial for:

| Use Case | Tool |
|----------|------|
| Checking if your server is slow | `uptime`, `top`, `htop` |
| Debugging login issues or attacks | `auth.log`, `journalctl` |
| Managing running apps | `systemctl` |
| Monitoring available resources | `df`, `free`, `ps aux` |

> 📌 **Knowing how to check your server’s health is a foundational Linux skill** whether you're a beginner, sysadmin, or cloud engineer.

---

