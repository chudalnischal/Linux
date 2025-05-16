# 📅 Day 3: Shell Basics, Command Path, Environment Variables & More

## 🧠 What You’ll Learn Today:
In Day 3, you’ll explore core Linux shell features and basic commands that are essential for scripting and system interaction. Covered topics:

- Command Path
- Shell Basics
- Environment Variables
- Command Help
- Redirection
- Super User (root)

---

## 🔧 Command Path & Shell Basics

### 🔹 `echo $SHELL`
Shows the current shell (e.g., `/bin/bash`, `/bin/zsh`).

### 🔹 `which <command>`
Finds the path of the executable for a command.
```bash
which ls
```

### 🔹 `echo $PATH`
Displays the PATH environment variable, which lists directories the shell checks for commands.

---

## 🌍 Environment Variables

### 🔹 `printenv` or `env`
Displays all environment variables.

### 🔹 `echo $VARIABLE_NAME`
Prints a specific environment variable.
```bash
echo $HOME
```

### 🔹 `export VAR=value`
Creates or modifies an environment variable.
```bash
export MYNAME=Nischal
echo $MYNAME
```

---

## 🆘 Command Help

| Command | Description |
|---------|-------------|
| `man <command>` | Shows the manual page for a command |
| `command --help` | Displays short help/usage info |
| `info <command>` | Displays detailed info for GNU commands |

```bash
man ls
ls --help
```

---

## 🔄 Redirects

### 🔹 Output Redirection (`>` and `>>`)
```bash
echo "Hello" > file.txt    # Overwrites file
echo "World" >> file.txt   # Appends to file
```

### 🔹 Input Redirection (`<`)
```bash
sort < unsorted.txt
```

### 🔹 Redirect both stdout and stderr
```bash
command > output.txt 2>&1
```

---

## 🔐 Super User (Root Access)

### 🔹 `sudo <command>`
Runs a command with superuser privileges.
```bash
sudo apt update
```

### 🔹 `su -`
Switches to the root user (if enabled).

> 🔒 Use superuser rights carefully! It can make system-wide changes.

---

## 🧪 Try It Yourself

- Check your shell with `echo $SHELL`
- Use `which bash`, `man echo`, `echo $PATH`
- Redirect command output using `>` and `>>`
- Try using `sudo` for a package command like `sudo apt install` (if on Debian-based system)

---

## 📚 Further Reading

- `man bash` – For bash shell documentation
- Explore `.bashrc` or `.zshrc` files to configure your environment

---

**Keep experimenting! You're building a solid foundation. 🧱🐧**
