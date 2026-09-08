# Day 4 — Files, Pipes & Text Processing

## 🎯 Objective

Learn how Bash works with files, command output, pipelines, and text-processing utilities.

Today focused on:

- Input and output redirection
- Pipes
- File searching
- `grep`
- `cut`
- `sort`
- `uniq`
- `wc`
- `head` and `tail`
- `sed`
- `awk`
- Combining commands for automation
- Basic log analysis

These concepts are particularly important for **Linux administration, cybersecurity, and DevSecOps**, where large amounts of system and log data often need to be searched and processed from the command line.

---

# 1. Output Redirection

Normally, a command prints its output to the terminal.

For example:

```bash
ls
```

Output can be redirected into a file using:

```bash
>
```

Example:

```bash
ls > files.txt
```

Instead of displaying the output on the screen, Bash writes it to `files.txt`.

If the file already exists, its contents are **overwritten**.

---

# 2. Append Output

The `>>` operator appends output to an existing file.

```bash
date >> system.log
```

Every time this command runs, the date is added to the end of the file.

Difference:

```text
>   → overwrite
>>  → append
```

This is useful for creating logs.

Example:

```bash
echo "Script started" >> script.log
```

---

# 3. Input Redirection

The `<` operator redirects a file into a command's standard input.

Example:

```bash
wc -l < file.txt
```

Instead of receiving input from the terminal, `wc` receives the contents of `file.txt`.

---

# 4. Standard Output and Error

Linux commands generally use three standard streams:

| Stream | Number | Purpose |
|---|---:|---|
| Standard input | `0` | Input |
| Standard output | `1` | Normal output |
| Standard error | `2` | Error messages |

Standard output can be redirected:

```bash
command > output.txt
```

Errors can be redirected:

```bash
command 2> error.txt
```

Both can be redirected separately:

```bash
command > output.txt 2> error.txt
```

---

# 5. Pipes

A pipe allows the output of one command to become the input of another command.

The pipe operator is:

```bash
|
```

Example:

```bash
ls | less
```

The output from `ls` is passed to `less`.

Another example:

```bash
ps aux | grep ssh
```

This searches the output of `ps aux` for processes containing `ssh`.

The basic concept is:

```text
Command 1
   ↓
Output
   ↓
   |
   ↓
Command 2
   ↓
Output
```

Multiple commands can be chained:

```bash
command1 | command2 | command3
```

This is one of the most powerful features of the Linux command line.

---

# 6. `grep`

`grep` searches text for matching patterns.

Basic usage:

```bash
grep "error" logfile.txt
```

This displays lines containing `error`.

---

## Case-Insensitive Search

```bash
grep -i "error" logfile.txt
```

This matches:

```text
error
ERROR
Error
eRrOr
```

---

## Count Matches

```bash
grep -c "error" logfile.txt
```

This returns the number of matching lines.

---

## Show Line Numbers

```bash
grep -n "error" logfile.txt
```

Example:

```text
15:ERROR Authentication failed
27:ERROR Permission denied
```

---

## Invert the Search

The `-v` option shows lines that **do not** match.

```bash
grep -v "INFO" logfile.txt
```

This can be useful for filtering out unimportant log messages.

---

# 7. `wc`

`wc` counts information in text.

Examples:

```bash
wc file.txt
```

Count lines:

```bash
wc -l file.txt
```

Count words:

```bash
wc -w file.txt
```

Count characters:

```bash
wc -c file.txt
```

Combined with other commands:

```bash
grep "ERROR" logfile.txt | wc -l
```

This counts the number of lines containing `ERROR`.

---

# 8. `sort`

`sort` sorts lines of text.

Example:

```bash
sort users.txt
```

Reverse order:

```bash
sort -r users.txt
```

Numeric sorting:

```bash
sort -n numbers.txt
```

`sort` becomes especially useful when combined with `uniq`.

---

# 9. `uniq`

`uniq` removes consecutive duplicate lines.

Example:

```bash
sort users.txt | uniq
```

Count occurrences:

```bash
sort users.txt | uniq -c
```

Example:

```text
3 admin
5 user
2 guest
```

The combination:

```bash
sort | uniq -c
```

is a common pattern for analyzing repeated values.

---

# 10. `cut`

`cut` extracts specific sections from lines.

A common example is `/etc/passwd`.

```bash
cut -d: -f1 /etc/passwd
```

Here:

```text
-d:  → use : as the delimiter
-f1  → select field 1
```

Since `/etc/passwd` uses colon-separated fields, this extracts usernames.

Example:

```text
root
daemon
bin
sys
user
```

---

# 11. `head`

`head` displays the beginning of a file.

```bash
head logfile.txt
```

Display the first 5 lines:

```bash
head -n 5 logfile.txt
```

Useful when quickly inspecting a large file.

---

# 12. `tail`

`tail` displays the end of a file.

```bash
tail logfile.txt
```

Display the last 10 lines:

```bash
tail -n 10 logfile.txt
```

`tail` is particularly useful for examining logs.

---

## Following a Log

The `-f` option follows a file as it changes:

```bash
tail -f application.log
```

New lines added to the log appear in real time.

This is commonly used during system troubleshooting and monitoring.

---

# 13. `find`

`find` searches for files and directories.

Example:

```bash
find . -name "*.log"
```

This searches the current directory and its subdirectories for `.log` files.

Find directories:

```bash
find . -type d
```

Find regular files:

```bash
find . -type f
```

Find files with a specific name:

```bash
find . -type f -name "config.txt"
```

---

# 14. Combining `find` and `grep`

Commands can be combined to perform more useful searches.

Example:

