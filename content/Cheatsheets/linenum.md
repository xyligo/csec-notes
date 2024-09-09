---
title: LinEnum
---
LinEnum is a shell script that automates the process of gathering information from a Linux system to help identify potential security vulnerabilities.

## 1. Basic Usage

### 1.1 Running LinEnum

```bash
./LinEnum.sh
# Runs the script with default options.
```

### 1.2 Running with Verbose Output

```bash
./LinEnum.sh -v
# Runs the script in verbose mode to provide more detailed output.
```

## 2. Script Options

### 2.1 Detailed Enumeration

```bash
./LinEnum.sh -t
# Runs thorough (detailed) tests.
```

### 2.2 Export to HTML

```bash
./LinEnum.sh -r report.html -h
# Outputs the results to an HTML file named 'report.html'.
```

### 2.3 Include Additional Checks

```bash
./LinEnum.sh -a
# Runs additional tests.
```

## 3. Key Checks Performed

### 3.1 System Information

- Kernel version
- Operating system details
- Network configuration

### 3.2 User Information

- Current user details
- Super users listing
- Users with console

### 3.3 Environmental Information

- Environment variables
- Sudo version
- Cron jobs

### 3.4 Security Information

- SUID/GUID files
- Config files accessible by current user
- Installed packages and potential vulnerabilities

## 4. Automating with Cron

### 4.1 Setup Cron Job

```bash
echo "*/5 * * * * /path/to/LinEnum.sh" | crontab -
# Sets up a cron job to run LinEnum every 5 minutes.
```

## 5. Tips for Effective Use

### 5.1 Updating Script

Regularly update the script from its GitHub repository to ensure the latest checks and features are included.

### 5.2 Combine with Other Tools

For a comprehensive security assessment, use LinEnum in conjunction with other tools like `pspy` and `chkrootkit`.

## 6. Download and Installation

### 6.1 Clone from GitHub

```bash
git clone https://github.com/rebootuser/LinEnum.git
# Clones the repository to get the latest version of the script.
```

### 6.2 Running from Remote Server

```bash
curl -O https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
chmod +x LinEnum.sh
./LinEnum.sh
# Downloads and runs the script directly from GitHub.
```

## 7. References

- [LinEnum GitHub Repository](https://github.com/rebootuser/LinEnum)
