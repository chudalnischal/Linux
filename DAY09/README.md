# 📅 Day 9: Service Management in Linux

## 🧠 What You’ll Learn Today:
Today is all about managing services on a Linux system. Services are programs that run **in the background** (like web servers, database servers, SSH daemons, etc.) and are controlled by the system’s **init system**—most commonly `systemd`.

Topics Covered:
- Checking Service Status
- Starting / Stopping / Restarting Services
- Checking Service Logs
- Creating Your Own Services

---

## 🛠️ What is a Service?

A **service** is a long-running background process. Examples include:
- `ssh` (remote login)
- `nginx` or `apache2` (web servers)
- `mysql` (database server)

Services are managed by a system process manager. Most modern Linux systems use `systemd`, which uses the `systemctl` command.

---

## ✅ Checking Service Status

### 🔹 Check if a service is active
```bash
systemctl status ssh
```

Output will show:
- Whether the service is **active**, **inactive**, or **failed**
- Process ID
- Last few log entries

### 🔹 List all running services
```bash
systemctl list-units --type=service --state=running
```

### 🔹 List all services (active and inactive)
```bash
systemctl list-units --type=service
```

---

## ▶️ Starting, Stopping, and Restarting Services

### 🔹 Start a service
```bash
sudo systemctl start apache2
```

### 🔹 Stop a service
```bash
sudo systemctl stop apache2
```

### 🔹 Restart a service
```bash
sudo systemctl restart apache2
```

### 🔹 Reload a service (reload config without stopping)
```bash
sudo systemctl reload apache2
```

> Replace `apache2` with your actual service name (`ssh`, `docker`, `mysql`, etc.)

---

## 🔄 Enable or Disable Services on Boot

### 🔹 Enable service to start at boot
```bash
sudo systemctl enable apache2
```

### 🔹 Disable service from starting at boot
```bash
sudo systemctl disable apache2
```

### 🔹 Check if service is enabled
```bash
systemctl is-enabled apache2
```

---

## 📜 Checking Service Logs

Services managed by `systemd` log their output to `journald`. You can view logs using `journalctl`.

### 🔹 View logs for a service
```bash
journalctl -u ssh
```

### 🔹 Show logs with live update (like tail -f)
```bash
journalctl -u ssh -f
```

### 🔹 Show logs from today
```bash
journalctl -u ssh --since today
```

> Replace `ssh` with the name of the service you're inspecting

---

## 🛠️ Creating a Custom Service

Let’s say you want to run a custom script as a service.

### 🔹 1. Create your script
```bash
sudo nano /usr/local/bin/hello.sh
```

Paste this in:
```bash
#!/bin/bash
while true; do
  echo "Hello from my service!"
  sleep 10
done
```

Make it executable:
```bash
sudo chmod +x /usr/local/bin/hello.sh
```

### 🔹 2. Create a systemd service file
```bash
sudo nano /etc/systemd/system/hello.service
```

Paste this:
```
[Unit]
Description=My Hello Service

[Service]
ExecStart=/usr/local/bin/hello.sh
Restart=always

[Install]
WantedBy=multi-user.target
```

### 🔹 3. Start and Enable the Service
```bash
sudo systemctl daemon-reexec       # Refresh systemd
sudo systemctl daemon-reload       # Reload configs
sudo systemctl start hello.service
sudo systemctl enable hello.service
```

### 🔹 4. Check its logs
```bash
journalctl -u hello.service -f
```

---

## 🧪 Try It Yourself

- Start the SSH or Docker service:
```bash
sudo systemctl start ssh
sudo systemctl status ssh
```

- Check logs for your service:
```bash
journalctl -u ssh --since yesterday
```

- Create your own custom service to run a script

---

## ✅ Why This Matters

| Task | Tool |
|------|------|
| Check if service is running | `systemctl status` |
| Start/Stop services manually | `systemctl start/stop/restart` |
| Enable services at boot | `systemctl enable` |
| View logs of service behavior | `journalctl` |
| Run your own background jobs | Custom `systemd` services |

> 📌 Managing services is key for running applications and keeping systems healthy and automated.

---

Awesome job! You’re now equipped to control system services like a real Linux admin. 🧠🛠️🐧
