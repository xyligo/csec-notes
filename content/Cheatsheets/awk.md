---
title: Awk
tags:
  - awk
  - cheatsheet
---
AWK is a powerful text processing language, ideal for data extraction, reporting, and data-reformatting. This cheatsheet provides quick commands and usage examples for various AWK tasks.

## 1. Basic Syntax

### 1.1 Print Entire File

```bash
awk '{print}' file.txt
# Prints every line of the file.
```

### 1.2 Print Specific Columns

```bash
awk '{print $1, $3}' file.txt
# Prints the first and third columns of each line.
```

## 2. Field Separator

### 2.1 Specify Field Separator

```bash
awk -F',' '{print $2}' file.csv
# Uses comma as the field separator and prints the second column.
```

### 2.2 Multiple Field Separators

```bash
awk -F'[,:]' '{print $1, $2}' file.txt
# Uses either a comma or colon as the field separator.
```

## 3. Pattern Matching

### 3.1 Print Lines Matching Pattern

```bash
awk '/pattern/ {print}' file.txt
# Prints lines that match 'pattern'.
```

### 3.2 Print Lines Not Matching Pattern

```bash
awk '!/pattern/ {print}' file.txt
# Prints lines that do not match 'pattern'.
```

## 4. Built-in Variables

### 4.1 Number of Records

```bash
awk 'END {print NR}' file.txt
# Prints the number of records processed.
```

### 4.2 Filename

```bash
awk 'FNR==1 {print "Processing file:", FILENAME}' *.txt
# Prints filename of each file being processed.
```

## 5. Conditional Statements

### 5.1 If-Else

```bash
awk '{if ($1 > 50) print $1, "High"; else print $1, "Low"}' file.txt
# Prints 'High' if the first column is greater than 50, otherwise 'Low'.
```

### 5.2 Complex Conditions

```bash
awk '$1 > 50 && /pattern/ {print}' file.txt
# Prints lines where the first column is greater than 50 and 'pattern' is matched.
```

## 6. Arrays

### 6.1 Using Arrays

```bash
awk '{array[$1]++}' END {for (i in array) print i, array[i]}' file.txt
# Counts occurrences of each unique value in the first column.
```

## 7. String Functions

### 7.1 Length of String

```bash
awk '{print length($1)}' file.txt
# Prints the length of the first column.
```

### 7.2 Substring

```bash
awk '{print substr($1, 1, 3)}' file.txt
# Prints the first three characters of the first column.
```

## 8. Mathematical Functions

### 8.1 Random Number

```bash
awk 'BEGIN {srand(); print int(rand()*100)}'
# Prints a random number between 0 and 99.
```

## 9. File Inclusion

### 9.1 Include Another AWK Script

```bash
awk -f script.awk file.txt
# Executes commands from 'script.awk' on 'file.txt'.
```

## 10. References

- [GNU AWK Manual](https://www.gnu.org/software/gawk/manual/gawk.html)
