# Day 5 — Functions, Arguments & Error Handling

## 🎯 Objective

Learn how to make Bash scripts more **modular, reusable, configurable, and reliable**.

Today focused on:

- Functions
- Function parameters
- Script arguments
- Special Bash variables
- Exit status
- `exit`
- Conditional command execution
- Error handling
- `set -e`
- `set -u`
- `set -o pipefail`
- `set -euo pipefail`
- Building reusable command-line scripts

These concepts are important for writing Bash scripts that can be used as practical Linux administration and cybersecurity tools.

---

# 1. Functions

A function is a reusable block of code.

Instead of writing the same commands multiple times, a function can be defined once and called whenever required.

Basic syntax:

```bash
function_name() {
    # commands
}
```

Example:

```bash
greet() {
    echo "Hello!"
}

greet
```

Output:

```text
Hello!
```

---

# 2. Functions with Parameters

Functions can accept arguments.

Example:

```bash
greet() {
    echo "Hello $1"
}

greet "Angad"
```

Output:

```text
Hello Angad
```

Inside the function:

```text
$1 → first function argument
```

Another example:

```bash
add() {
    echo $(( $1 + $2 ))
}

add 10 20
```

Output:

```text
30
```

Here:

```text
$1 → 10
$2 → 20
```

---

# 3. Function Return Values

Bash functions can return an exit status using `return`.

Example:

```bash
check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}
```

The function can then be tested:

```bash
if check_file "test.txt"; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

Bash uses:

```text
0     → success
non-zero → failure
```

This convention is fundamental to Linux and Bash scripting.

---

# 4. Script Arguments

Bash scripts can receive arguments directly from the command line.

Example script:

```bash
#!/bin/bash

echo "First argument: $1"
echo "Second argument: $2"
```

Run:

```bash
./script.sh hello world
```

Output:

```text
First argument: hello
Second argument: world
```

This allows scripts to accept input without requiring interactive prompts.

---

# 5. Important Special Variables

Bash provides several special variables.

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status of previous command |
| `$$` | Process ID of current shell |
| `$HOME` | User's home directory |
| `$USER` | Current username |

Example:

```bash
#!/bin/bash

echo "Script: $0"
echo "First argument: $1"
echo "Number of arguments: $#"
```

Run:

```bash
./script.sh test
```

---

# 6. `$@` — All Arguments

`$@` represents all positional arguments.

Example:

```bash
#!/bin/bash

for argument in "$@"; do
    echo "Argument: $argument"
done
```

Run:

```bash
./script.sh one two three
```

Output:

```text
Argument: one
Argument: two
Argument: three
```

This is useful when a script needs to process an unknown number of inputs.

---

# 7. Checking Arguments

A script should validate required arguments before using them.

Example:

```bash
#!/bin/bash

if [ "$#" -lt 1 ]; then
    echo "Usage: $0 <filename>"
    exit 1
fi

echo "File: $1"
```

Running:

```bash
./script.sh
```

produces:

```text
Usage: ./script.sh <filename>
```

Running:

```bash
./script.sh logfile.txt
```

produces:

```text
File: logfile.txt
```

Argument validation prevents scripts from behaving unexpectedly.

---

# 8. Exit Status

Every command executed in Bash produces an exit status.

The special variable:

```bash
$?
```

contains the exit status of the previous command.

Example:

```bash
ls /etc

echo $?
```

If the command succeeds:

```text
0
```

If it fails, a non-zero value is returned.

Example:

```bash
ls /does-not-exist

echo $?
```

The exact non-zero value can depend on the command.

---

# 9. Why Exit Codes Matter

Exit codes allow scripts to determine whether an operation succeeded.

Example:

```bash
mkdir test

if [ "$?" -eq 0 ]; then
    echo "Directory created successfully."
else
    echo "Failed to create directory."
fi
```

A more common pattern is to place the command directly inside the condition:

```bash
if mkdir test; then
    echo "Directory created successfully."
else
    echo "Failed to create directory."
fi
```

This is generally cleaner than checking `$?` afterward.

---

# 10. `exit`

The `exit` command terminates the script and can provide an exit status.

Successful completion:

```bash
exit 0
```

Failure:

```bash
exit 1
```

Example:

```bash
#!/bin/bash

if [ ! -f "$1" ]; then
    echo "File not found."
    exit 1
fi

echo "File found."
exit 0
```

This allows other programs or scripts to determine whether the script succeeded.

---

# 11. Error Handling

Good Bash scripts should anticipate failures.

Potential problems include:

- Missing arguments
- Missing files
- Invalid input
- Failed commands
- Permission problems
- Incorrect paths
- Unexpected command output

Instead of assuming everything succeeds, a script should check important operations.

Example:

```bash
if cp "$1" "$2"; then
    echo "Copy successful."
else
    echo "Copy failed."
    exit 1
fi
```

---

# 12. `set -e`

Bash normally continues executing after many command failures.

The following option changes that behavior:

```bash
set -e
```

It tells Bash to exit when a command returns a non-zero status in contexts where the failure is considered an unhandled error.

Example:

```bash
#!/bin/bash

set -e

mkdir test
cp missing.txt test/

echo "This may not execute if the copy fails."
```

`set -e` can help prevent a script from continuing after an unexpected failure.

However, its behavior has important exceptions, particularly around conditions and compound commands, so it should not be treated as a complete error-handling system.

---

# 13. `set -u`

The `-u` option treats unset variables as errors.

```bash
set -u
```

Example:

```bash
#!/bin/bash

set -u