```bash
find . -type f -name "*.log" -exec grep -i "error" {} \;
```

This searches log files for the word `error`.

The important concept is that Bash allows small utilities to be combined into larger workflows.

---

# 15. `sed`

`sed` is a stream editor used to process and transform text.

A common operation is substitution.

Example:

```bash
sed 's/error/ERROR/' logfile.txt
```

This replaces the first occurrence of `error` on each line with `ERROR`.

Replace all occurrences on each line:

```bash
sed 's/error/ERROR/g' logfile.txt
```

The `g` means global replacement within each line.

---

# 16. `awk`

`awk` is a powerful text-processing language commonly used for working with structured data.

Basic example:

```bash
awk '{print $1}' file.txt
```

This prints the first whitespace-separated field from every line.

Second field:

```bash
awk '{print $2}' file.txt
```

Multiple fields:

```bash
awk '{print $1, $3}' file.txt
```

---

## Using a Delimiter

For colon-separated data:

```bash
awk -F: '{print $1}' /etc/passwd
```

`-F:` specifies `:` as the field separator.

This is another way to extract usernames.

---

# 17. Log Analysis

Text processing becomes particularly useful when working with logs.

Consider:

```text
INFO User login
INFO Backup started
ERROR Authentication failed
INFO User logout
ERROR Permission denied
WARNING Disk usage high
ERROR Authentication failed
```

Count errors:

```bash
grep -i "error" logfile.txt | wc -l
```

Find authentication failures:

```bash
grep -i "authentication failed" logfile.txt
```

Count repeated events:

```bash
grep -i "error" logfile.txt | sort | uniq -c
```

This transforms raw log data into useful information.

---

# 18. Practical Security Example

A basic log-analysis workflow could be:

```bash
grep -i "failed" logfile.txt
```

Then count the results:

```bash
grep -i "failed" logfile.txt | wc -l
```

Or search for multiple security-related keywords:

```bash
grep -Ei "failed|denied|error" logfile.txt
```

This can help identify potentially interesting events during system investigation.

For real security investigations, the exact log format and operating system must be considered before interpreting results.

---

# 19. Command Chaining

Commands can be chained to create increasingly useful operations.

Example:

```bash
cat logfile.txt | grep "ERROR"
```

A better approach in many cases is to let `grep` read the file directly:

```bash
grep "ERROR" logfile.txt
```

For counting:

```bash
grep "ERROR" logfile.txt | wc -l
```

For frequency analysis:

```bash
grep "ERROR" logfile.txt | sort | uniq -c
```

The general pattern is:

```text
Input
  ↓
Filter
  ↓
Transform
  ↓
Count / Sort
  ↓
Useful Information
```

---

# 20. Practical Exercises

## Exercise 1 — File Search

Find all `.log` files in the current directory.

```bash
find . -type f -name "*.log"
```

---

## Exercise 2 — Error Search

Search a log file for errors.

```bash
grep -i "error" logfile.txt
```

---

## Exercise 3 — Error Count

Count the number of error lines.

```bash
grep -i "error" logfile.txt | wc -l
```

---

## Exercise 4 — Extract Usernames

Extract usernames from `/etc/passwd`.

```bash
cut -d: -f1 /etc/passwd
```

---

## Exercise 5 — Analyze Repeated Events

Count repeated log messages.

```bash
sort logfile.txt | uniq -c
```

---

## Exercise 6 — Build a Basic Log Analyzer

Create a script that reports:

```text
===== LOG ANALYSIS =====

Total Lines:
Errors:
Warnings:
Failed Events:
```

The script should use tools such as:

```text
grep
wc
```

This is an important step toward the security auditing project that will be developed later.

---

# 21. Practical Workflow

The main workflow learned today was:

```text
Raw Data
   ↓
Search / Filter
   ↓
Extract
   ↓
Sort
   ↓
Remove / Count Duplicates
   ↓
Count / Analyze
   ↓
Useful Information
```

For example:

```bash
grep -i "error" logfile.txt | sort | uniq -c
```

This combines multiple small operations into one useful analysis pipeline.

---

# 🔐 Cybersecurity Relevance

Text processing is one of the most important Bash skills for cybersecurity.

Security analysts and system administrators frequently work with:

- Authentication logs
- Web server logs
- Application logs
- System logs
- Configuration files
- Process output
- Network information

Instead of manually reading thousands of lines, command-line tools can filter and analyze the data.

For example:

```bash
grep -Ei "failed|denied|error" logfile.txt
```

can quickly identify lines containing common security-relevant terms.

Bash therefore acts as a bridge between **Linux administration and security automation**.

---

# 🧠 Key Takeaways

- `>` redirects output and overwrites a file.
- `>>` appends output to a file.
- `<` redirects input from a file.
- `|` connects the output of one command to another.
- `grep` searches text.
- `wc` counts lines, words, and characters.
- `sort` sorts text.
- `uniq` removes/counts repeated lines.
- `cut` extracts fields.
- `head` examines the beginning of files.
- `tail` examines the end of files.
- `find` searches for files and directories.
- `sed` performs stream-based text transformations.
- `awk` processes structured text and fields.
- Combining commands creates powerful Linux automation pipelines.

---

# 🧪 Commands & Syntax Learned

```text
>
>>
<
|
grep
grep -i
grep -n
grep -v
grep -E
wc
wc -l
sort
sort -r
sort -n
uniq
uniq -c
cut
head
tail
tail -f
find
sed
awk
```

---

## 📌 Day 4 Status

**Completed — Files, Pipes & Text Processing**

Next:

**Day 5 — Functions, Arguments & Error Handling**