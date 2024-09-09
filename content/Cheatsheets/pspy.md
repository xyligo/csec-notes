---
title: Pspy
tags:
  - pspy
  - cheatsheet
---

pspy is a command-line tool used to monitor ongoing processes on Linux systems without requiring root privileges, making it valuable for both system administrators and penetration testers.

## 1. Basic Usage

### 1.1 Downloading pspy

```bash
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.0/pspy32
# Download pspy32 bit version
chmod +x pspy32
# Make it executable
```

### 1.2 Running pspy

```bash
./pspy32
# Run pspy with default settings.
```

## 2. Advanced Options

### 2.1 Check for Root Processes

```bash
./pspy32 -p
# Show parent PIDs as well as their CMDs.
```

### 2.2 Increase Verbosity

```bash
./pspy32 -v
# Show verbose output (more detailed).
```

### 2.3 Monitor Specific Directories

```bash
./pspy32 -d /tmp,/var
# Monitor specified directories for process activity.
```

## 3. Monitoring File Activity

### 3.1 Watch File Openings

```bash
./pspy32 -f
# Monitor files being opened by processes.
```

### 3.2 Report New Files

```bash
./pspy32 -r
# Report new files when they are created.
```

## 4. Output Options

### 4.1 Save Output to File

```bash
./pspy32 > output.txt
# Redirect standard output to a file.
```

### 4.2 Combine Watching and Logging

```bash
./pspy32 -vf > activity.log
# Use verbose and file monitoring options, saving output to log file.
```

## 5. Using pspy in Penetration Testing

### 5.1 Identifying Cron Jobs

```bash
./pspy32
# Regularly check output for cron jobs or scheduled tasks.
```

### 5.2 Finding Misconfigured Services

```bash
./pspy32 -v
# Detect processes with potential misconfigurations or vulnerabilities.
```

## 6. Tips for Effective Monitoring

- Always choose the correct binary for your system architecture (32-bit or 64-bit).
- Combine pspy with other monitoring tools like `lsof` or `netstat` for comprehensive insights.
- Run pspy periodically or during suspected attack windows to catch unusual activities.

## 7. Download and Installation

### 7.1 Latest Release

```bash
# Download the latest release from the GitHub repository.
curl -L https://github.com/DominicBreuker/pspy/releases/latest/download/pspy64 > pspy64
chmod +x pspy64
./pspy64
```

## 8. References

- [pspy GitHub Repository](https://github.com/DominicBreuker/pspy)
