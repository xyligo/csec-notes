---
title: Metasploit
tags:
  - metasploit
  - cheatsheet
---
## Basic Usage 
```bash
msfconsole                   # Start Metasploit console
search <keyword>             # Search exploits, payloads, etc.
use <module>                 # Select a module to use
info                         # Get information about the selected module
show options                 # Show available options for the selected module
set <option> <value>         # Set a specific option for the module
setg <option> <value>        # Set a global option
unset <option>               # Unset a specific option
run / exploit                # Run the selected module
sessions -i <id>             # Interact with a session
exit                         # Exit the console
```

## Database Commands
```bash
db_status                    # Check the database status
workspace -a <name>          # Add a new workspace
workspace <name>             # Switch to a workspace
hosts                        # List hosts in the database
services                     # List services in the database
vulns                        # List vulnerabilities in the database
creds                        # List credentials in the database
loot                         # List collected loot in the database
notes                        # List notes in the database
```

## Exploit Usage
```bash
use exploit/<path>           # Use a specific exploit
show targets                 # Show available targets for the exploit
set TARGET <id>              # Set the target for the exploit
set RHOSTS <IP>              # Set the target IP address
set RPORT <port>             # Set the target port
check                        # Check if the target is vulnerable
exploit -j                   # Run the exploit in the background as a job
exploit -z                   # Exploit and do not interact with the session
```

## Payloads
```bash
show payloads                # Show available payloads
set PAYLOAD <payload>        # Set the payload for the exploit
set LHOST <IP>               # Set the local host IP
set LPORT <port>             # Set the local port
```

## Post-Exploitation
```bash
use post/<module>            # Use a post-exploitation module
set SESSION <id>             # Set the session to run the module on
run                          # Run the post-exploitation module
```

## Auxiliary Modules
```bash
use auxiliary/<module>       # Use an auxiliary module
set RHOSTS <IP>              # Set the target IP address
set THREADS <number>         # Set the number of concurrent threads
run                          # Run the auxiliary module
```

## Meterpreter Commands
```bash
sysinfo                      # Get system information
getuid                       # Get the user ID of the session
download <file>              # Download a file from the target machine
upload <file>                # Upload a file to the target machine
shell                        # Drop into a shell on the target machine
background                   # Background the current session
ps                           # List running processes
migrate <pid>                # Migrate the session to another process
keyscan_start                # Start capturing keystrokes
keyscan_dump                 # Dump captured keystrokes
screenshare                  # Start a live screen share session
screenshot                   # Take a screenshot of the target machine
hashdump                     # Dump the hashes from the target machine
```