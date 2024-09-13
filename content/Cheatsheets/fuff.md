---
title: Fuff
tags:
  - fuff
  - cheatsheet
---

FFUF is a fast web fuzzer written in Go, used for directory discovery, virtual host discovery, and fuzzing web applications. This cheatsheet covers common FFUF commands and options for effective use.

## 1. Basic Usage

### 1.1 Directory Brute-Forcing

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt
# Uses FUZZ keyword to brute-force directories using a wordlist.
```

### 1.2 Virtual Host Discovery

```bash
ffuf -u http://FUZZ.example.com -w /path/to/wordlist.txt -H "Host: FUZZ.example.com"
# Discovers virtual hosts using a wordlist.
```

## 2. HTTP Methods and Headers

### 2.1 Specify HTTP Method

```bash
ffuf -u http://example.com/FUZZ -X POST -w /path/to/wordlist.txt
# Uses POST as the HTTP method instead of the default GET.
```

### 2.2 Add Custom Headers

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -H "User-Agent: CustomAgent"
# Adds a custom User-Agent header to requests.
```

## 3. Filtering Options

### 3.1 Filter by Status Codes

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -fc 403,404
# Filters out results with status codes 403 and 404.
```

### 3.2 Filter by Response Size

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -fs 0
# Filters out responses with a size of 0 bytes.
```

### 3.3 Filter by Words or Lines

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -fw 10
# Filters responses with exactly 10 words.
```

## 4. Recursion

### 4.1 Recursive Scanning

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -recursion -recursion-depth 2
# Enables recursive scanning up to a depth of 2 levels.
```

## 5. Output Options

### 5.1 Save Results to a File

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -o output.json -of json
# Saves the output in JSON format to a file.
```

### 5.2 Quiet Mode

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -s
# Runs FFUF in silent mode with minimal output.
```

## 6. Speed and Performance

### 6.1 Set Number of Threads

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -t 100
# Sets the number of concurrent threads to 100.
```

### 6.2 Request Timeout

```bash
ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -timeout 10
# Sets the request timeout to 10 seconds.
```

## 7. Advanced Usage

### 7.1 Multiple Fuzz Points

```bash
ffuf -u http://example.com/FUZZ1/FUZZ2 -w /path/to/wordlist1.txt:/path/to/wordlist2.txt
# Uses multiple fuzz points with different wordlists.
```

### 7.2 Fuzz POST Data

```bash
ffuf -u http://example.com/post -X POST -d "username=FUZZ&password=FUZZ" -w /path/to/wordlist.txt
# Fuzzes POST data fields.
```

## 8. Useful Wordlists

- **SecLists**: [SecLists GitHub Repository](https://github.com/danielmiessler/SecLists)
- **Dirbuster**: Commonly used wordlists for directory and file discovery.

## 9. References

- [FFUF GitHub Repository](https://github.com/ffuf/ffuf)
- [FFUF Documentation](https://github.com/ffuf/ffuf#usage)
