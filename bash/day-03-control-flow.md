# Day 3 — Control Flow

## 🎯 Objective

Learn how to make Bash scripts **make decisions and repeat tasks** using conditional statements, loops, and `case` statements.

Today focused on:

- `if`, `elif`, and `else`
- Comparison operators
- File and string tests
- `for` loops
- `while` loops
- `case` statements
- Combining conditions with logical operators
- Practical Bash automation

---

# 1. Conditional Statements

Conditional statements allow a script to make decisions based on whether a condition is true or false.

Basic structure:

```bash
if [ condition ]; then
    # commands
else
    # commands
fi
```

Example:

```bash
#!/bin/bash

age=20

if [ "$age" -ge 18 ]; then
    echo "You are an adult."
else
    echo "You are a minor."
fi
```

The `fi` marks the end of the `if` statement.

---

# 2. `if`, `elif`, and `else`

Multiple conditions can be checked using `elif`.

```bash
#!/bin/bash

read -p "Enter your age: " age

if [ "$age" -lt 13 ]; then
    echo "Child"
elif [ "$age" -lt 18 ]; then
    echo "Teenager"
else
    echo "Adult"
fi
```

The conditions are evaluated from top to bottom.

---

# 3. Numeric Comparison Operators

Bash uses specific operators for comparing integers.

| Operator | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |
| `-lt` | Less than |
| `-le` | Less than or equal |

Example:

```bash
if [ "$number" -gt 10 ]; then
    echo "Greater than 10"
fi
```

---

# 4. String Comparisons

Strings can also be compared.

Common operators:

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | String is empty |
| `-n` | String is not empty |

Example:

```bash
#!/bin/bash

read -p "Enter username: " username

if [ "$username" = "admin" ]; then
    echo "Administrator account"
else
    echo "Standard user"
fi
```

---

# 5. File Tests

Bash can check whether files and directories exist and whether they have particular properties.

| Operator | Meaning |
|---|---|
| `-e` | Exists |
| `-f` | Regular file |
| `-d` | Directory |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

Example:

```bash
if [ -f "config.txt" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

Directory check:

```bash
if [ -d "logs" ]; then
    echo "Logs directory exists."
fi
```

These tests are particularly useful when writing administration and security scripts.

---

# 6. Combining Conditions

Conditions can be combined using logical operators.

### AND

```bash
if [ "$age" -ge 18 ] && [ "$age" -le 60 ]; then
    echo "Age is between 18 and 60."
fi
```

Both conditions must be true.

### OR

```bash
if [ "$choice" = "y" ] || [ "$choice" = "Y" ]; then
    echo "Confirmed."
fi
```

At least one condition must be true.

### NOT

```bash
if [ ! -f "file.txt" ]; then
    echo "File does not exist."
fi
```

The `!` negates the condition.

---

# 7. `for` Loops

A `for` loop repeats commands for each item in a list.

Basic syntax:

```bash
for item in list; do
    echo "$item"
done
```

Example:

```bash
for name in Alice Bob Charlie; do
    echo "Hello $name"
done
```

Output:

```text
Hello Alice
Hello Bob
Hello Charlie
```

---

# 8. Iterating Through Files

A `for` loop can process files in a directory.

```bash
for file in *.txt; do
    echo "$file"
done
```

This is useful for automation tasks involving multiple files.

For example:

```bash
for file in *.log; do
    echo "Checking $file"
done
```

This pattern will become useful for automated log analysis.

---

# 9. Numeric `for` Loops

Bash provides arithmetic loop syntax.

```bash
for ((i=1; i<=5; i++)); do
    echo "$i"
done
```

Output:

```text
1
2
3
4
5
```

The three parts are:

```text
initialization
condition
increment
```

---

# 10. `while` Loops

A `while` loop continues executing as long as its condition remains true.

Example:

```bash
count=1

while [ "$count" -le 5 ]; do
    echo "$count"
    ((count++))
done
```

Output:

```text
1
2
3
4
5
```

The variable must eventually change so that the condition becomes false.

Otherwise, the script can enter an **infinite loop**.

---

# 11. `case` Statements

`case` is useful when a script needs to choose between multiple options.

Basic structure:

```bash
case "$choice" in
    1)
        echo "Option 1"
        ;;
    2)
        echo "Option 2"
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

The `;;` ends each case.

The `*` acts as the default option.

---

# 12. Menu-Based Script

A practical example combines `case` with Linux commands.

