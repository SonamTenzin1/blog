---
author: Sonam Tenzin
pubDatetime: 2025-04-16T21:35:00+06:00
modDatetime: 2025-04-16T21:35:00+06:00
title: Shell
featured: false
draft: false
tags:
  - regex
  - grep
  - shell
  - linux
description: Introduction to Regular Expressions and basic grep usage for pattern matching and text filtering.
---

## Regular Expressions (RegEx)

Regular expressions (RegEx) are like the art of crafting precise blueprints for searching patterns in text or files. They allow you to find, replace, and manipulate data with precision. Think of RegEx as a highly customizable filter for sifting through strings of text—whether for analyzing data, validating input, or performing advanced search operations.

At its core, a regular expression is a sequence of characters and symbols that form a search pattern. These often involve **metacharacters**, which define the structure of the search rather than representing literal text. For example, metacharacters can specify whether you're searching for digits, letters, or patterns.

RegEx is supported in many tools and languages (e.g., `grep`, `sed`), making it a powerful tool in a Linux user's toolkit.

---

## Grouping

Regex supports pattern grouping using different types of brackets:

| Operator | Description |
|----------|-------------|
| `(a)`    | Round brackets group parts of a regex so they are processed together. |
| `[a-z]`  | Square brackets define character classes—sets of characters to match. |
| `{1,10}` | Curly brackets define **quantifiers**—how many times a pattern should repeat. |
| `|`      | OR operator; matches either expression. |
| `.*`     | Functions like an AND operator; matches when both patterns appear in order. |

---

## Examples

### OR Operator

```bash
grep -E "(my|false)" /etc/passwd
```

This command matches lines containing either "my" or "false".

**Output Example:**
```
lxd:x:105:65534::/var/lib/lxd/:/bin/false
pollinate:x:109:1::/var/cache/pollinate:/bin/false
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

### AND Operator

```bash
grep -E "my.*false" /etc/passwd
```

This matches lines containing **both** "my" and "false" in the specified order.

**Alternative using pipe:**

```bash
grep -E "my" /etc/passwd | grep -E "false"
```

---

## Practice Tasks (Using `/etc/ssh/sshd_config`)

1. **Show all lines that do not contain the `#` character.**

   ```bash
   grep -v "#" /etc/ssh/sshd_config
   ```

2. **Search for all lines containing a word that starts with `Permit`.**

   ```bash
   grep -E "\bPermit\w*" /etc/ssh/sshd_config
   ```

3. **Search for all lines containing a word ending with `Authentication`.**

   ```bash
   grep -E "\w*Authentication\b" /etc/ssh/sshd_config
   ```

4. **Search for all lines containing the word `Key`.**

   ```bash
   grep "Key" /etc/ssh/sshd_config
   ```

5. **Search for all lines beginning with `Password` and containing `yes`.**

   ```bash
   grep -E "^Password.*yes" /etc/ssh/sshd_config
   ```

6. **Search for all lines that end with `yes`.**

   ```bash
   grep -E "yes$" /etc/ssh/sshd_config
   ```

---