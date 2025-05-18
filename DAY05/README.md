# 📅 Day 5: Text Processing in Linux

## 🧠 What You’ll Learn Today:
Today is all about how to read, filter, format, and process text using powerful Linux commands. These tools are often used for analyzing log files, scripting, or automating reports.

Covered Tools:
- stdout / stdin / stderr
- cut, paste
- head, tail
- expand, unexpand
- join, split
- sort, tr, uniq
- wc, nl
- grep, awk
- pipe (`|`)

---

## 📤 stdout, stdin, stderr

- **stdin** – Standard Input (keyboard/input file)
- **stdout** – Standard Output (usually the screen)
- **stderr** – Standard Error (error messages)

```bash
command > file.txt      # Redirect stdout to file
command 2> error.txt    # Redirect stderr
command < input.txt     # Redirect stdin from a file
```

---

## ✂️ `cut` – Extract columns

```bash
cut -d ':' -f1 /etc/passwd
```
- `-d` = delimiter
- `-f` = field number

---

## 📋 `paste` – Combine lines side by side

```bash
paste file1.txt file2.txt
```

---

## 🧢 `head` and `tail` – View start or end

```bash
head -n 5 file.txt     # First 5 lines
tail -n 10 file.txt    # Last 10 lines
```

---

## ⛓️ `expand` and `unexpand` – Tabs & spaces

```bash
expand file.txt       # Converts tabs to spaces
unexpand file.txt     # Converts spaces to tabs
```

---

## 🔗 `join` – Join lines from 2 files with matching fields

```bash
join file1.txt file2.txt
```

Files must be sorted on the join field.

---

## 🔪 `split` – Break file into parts

```bash
split -l 5 file.txt part_
```

Splits file into chunks with 5 lines each.

---

## 🔤 `sort` – Sort lines

```bash
sort names.txt
sort -r names.txt     # Reverse order
```

---

## 🔁 `tr` – Translate or delete characters

```bash
tr a-z A-Z < input.txt     # Convert to uppercase
tr -d '0-9' < input.txt    # Remove digits
```

---

## 🚫 `uniq` – Remove duplicate lines

```bash
uniq file.txt
sort file.txt | uniq       # Often used with sort
```

---

## 🔢 `nl` and `wc`

```bash
nl file.txt          # Numbered lines
wc -l file.txt       # Line count
wc -w file.txt       # Word count
wc -c file.txt       # Byte count
```

---

## 🔍 `grep` – Search text

```bash
grep "error" logfile.txt
grep -i "user" file.txt    # Case-insensitive
grep -r "main()" .         # Recursive search in dir
```

---

## 🧠 `awk` – Pattern scanning and processing

```bash
awk '{print $1}' file.txt            # Print first column
awk -F ':' '{print $1, $3}' /etc/passwd   # Use ":" delimiter
```

---

## 🧩 Pipe (`|`) – Combine commands

```bash
cat file.txt | grep "apple" | wc -l
```

Takes output of one command and sends it as input to the next.

---

## 🧪 Try It Yourself

- Count how many lines contain the word "linux":
```bash
grep -i "linux" file.txt | wc -l
```

- Extract usernames from /etc/passwd:
```bash
cut -d ':' -f1 /etc/passwd
```

- View top 5 longest words in a file:
```bash
tr ' ' '\n' < file.txt | sort | uniq | awk '{ print length, $0 }' | sort -nr | head -5
```

---

**Text processing is essential for scripting and automation. You’re leveling up! 🐧🧠**
