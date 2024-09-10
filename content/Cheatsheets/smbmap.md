---
title: SMBMap
tag: 
  - smbmap
  - cheatcheet
---

SMBMap is a tool that allows users to enumerate and access Samba share drives across an internal network. It's a useful utility for penetration testers and network administrators to assess SMB shares for vulnerabilities and misconfigurations.

## 1. Basic Usage

### 1.1 List Shares on a Host

```bash
smbmap -H 192.168.1.1
# Lists all SMB shares on the specified host.
```

### 1.2 Authenticate with Credentials

```bash
smbmap -H 192.168.1.1 -u username -p password
# Uses the specified username and password to authenticate.
```

### 1.3 Using a Password Hash

```bash
smbmap -H 192.168.1.1 -u username -H <NTLM_hash>
# Authenticates using an NTLM hash instead of a password.
```

## 2. File and Directory Operations

### 2.1 List Contents of a Share

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name
# Lists files and directories in the specified share.
```

### 2.2 Download a File

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name -A file_name -q
# Downloads a file from the specified share.
```

### 2.3 Upload a File

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name -U /local/file/path -p /remote/file/path
# Uploads a local file to the specified share.
```

## 3. Permissions and Access

### 3.1 Check Writable Shares

```bash
smbmap -H 192.168.1.1 -u username -p password -R share_name
# Checks for writable directories and files within a share.
```

### 3.2 Search for Sensitive Files

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name -A "*.conf"
# Searches for files with specific patterns, like configuration files.
```

## 4. Recursive Operations

### 4.1 Recursively List Files

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name -R
# Recursively lists all files in the share.
```

### 4.2 Search Recursively for Files

```bash
smbmap -H 192.168.1.1 -u username -p password -r share_name -A "*.log" -R
# Recursively searches for files matching a pattern, like log files.
```

## 5. Advanced Options

### 5.1 Execute a Command

```bash
smbmap -H 192.168.1.1 -u username -p password --exec "ipconfig"
# Executes a command on the remote system via SMB.
```

### 5.2 Use a Proxy

```bash
smbmap -H 192.168.1.1 -u username -p password --proxy "http://127.0.0.1:8080"
# Routes traffic through a specified proxy.
```

## 6. Common Use Cases

### 6.1 Enumerate Shares with Guest Access

```bash
smbmap -H 192.168.1.1 -u guest
# Checks for shares accessible with guest/anonymous access.
```

### 6.2 Mount a Share Locally

```bash
mount -t cifs //192.168.1.1/share_name /mnt/share -o username=user,password=pass
# Mounts an SMB share to a local directory.
```

## 7. References

- [SMBMap GitHub Repository](https://github.com/ShawnDEvans/smbmap)
- [SMBMap Documentation](https://github.com/ShawnDEvans/smbmap#usage)
