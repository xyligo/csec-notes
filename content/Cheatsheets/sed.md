---
title: Sed
tags:
  - sed
  - cheatsheet
---
Sed is a stream editor for filtering and transforming text. It's commonly used for text substitutions, more complex edits, and data extraction. This cheatsheet provides a quick reference to essential sed commands for various text manipulation tasks.

## 1. Basic Usage

### 1.1 Substitute Command

```bash
sed 's/old/new/' file.txt
# Replaces the first occurrence of 'old' with 'new' in each line.
```

### 1.2 Global Replacement

```bash
sed 's/old/new/g' file.txt
# Replaces all occurrences of 'old' with 'new' in each line.
```

## 2. Advanced Patterns

### 2.1 Substitute with Flags

```bash
sed 's/old/new/gi' file.txt
# Replaces all occurrences of 'old' with 'new' case-insensitively.
```

### 2.2 Address Ranges

```bash
sed '2,5s/old/new/g' file.txt
# Applies the substitution only from line 2 to line 5.
```

### 2.3 Address Patterns

```bash
sed '/start/,/end/s/old/new/g' file.txt
# Applies the substitution between lines containing 'start' and 'end'.
```

## 3. Deleting Text

### 3.1 Delete Lines

```bash
sed '3d' file.txt
# Deletes the third line.
```

### 3.2 Delete Range

```bash
sed '2,4d' file.txt
# Deletes lines from 2 to 4.
```

### 3.3 Delete Matching

```bash
sed '/pattern/d' file.txt
# Deletes lines matching 'pattern'.
```

## 4. Insertion and Appending

### 4.1 Insert Before a Line

```bash
sed '4i\New line' file.txt
# Inserts 'New line' before line 4.
```

### 4.2 Append After a Line

```bash
sed '4a\New line' file.txt
# Appends 'New line' after line 4.
```

## 5. Advanced Editing

### 5.1 Modifying Line

```bash
sed '3c\New content' file.txt
# Changes line 3 to 'New content'.
```

### 5.2 Transform Characters

```bash
sed 'y/abc/ABC/' file.txt
# Transforms 'a' to 'A', 'b' to 'B', 'c' to 'C' in all lines.
```

## 6. In-place Editing

### 6.1 Edit File Directly

```bash
sed -i 's/old/new/g' file.txt
# Edits file in-place, replacing 'old' with 'new'.
```

### 6.2 Backup Before In-place Edit

```bash
sed -i'.bak' 's/old/new/g' file.txt
# Creates a backup with '.bak' extension before editing.
```

## 7. Practical Examples

### 7.1 Clean Up HTML Tags

```bash
sed 's/<[^>]*>//g' file.html
# Removes all HTML tags from the file.
```

### 7.2 Print Specific Lines

```bash
sed -n '45,50p' file.txt
# Prints lines 45 to 50.
```

## 8. References

- [GNU Sed Manual](https://www.gnu.org/software/sed/manual/sed.html)
