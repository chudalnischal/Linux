# 📅 Day 7: Process Management in Linux

## 🧠 What You’ll Learn Today:
Today you'll understand how to manage **processes** in Linux. Processes are running instances of programs, and managing them is a core skill for system administrators, developers, and DevOps engineers.

Covered Topics:
- Background / Foreground Processes
- Listing / Finding Processes
- Process Signals & Killing Processes
- Process Priorities
- Process Forking

---

## 🔁 What is a Process?
A **process** is any program or command that's currently running. Every process has a unique **PID (Process ID)**.

You can see active processes using:
```bash
ps
top
htop
```

---

## 🚀 Background vs Foreground Processes

### 🔹 Foreground Process
A process that runs in your current terminal and **takes control** of it.
```bash
ping google.com
```

To stop it temporarily: `Ctrl + Z`  
To end it: `Ctrl + C`

### 🔹 Background Process
Run the command in the background so your terminal is still usable.

```bash
ping google.com &
```

Use `jobs` to list background processes.

### 🔹 Move between Foreground & Background

- Move background process to foreground:
```bash
fg %1
```

- Stop foreground process and send to background:
```bash
Ctrl + Z
bg %1
```

> `%1` refers to job number 1 (you can get job numbers via `jobs`)

---

## 🔍 Listing and Finding Processes

### 🔹 `ps` – Process Status
```bash
ps aux
```

- `a` – All users
- `u` – User info
- `x` – Processes not attached to terminal

### 🔹 `top` – Real-time overview
```bash
top
```

Use `q` to quit

### 🔹 `htop` – Enhanced version of `top`
```bash
sudo apt install htop
htop
```

### 🔹 `pgrep` – Find process by name
```bash
pgrep firefox
```

### 🔹 `pidof` – Get PID of a specific program
```bash
pidof bash
```

---

## ☠️ Killing and Signaling Processes

### 🔹 `kill` – Send signals to processes
```bash
kill PID
```

Default is `SIGTERM` (signal 15) – politely asks the process to stop.

### 🔹 `kill -9` – Force Kill
```bash
kill -9 PID
```

### 🔹 `killall` – Kill by name
```bash
killall firefox
```

---

## 📶 Process Signals

| Signal | Name     | Description               |
|--------|----------|---------------------------|
| 1      | SIGHUP   | Reload config             |
| 9      | SIGKILL  | Force kill (cannot be ignored) |
| 15     | SIGTERM  | Graceful termination      |
| 18     | SIGCONT  | Continue if stopped       |
| 19     | SIGSTOP  | Pause execution           |

Send signals manually:
```bash
kill -SIGSTOP PID
kill -SIGCONT PID
```

---

## 🧮 Process Priorities (nice/renice)

### 🔹 Start with a nice value
```bash
nice -n 10 command
```

### 🔹 Change priority of a running process
```bash
renice -n 5 -p <PID>
```

### 🔹 Check nice values
```bash
ps -eo pid,ni,comm
```

---

## 🌱 Process Forking

### 🔹 What is Forking?
When a process **creates a copy of itself**, it's called forking. This is how most processes are started.

Example:
```bash
bash -c "sleep 10 & echo 'Forked process started'"
```

---

## 🧪 Try It Yourself

- Run a process in the background:
```bash
sleep 1000 &
```

- Find its PID:
```bash
ps aux | grep sleep
```

- Kill it:
```bash
kill <PID>
```

- Use `top`, `htop`, `nice`, and `renice` to observe process behavior

---

## ✅ Why This Matters

| Task | Tool |
|------|------|
| Monitor running processes | `ps`, `top`, `htop` |
| Start/stop background jobs | `jobs`, `bg`, `fg`, `&` |
| Kill misbehaving apps | `kill`, `killall` |
| Prioritize resource usage | `nice`, `renice` |

> 📌 **Mastering process management gives you full control over your system performance and stability.**

---

Keep pushing forward — you're managing your system like a pro now! 🐧⚙️