echo "$username"
```

If `username` has not been defined, Bash reports an error rather than silently treating it as an empty value.

This can help catch variable-name mistakes.

---

# 14. `set -o pipefail`

Normally, the exit status of a pipeline is primarily determined by the last command.

Example:

```bash
command1 | command2
```

With:

```bash
set -o pipefail
```

the pipeline can fail if an earlier command fails.

Example:

```bash
set -o pipefail
```

This is particularly useful when scripts depend on pipelines for processing security or system data.

---

# 15. `set -euo pipefail`

These options are commonly combined:

```bash
set -euo pipefail
```

They provide three useful protections:

```text
-e → stop on unhandled command failures
-u → detect unset variables
-o pipefail → detect failures within pipelines
```

Example:

```bash
#!/bin/bash

set -euo pipefail

echo "Starting script..."
```

This is a common starting point for robust Bash scripts, although individual scripts may need additional explicit error handling.

---

# 16. Using Default Values

When using variables that may be unset, Bash provides parameter expansion.

Example:

```bash
name="${1:-Guest}"

echo "Hello $name"
```

If an argument is provided:

```bash
./script.sh Angad
```

Output:

```text
Hello Angad
```

Without an argument:

```bash
./script.sh
```

Output:

```text
Hello Guest
```

This is useful when writing flexible command-line tools.

---

# 17. Combining Functions and Arguments

Functions and script arguments can be combined to create reusable tools.

Example:

```bash
#!/bin/bash

show_file_info() {
    local file="$1"

    if [ -f "$file" ]; then
        echo "File: $file"
        echo "Size: $(wc -c < "$file") bytes"
    else
        echo "File not found: $file"
        return 1
    fi
}

if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <file>"
    exit 1
fi

show_file_info "$1"
```

This script:

1. Checks the number of arguments.
2. Receives a filename.
3. Passes the filename to a function.
4. Checks whether the file exists.
5. Displays information about the file.
6. Returns an appropriate status.

This is much closer to how practical Bash utilities are structured.

---

# 18. `local` Variables

Variables inside functions can be declared with `local`.

Example:

```bash
show_user() {
    local username="$1"
    echo "User: $username"
}
```

`local` limits the variable to the function's scope.

This helps prevent functions from unintentionally modifying variables elsewhere in the script.

---

# 19. Practical Exercises

## Exercise 1 — Greeting Function

Create a function that accepts a name and prints:

```text
Hello <name>
```

Example:

```bash
greet() {
    echo "Hello $1"
}
```

---

## Exercise 2 — File Checker

Create a function that accepts a filename and reports whether it exists.

```text
File exists.
```

or:

```text
File does not exist.
```

---

## Exercise 3 — Argument Counter

Create a script that displays:

```text
Script name:
Number of arguments:
Arguments:
```

Use:

```text
$0
$#
$@
```

---

## Exercise 4 — Safe Script

Create a script that:

1. Requires one filename argument.
2. Checks whether the file exists.
3. Prints an error if it doesn't.
4. Exits with a non-zero status on failure.
5. Prints information about the file if successful.

---

## Exercise 5 — Robust Pipeline

Create a script using:

```bash
set -euo pipefail
```

and use a pipeline to process a test log.

Verify what happens when one command in the pipeline fails.

---

# 20. Practical Workflow

The structure of a more reliable Bash script can now be:

```text
Start
  ↓
Validate Arguments
  ↓
Validate Input
  ↓
Perform Operation
  ↓
Check Result
  ↓
Handle Error
  ↓
Return Exit Status
```

Functions make this structure easier to organize:

```text
Main Script
    │
    ├── validate_input()
    │
    ├── check_file()
    │
    ├── process_data()
    │
    └── generate_output()
```

This makes scripts easier to read, test, maintain, and reuse.

---

# 🔐 Cybersecurity Relevance

These concepts are directly applicable to security automation.

A security script may need to:

- Accept a target file or directory as an argument.
- Validate that the input exists.
- Process multiple files.
- Return success or failure to another automation tool.
- Handle missing permissions.
- Detect failed commands.
- Use functions to separate different security checks.
- Process pipelines safely.

For example, a future security audit script could have functions such as:

```bash
check_users()
check_permissions()
check_processes()
check_network()
check_logs()
generate_report()
```

This modular structure will make the final **Linux Security Audit** project easier to develop and maintain.

---

# 🧠 Key Takeaways

- Functions allow code to be reused.
- Function arguments are accessed using positional parameters such as `$1` and `$2`.
- Scripts can receive arguments from the command line.
- `$0` represents the script name.
- `$#` represents the number of arguments.
- `$@` represents all arguments.
- `$?` contains the previous command's exit status.
- `exit` allows a script to terminate with a specific status.
- `0` conventionally represents success.
- Non-zero exit codes represent failure.
- Input should be validated before it is processed.
- `set -euo pipefail` provides useful safeguards for many scripts.
- `local` helps keep function variables scoped to the function.
- Functions make larger Bash projects easier to organize.

---

# 🧪 Commands & Syntax Learned

```bash
function_name() {
    ...
}
```

```bash
$0
$1
$2
$#
$@
$?
$$
```

```bash
return 0
return 1
```

```bash
exit 0
exit 1
```

```bash
set -e
set -u
set -o pipefail
set -euo pipefail
```

```bash
local variable="value"
```

```bash
"${1:-default}"
```

---

## 📌 Day 5 Status

**Completed — Functions, Arguments & Error Handling**

Next:

**Day 6 — Linux Automation: System Information, Disk Monitoring & Backups**