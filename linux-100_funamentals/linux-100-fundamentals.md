# TCM Security - Linux 100 Fundamentals Notes

This repository contains my personal notes from the **Linux 100 Fundamentals** course by TCM Security. 
---

## 🧱 Basic Concepts and Commands

- `sudo` only works for users listed in the **sudoers** file.
- `sudo su -` is used to switch to the **root** user.
- In the prompt `kali@kali`, the first `kali` is the **username**, and the second is the **hostname**.
- `(kali㉿kali)-[~]`: `~` refers to the current user’s home directory.

---

## 📁 Navigation and Filesystem

- `cd ..` moves one directory up.
- `cd /` goes to the root directory.
- `pwd` prints the current working directory.
- `ls` lists directory contents.
- Use `Tab` to autocomplete paths or commands.
- You can list contents of any path without changing directory using `ls /etc`, `ls ~/Downloads`, etc.
- `mkdir` creates directories, `rmdir` removes them.
- You can specify full paths while using these commands from anywhere.
- Use `clear` or `Ctrl + L` to clear the screen.

---

## 🧰 Working with Files

- `echo "Hi" > test.txt`: Creates `test.txt` and writes "Hi".
- `echo "Hello again" >> test.txt`: Appends text to `test.txt`.
- `cp test.txt Downloads/`: Copies the file to the Downloads folder.
- `mv test.txt Downloads/`: Moves the file; it will no longer be in the original location.
- `rm test.txt`: Removes the file.
- `touch newfile.txt`: Creates an empty file or updates timestamp.
- `nano newfile.txt`: Opens the Nano editor to edit the file.
- `mousepad newfile.txt`: Opens the GUI Mousepad editor.
- Files and directories are **case-sensitive** (e.g., `Downloads` ≠ `downloads`).

---

## 🔍 Permissions and Users

- `ls -la`: Lists files with permissions.
  - Files: `-rw-r--r--`
  - Directories: Start with `d`, e.g., `drwxr-xr-x`
- Three permission groups:
  - **Owner**
  - **Group**
  - **Others**
- `chmod` changes permissions:
  - `chmod +x file.sh`: Adds execute permission.
  - `chmod 777 file.txt`: Gives full `rwx` permissions to all.
- Temporary files with `rwx` permissions are useful in pentesting.

### User Management

- `sudo adduser john`: Creates a user named **john**.
- `su john`: Switch to user **john**.
- `passwd`: Changes the current user's password.
- `cat /etc/passwd`: View user list on the system.
- `sudo cat /etc/sudoers`: View sudoers file.
- `sudo -l`: Check commands a user can run with `sudo`.

---

## 🌐 Networking

- `ip a` or `ifconfig`: Show IP address (wired).
- `iwconfig`: Show wireless network interfaces.
- `ip n` or `arp -a`: Show ARP cache / neighbor table.
- `ip r` or `route`: Display routing table.
- `ping <IP>`: Sends ICMP packets (Note: Disabled ICMP = No response).

---

## 🔁 Useful Terminal Tips

- Use the **Up Arrow** to view previous commands.
- Refer to manual pages:
  - `man ls`
  - `ls --help`
- [explainshell.com](https://explainshell.com) is a helpful resource for command breakdowns.

---

## ⚙️ Service Management

- `sudo service apache2 start`: Start Apache web server.
- `sudo service apache2 stop`: Stop Apache web server.
- `python3 -m http.server 80`: Start a basic HTTP server on port 80.
- `sudo systemctl enable ssh`: Enable SSH at boot.
- `sudo systemctl disable ssh`: Disable SSH at boot.

---

## 📦 Package Management

- `sudo apt update && sudo apt upgrade`: Update and upgrade all packages.
- `sudo apt install cron-daemon-common`: Install cron-related utilities.
- `sudo git clone https://github.com/Dewalt-arch/pimpmykali.git`: Clone a GitHub repository.

---

## 🐚 Bash Scripting Example: IP Sweep

```bash
#!/bin/bash

if [ "$1" == "" ]
then
  echo "You forgot an IP address!"
  echo "Syntax: ./ipsweep.sh 192.168.1"
else
  for ip in $(seq 1 254); do
    ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
  done
fi
```

*This script pings all IPs in a /24 subnet and extracts live hosts. It's a lightweight way to sweep for active devices on a local network.*


