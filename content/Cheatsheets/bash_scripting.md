---
title: Bash Scripting
tags:
  - bash
  - scripting
  - cheatsheet
---
Bash (Bourne Again SHell) is a powerful scripting language used in many Unix-like operating systems. This cheatsheet covers basic and intermediate concepts useful for writing effective Bash scripts.

## 1. Script Structure

### 1.1 Shebang

```bash
#!/bin/bash
# This line tells the system to use bash to interpret the script.
```

### 1.2 Making a Script Executable

```bash
chmod +x scriptname.sh
# Adds executable permissions to the script.
```

## 2. Variables

### 2.1 Assigning Values

```bash
name="John"
age=30
# Strings need quotes; numbers do not.
```

### 2.2 Using Variables

```bash
echo $name
echo ${age} years old
# Curly braces are optional but useful for clarity.
```

## 3. User Input

### 3.1 Reading Input

```bash
read -p "Enter your name: " name
echo "Hello, $name!"
# Prompts user for input.
```

## 4. Conditional Statements

### 4.1 If Statement

```bash
if [ $age -gt 18 ]
then
    echo "You are an adult."
elif [ $age -eq 18 ]
then
    echo "Just turned 18!"
else
    echo "You are not an adult."
fi
```

### 4.2 Test Conditions

- `-eq`: equal
- `-ne`: not equal
- `-gt`: greater than
- `-lt`: less than
- `-ge`: greater than or equal to
- `-le`: less than or equal to

## 5. Loops

### 5.1 For Loop

```bash
for i in {1..5}
do
    echo "Looping: number $i"
done
```

### 5.2 While Loop

```bash
while [ $count -le 5 ]
do
    echo "Count: $count"
    count=$((count + 1))
done
```

## 6. Functions

### 6.1 Defining a Function

```bash
greet() {
    echo "Hello, $1!"
}
# $1 is the first argument passed to the function.
```

### 6.2 Calling a Function

```bash
greet "World"
```

## 7. Arrays

### 7.1 Declaring an Array

```bash
colors=('red' 'green' 'blue')
```

### 7.2 Accessing Array Elements

```bash
echo ${colors[0]} # red
echo ${colors[@]} # all elements
```

## 8. File and Directory Operations

### 8.1 Checking for a File

```bash
if [ -f "$file" ]; then
    echo "$file exists."
fi
```

### 8.2 Reading from a File

```bash
while read line; do
    echo $line
done < filename.txt
```

## 9. Debugging

### 9.1 Debug Mode

```bash
bash -x scriptname.sh
# Prints each command and its expanded arguments before executing it.
```

### 9.2 Setting Debug Mode Within a Script

```bash
set -x # Turn debug mode on
# Script lines here...
set +x # Turn debug mode off
```

## 10. Best Practices

- Quote your variables to handle spaces: `"$var"`
- Use `[[ ]]` for tests to prevent script errors.
- Prefer absolute paths for files to avoid wrong file execution.

## 11. References

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Learn Shell](https://www.learnshell.org/)
