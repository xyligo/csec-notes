---
title: NMap
tags:
  - nmap
  - cheatsheets
---
# General Scan

```sh
nmap -v -A -p- <IP>
```

`-v` Verbose

`-A` OS Detection, Version, Script Scanning

`-p-` All ports
## Specific Ports & Banners

```sh
nmap -v -sV -p 80,443,135 <IP>
```

`-sV` Open port scan to get service/version

`-p` Specific Ports

## Just Ping

```sh
nmap -v -sn <IP>
```

`-sn` Disables port scan

## Default Scripts

```sh
nmap -v -sC <IP>
```

`-sC` Run default scripts, same as `--script=default`

## UDP Scan

```sh
nmap -v -sU <IP>
```

-----------

## Common Switches List

```
-v     Verbosity
-sC    Common Scripts
-sU    UDP Scan
-sn    Ping Scan
-sV    Service/Version Discovery
-T*    Intensity (* being 1 to 5, 5 being most aggressive)
-p-    All Ports
-p *   Ports in range (* being 20-85, -1000, 200-, 20,21,53)
```