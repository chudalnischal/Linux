# 📅 Day 2: Editing Files Using Vim Editor

## 🧠 What You’ll Learn:
Today, we explore **Vim**, a powerful and widely-used text editor in Linux. Vim helps you create and modify text files right from the terminal.

---

## 🔑 Basic Vim Commands and Modes

Vim has two main modes:
- **Normal Mode**: For navigation and commands
- **Insert Mode**: For typing/editing text

| Action                         | Command/Key           | Description                          |
|-------------------------------|----------------------|------------------------------------|
| Open a file in Vim             | `vim filename`       | Opens or creates a file to edit    |
| Switch to Insert Mode          | `i`                  | Start inserting text                |
| Save changes                  | `:w`                 | Write (save) file                   |
| Save and quit                 | `:wq` or `ZZ`        | Save file and exit Vim              |
| Quit without saving           | `:q!`                | Exit Vim without saving             |
| Move cursor                   | Arrow keys / `h j k l`| Navigate left, down, up, right    |
| Delete a character            | `x`                  | Delete character under cursor       |
| Undo last change             | `u`                  | Undo previous action                |
| Search text                  | `/text`              | Search for “text” forward           |
| Replace a word               | `:%s/old/new/g`      | Replace all 'old' with 'new' in file|

---

## 🔍 How to Edit a File in Vim - Step by Step:

1. Open the terminal and type:
```bash
   vim myfile.txt
```
You start in Normal Mode. Press i to switch to Insert Mode to start typing.
After editing, press Esc to return to Normal Mode.

2. To save your changes, type:
```bash
:w   # and press Enter.
```

3. To save and quit, type:
```bash
:wq
```

4. To quit without saving changes:
```bash
:q!
```

### 💡 Tips for Beginners:
- Press Esc often to make sure you are in Normal Mode before running commands.
- Use arrow keys or h (left), j (down), k (up), l (right) to move the cursor.
- Practice opening, editing, saving, and quitting to get comfortable.
- Vim can be very powerful but takes time to master — start simple!

### 📚 Further Reading and Help
- Use :help inside Vim to open the help docs.
- Check out online Vim tutorials and cheatsheets for more commands.

