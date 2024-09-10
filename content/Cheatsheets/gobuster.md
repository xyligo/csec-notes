---
title: Gobuster
tags: 
  - gobuster
  - cheatsheet
---

Gobuster is a popular directory/file and DNS busting tool used in penetration testing and security assessments. It is designed to brute-force URIs (directories and files) in web sites, DNS subdomains, virtual host names, and Amazon S3 buckets. This cheatsheet provides a quick reference to essential Gobuster commands and options.

## 1. Basic Usage

### 1.1 Directory Brute-Forcing

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt
# Brute-forces directories and files using a wordlist.
```

### 1.2 DNS Subdomain Brute-Forcing

```bash
gobuster dns -d example.com -w /path/to/wordlist.txt
# Finds DNS subdomains using a wordlist.
```

### 1.3 Virtual Host Brute-Forcing

```bash
gobuster vhost -u http://example.com -w /path/to/wordlist.txt
# Identifies virtual hosts on a target web server.
```

## 2. Advanced Options

### 2.1 Custom Status Codes

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -s 200,204,301,302,307,403
# Filters results to include specific status codes.
```

### 2.2 Specify Extensions

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -x php,html,txt
# Appends extensions to each wordlist entry.
```

### 2.3 Recursion

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -r
# Enables recursion for found directories.
```

## 3. Output Options

### 3.1 Save Results to a File

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -o output.txt
# Saves the scan results to a specified file.
```

### 3.2 Quiet Mode

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -q
# Runs Gobuster in quiet mode (less verbose).
```

## 4. Speed and Performance

### 4.1 Set Number of Threads

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -t 50
# Sets the number of concurrent threads (default is 10).
```

### 4.2 Request Timeout

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -to 5s
# Sets the request timeout to 5 seconds.
```

## 5. Proxy and Headers

### 5.1 Use a Proxy

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -p http://127.0.0.1:8080
# Routes traffic through a specified proxy.
```

### 5.2 Add Custom Headers

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -H "User-Agent: CustomAgent"
# Adds custom headers to the request.
```

## 6. Useful Wordlists

- **SecLists**: [SecLists GitHub Repository](https://github.com/danielmiessler/SecLists)
- **SVNDigger**: [SVNDigger Wordlists](https://github.com/mazen160/svndigger)

## 7. Common Use Cases

### 7.1 Brute-Force Hidden Files

```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -x bak,old,backup
# Finds hidden backup files with common extensions.
```

### 7.2 Brute-Force S3 Buckets

```bash
gobuster s3 -w /path/to/wordlist.txt
# Attempts to discover accessible S3 buckets using a wordlist.
```

## 8. References

- [Gobuster GitHub Repository](https://github.com/OJ/gobuster)
- [Gobuster Documentation](https://github.com/OJ/gobuster#usage)
