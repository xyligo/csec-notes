---
title: Hashcat
tags:
  - hashcat
  - cheatsheet
---

Hashcat is an advanced password recovery tool that uses GPU acceleration to crack a wide range of hash types. This cheatsheet provides essential commands and usage scenarios for effective use of Hashcat.

## 1. Basic Usage

### 1.1 Checking Hashcat Version

```bash
hashcat --version
# Displays the version of Hashcat.
```

### 1.2 List Supported Hash Types

```bash
hashcat --help | grep -A1 HASHTYPES
# Shows supported hash types with their corresponding mode numbers.
```

### 1.3 Example Hashes

```bash
hashcat --example-hashes
# Shows example hashes for different hash types.
```

## 2. Attack Modes

### 2.1 Straight (Dictionary Attack)

```bash
hashcat -m <mode> -a 0 <hashfile> <wordlist>
# Use a wordlist to perform a dictionary attack.
```

### 2.2 Combination Attack

```bash
hashcat -m <mode> -a 1 <hashfile> <wordlist1> <wordlist2>
# Combine words from two lists to crack passwords.
```

### 2.3 Brute-Force Attack

```bash
hashcat -m <mode> -a 3 <hashfile> ?d?d?d?d
# Use a brute-force attack pattern to crack four-digit passwords.
```

### 2.4 Hybrid Attack (Wordlist + Mask)

```bash
hashcat -m <mode> -a 6 <hashfile> <wordlist> ?d?d
# Append two digits to each word from the wordlist.
```

### 2.5 Hybrid Attack (Mask + Wordlist)

```bash
hashcat -m <mode> -a 7 <hashfile> ?d?d <wordlist>
# Prepend two digits to each word from the wordlist.
```

## 3. Hash Modes

### 3.1 MD5

```bash
hashcat -m 0 <hashfile> <wordlist>
# Mode number for MD5 is 0.
```

### 3.2 SHA-256

```bash
hashcat -m 1400 <hashfile> <wordlist>
# Mode number for SHA-256 is 1400.
```

### 3.3 WPA/WPA2

```bash
hashcat -m 2500 <hashfile> <wordlist>
# Mode number for WPA/WPA2 is 2500.
```

## 4. Advanced Options

### 4.1 Show Cracked Passwords

```bash
hashcat -m <mode> --show <hashfile>
# Display cracked passwords.
```

### 4.2 Save/Resume Session

```bash
hashcat -m <mode> --session <name> <hashfile>
# Save progress to a session for later resumption.
```

### 4.3 Restore Session

```bash
hashcat --restore --session <name>
# Resume a previously saved session.
```

### 4.4 Specify Workload Profile

```bash
hashcat -m <mode> -w 4 <hashfile>
# Set the workload profile from 1 (light) to 4 (nightmare).
```

## 5. Utilities

### 5.1 Convert CAP to HCCAPX

```bash
cap2hccapx.bin <capfile> <outputfile.hccapx>
# Convert Wi-Fi capture files for use with Hashcat.
```

### 5.2 Generate a Rule File

```bash
hashcat --stdout -r <rulefile> <wordlist> > <outputwordlist>
# Apply rules to a wordlist and save the output.
```

## 6. Performance Tuning

### 6.1 Benchmarking

```bash
hashcat -b
# Run a benchmark to test performance on your hardware.
```

### 6.2 Limiting GPU Usage

```bash
hashcat -m <mode> --gpu-temp-retain=<temperature> <hashfile>
# Limit GPU temperature to avoid overheating.
```

## 7. References

- [Hashcat Advanced Password Recovery](https://hashcat.net/hashcat/)
- [Hashcat Wiki](https://hashcat.net/wiki/)
