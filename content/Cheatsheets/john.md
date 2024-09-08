---
title: John the Ripper
tags: 
  - john
  - john the ripper
  - cheatsheet
---
John the Ripper (JtR) is a fast password cracker, primarily for cracking passwords using dictionary attacks, brute force, and hybrid attack modes. Here are some common commands and techniques to effectively use John the Ripper.

## 1. Basic Usage

### 1.1 Checking John Version

```bash
john --version
# Displays the version of John the Ripper.
```

### 1.2 Password Cracking

```bash
john [options] <password-file>
# Start cracking password hashes.
```

### 1.3 Show Cracked Passwords

```bash
john --show <password-file>
# Show all cracked passwords from a given password file.
```

## 2. Attack Modes

### 2.1 Dictionary Attack

```bash
john --wordlist=<dictionary> <password-file>
# Use a wordlist to perform a dictionary attack.
```

### 2.2 Single Crack Mode

```bash
john --single <password-file>
# Use single crack mode, ideal for simple passwords.
```

### 2.3 Incremental Mode

```bash
john --incremental <password-file>
# Use incremental mode for brute-forcing passwords.
```

### 2.4 External Mode

```bash
john --external=<mode> <password-file>
# Use an external mode, like a custom script or filter.
```

## 3. Advanced Options

### 3.1 Format Specification

```bash
john --format=<format> <password-file>
# Specify the format of the hash (e.g., md5, sha256).
```

### 3.2 Session Management

```bash
john --session=<name> <password-file>
# Save progress to a session for later resumption.
```

### 3.3 Resuming a Session

```bash
john --restore=<name>
# Resume a previously started and saved session.
```

### 3.4 List Formats

```bash
john --list=formats
# List all supported hash formats.
```

### 3.5 Parallel Processing

```bash
john --fork=<n> <password-file>
# Split the job into 'n' processes for parallel processing.
```

## 4. Configuration and Customization

### 4.1 Custom Rules

```bash
john --rules=<custom-rule> <password-file>
# Apply custom rules for more complex cracking strategies.
```

### 4.2 Wordlist Rules

```bash
john --wordlist=<dictionary> --rules <password-file>
# Apply wordlist with rules for modified dictionary attacks.
```

### 4.3 Configuration File

```bash
john --config=<path-to-config> <password-file>
# Use a custom configuration file.
```

## 5. Utilities

### 5.1 Unshadow Tool

```bash
unshadow <passwd-file> <shadow-file> > combined.txt
# Combine passwd and shadow files for UNIX-like systems.
```

### 5.2 Password Hash Extraction

```bash
john --pot=<output-file> --show <password-file>
# Extract cracked passwords and save them in a file.
```

## 6. Performance Tuning

### 6.1 Benchmarking

```bash
john --test
# Benchmarking John's performance on your system.
```

### 6.2 Tuning Options

```bash
john --max-run-time=<seconds> <password-file>
# Limit the runtime to prevent excessive processing.
```

## 7. References

- [John the Ripper Official Site](https://www.openwall.com/john/)
- [Openwall Community Wiki](https://openwall.info/wiki/john)
