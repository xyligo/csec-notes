---
title: NMap
tags:
  - nmap
  - cheatsheet
---
## Basic Usage

```bash 
nmap <target> 
```

- IP address, hostname, or range (e.g., 192.168.1.1, example.com, 192.168.1.1/24).
- Performs a simple scan, listing open ports and their corresponding services.

## Scan Specific Ports

```bash 
nmap -p <port_range> <target> 
```

- **-p <port_range>**: Specify ports (e.g., `80`, `1-100`, `22,80,443`).
- Scans only the specified ports.

## Service Version Detection

```bash 
nmap -sV <target> 
```

- **-sV**: Detects version information of services running on open ports.

## OS Detection

```bash 
nmap -O <target> 
```

- **-O**: Attempts to detect the operating system of the target.

## Aggressive Scan

```bash 
nmap -A <target> 
```

- **-A**: Performs OS detection, version detection, script scanning, and traceroute.

## Stealth Scan (SYN Scan)

```bash 
nmap -sS <target> 
```

- **-sS**: Performs a stealthy TCP SYN scan.

## UDP Scan

```bash 
nmap -sU <target>
```

- **-sU**: Scans for open UDP ports.

## Scan Multiple Targets

```bash 
nmap <target1> <target2> ... <targetN> 
```

- Scan multiple targets separated by spaces.

## Scan Entire Network

```bash 
nmap <network_range> 
```

- **<network_range>**: Specify a range (e.g., `192.168.1.0/24`).
- Scans all IPs within the specified range.

## Disable DNS Resolution

```bash 
nmap -n <target> 
```

- **-n**: Disables DNS resolution for faster scanning.

## Timing and Performance

```bash 
nmap -T<0-5> <target> 
```

- **-T<0-5>**: Adjusts timing template (0=slowest, 5=fastest).

## Save Scan Results to File

```bash 
nmap -oN <filename> <target>
```

- **-oN**: Saves the output in a normal format.
- **-oX**: Saves the output in XML format.
- **-oG**: Saves the output in a grepable format.

## Scan with a Custom Script

```bash 
nmap --script <script_name> <target> 
```

- **--script <script_name>**: Runs the specified NSE script (e.g., `http-title`).

## Scan for Specific Service

```bash 
nmap -p <port> --script <service_name> <target> 
```

- **--script <service_name>**: Runs a script related to a specific service (e.g., `ssl-cert` on port 443).

## Scan for Vulnerabilities

```bash 
nmap --script vuln <target> 
```

- **--script vuln**: Runs multiple scripts to detect vulnerabilities.

## Traceroute

```bash 
nmap --traceroute <target> 
```

- **--traceroute**: Performs traceroute to map the path packets take to reach the target.

## Scan a List of Targets from a File

```bash 
nmap -iL <file_name> 
```

- **-iL <file_name>**: Scans targets from a specified list in a file.

## Evade Firewall/IDS

```bash 
nmap -D <decoy_IP1>,<decoy_IP2>,<target>
```

- **-D**: Uses decoys to hide the real source of the scan. 