```bash
#!/bin/bash

echo "===== SYSTEM MENU ====="
echo "1. Current User"
echo "2. Current Directory"
echo "3. System Information"
echo "4. Exit"

read -p "Choose an option: " choice

case "$choice" in
    1)
        whoami
        ;;
    2)
        pwd
        ;;
    3)
        uname -a
        ;;
    4)
        echo "Exiting..."
        exit 0
        ;;
    *)
        echo "Invalid option."
        ;;
esac
```

This demonstrates how Bash can turn individual Linux commands into a simple interactive utility.

---

# 13. `break`

`break` immediately exits a loop.

Example:

```bash
while true; do
    read -p "Enter q to quit: " input

    if [ "$input" = "q" ]; then
        break
    fi

    echo "You entered: $input"
done
```

The loop continues until the user enters `q`.

---

# 14. `continue`

`continue` skips the current iteration and moves to the next one.

Example:

```bash
for number in 1 2 3 4 5; do

    if [ "$number" -eq 3 ]; then
        continue
    fi

    echo "$number"
done
```

Output:

```text
1
2
4
5
```

The value `3` is skipped.

---

# 15. Practical Exercises

The following exercises were used to practice Day 3 concepts.

### Exercise 1 — Number Checker

Create a script that accepts a number and determines whether it is:

- Positive
- Negative
- Zero

Example:

```text
Enter a number: 15
Positive
```

---

### Exercise 2 — File Checker

Create a script that asks for a filename and determines whether:

- The file exists
- It is a regular file
- It is readable
- It is executable

Example:

```text
Enter filename: script.sh

File exists: Yes
Regular file: Yes
Readable: Yes
Executable: Yes
```

---

### Exercise 3 — Number Loop

Print numbers from `1` to `10` using a `for` loop.

```bash
for ((i=1; i<=10; i++)); do
    echo "$i"
done
```

---

### Exercise 4 — Log File Checker

Create a script that checks whether a log file exists.

If it exists:

```text
Log file found.
```

Otherwise:

```text
Log file not found.
```

This will form the foundation for more advanced log-analysis scripts later.

---

### Exercise 5 — Interactive Menu

Create a menu with options such as:

```text
===== MENU =====

1. Show current user
2. Show hostname
3. Show current directory
4. Show system information
5. Exit
```

Use a `case` statement to execute the appropriate command.

---

# 16. Practical Workflow

The basic decision-making workflow in Bash is:

```text
Input
  ↓
Condition
  ↓
 ┌───────────────┐
 │ True or False │
 └───────────────┘
      ↓     ↓
    True   False
      ↓     ↓
   Action  Action
```

For repetitive tasks:

```text
Start
  ↓
Check Condition
  ↓
Execute Task
  ↓
Update Value
  ↓
Check Again
  ↓
Condition False?
  ↓
Stop
```

---

# 🔐 Cybersecurity Relevance

Control flow is fundamental to security automation.

A security script frequently needs to ask questions such as:

```text
Does this file exist?
        ↓
      Yes/No

Is this permission configuration risky?
        ↓
      Yes/No

Is disk usage above the threshold?
        ↓
      Yes/No

Does this log contain a failed authentication?
        ↓
      Yes/No
```

Loops allow the script to perform these checks across many files, users, processes, or log entries.

For example:

```bash
for file in /var/log/*.log; do
    if [ -f "$file" ]; then
        echo "Checking $file"
    fi
done
```

This is the foundation for automated security monitoring and auditing.

---

# 🧠 Key Takeaways

- `if` statements allow Bash scripts to make decisions.
- `elif` allows additional conditions to be checked.
- `else` handles the alternative case.
- Numeric comparisons use operators such as `-eq`, `-gt`, and `-lt`.
- Bash can test files and directories using operators such as `-f` and `-d`.
- `for` loops are useful for processing lists and files.
- `while` loops repeat tasks while a condition remains true.
- `case` statements are useful for menus and multiple choices.
- `break` exits a loop.
- `continue` skips the current loop iteration.
- Combining conditions allows more complex automation logic.

---

# 🧪 Syntax Learned

```bash
if [ condition ]; then
    ...
elif [ condition ]; then
    ...
else
    ...
fi
```

```bash
for item in list; do
    ...
done
```

```bash
for ((i=0; i<10; i++)); do
    ...
done
```

```bash
while [ condition ]; do
    ...
done
```

```bash
case "$value" in
    option1)
        ...
        ;;
    option2)
        ...
        ;;
    *)
        ...
        ;;
esac
```

```bash
break
continue
```

---

## 📌 Day 3 Status

**Completed — Bash Control Flow**

Next:

**Day 4 — Files, Pipes & Text Processing**