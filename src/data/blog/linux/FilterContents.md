---
author: Sonam Tenzin  
pubDatetime: 2025-04-16T18:59:05+06:00  
modDatetime: 2025-04-16T18:59:05+06:00  
title: Filter Contents  
featured: false  
draft: false  
tags:  
  - Linux
  - Filtering
  - Commands
description: Overview of filtering contents in Linux using various commands. Discusses usage of cat, more, less, head, tail, sort, grep, cut, tr, column, awk, sed, and wc commands for effective content management.

---

### More

The `more` command is used to view large files one screen at a time. It is particularly useful when dealing with files like `/etc/passwd` that might not fit in a single screen.

```bash
$ cat /etc/passwd | more
```

The file is displayed screen by screen, and you can exit by pressing `[Q]`. The output remains visible in the terminal.

### Less

The `less` command is similar to `more`, but with more features. It allows for both forward and backward navigation.

```bash
$ less /etc/passwd
```

You can scroll through the file, and when you exit using `[Q]`, the output disappears from the terminal.

### Head

The `head` command allows you to view the first few lines of a file. By default, it shows the first 10 lines.

```bash
$ head /etc/passwd
```

This is useful when you are only interested in the top part of the file.

### Tail

The `tail` command displays the last few lines of a file, typically the last 10 lines.

```bash
$ tail /etc/passwd
```

It’s particularly useful when monitoring log files for the most recent entries.

### Sort

Sorting the output is often necessary, and `sort` helps organize data either alphabetically or numerically.

```bash
$ cat /etc/passwd | sort
```

This sorts the entries alphabetically.

### Grep

The `grep` command is used to search for specific patterns. It can be used with regular expressions to find lines that match certain conditions.

```bash
$ cat /etc/passwd | grep "/bin/bash"
```

This filters the content, displaying only users whose shell is `/bin/bash`.

### Cut

`cut` is used to cut out sections of lines based on a delimiter. For example, to display specific columns separated by colons (`:`):

```bash
$ cat /etc/passwd | cut -d ":" -f 1,7
```

This command outputs the usernames and their shells.

### Tr

The `tr` command is used to replace or remove specific characters in a stream of text.

```bash
$ cat /etc/passwd | tr ":" " "
```

This replaces all colons with spaces.

### Column

When results are cluttered, `column` helps format them into neat columns.

```bash
$ cat /etc/passwd | tr ":" " " | column -t
```

This command improves the readability of the output by aligning columns.

### Awk

`awk` is a powerful tool for pattern scanning and processing. It can be used to display specific columns.

```bash
$ cat /etc/passwd | awk -F: '{print $1, $NF}'
```

This displays the first and last fields of each line in the file.

### Sed

`sed` is a stream editor that allows you to replace text using regular expressions.

```bash
$ cat /etc/passwd | sed 's/bin/HTB/g'
```

This command replaces the string "bin" with "HTB" throughout the file.

### Wc

`wc` (word count) can be used to count the number of lines, words, or characters.

```bash
$ cat /etc/passwd | wc -l
```

This command counts the number of lines in the file.