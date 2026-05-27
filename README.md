# 🐧 Phase 01 — Linux & Bash Scripting
---

## What You'll Learn

### File System & Permissions
- Understand inodes, hard links vs soft links
- Master `chmod`, `chown`, `chattr`, `lsattr`
- Research: sticky bit, setuid, setgid — what they are and when to use
- Practice: set up a shared directory with proper group permissions

### Users, Groups & sudoers
- Create/manage users with `useradd`, `usermod`, `userdel`
- Understand `/etc/passwd`, `/etc/shadow`, `/etc/group` structure
- Configure `/etc/sudoers` using `visudo` safely
- Research: difference between `su` and `sudo` — security implications

### Systemd & Process Management
- Write a custom `.service` unit file from scratch
- Master: `systemctl start/stop/enable/disable/status/reload`
- Use `journalctl -u`, `-f`, `--since` for log analysis
- Research: systemd targets vs old SysV runlevels
- Practice: make a Python script run as a persistent service

### Bash Scripting
- Variables, conditionals (`if/elif/else`), loops (`for/while/until`)
- Functions, positional parameters (`$1`, `$2`, `$@`, `$#`)
- Input handling: `read`, `getopts` for CLI argument parsing
- Error handling: exit codes, `set -e`, `set -o pipefail`, `trap`
- Research: difference between `[ ]` and `[[ ]]` in bash conditionals
- String manipulation: `grep`, `sed`, `awk` — learn each independently

### Cron Jobs & Task Scheduling
- Understand `crontab` syntax (minute hour dom month dow)
- Create user-level and system-level cron jobs
- Research: `anacron` vs `cron` — when does each make sense?
- Practice: schedule a log rotation script

### SSH & Remote Access
- Generate SSH keys: `ssh-keygen` (RSA vs ED25519 — research why ED25519 is preferred)
- Configure `~/.ssh/config` for multiple hosts
- Set up SSH server hardening: disable root login, change port, AllowUsers
- Research: SSH tunneling (local, remote, dynamic) — document use cases
- Practice: set up key-based auth between two VMs

---

## Final Project

### Automated Server Bootstrap Script

Write a Bash script that fully configures a fresh Ubuntu server:

- Installs specified packages
- Creates an admin user with SSH key
- Configures UFW firewall rules
- Sets up a cron job for disk-usage alerts
- Generates a setup report

**Requirements:**
- Script must handle errors gracefully
- Support `--dry-run` flag

### Deliverables
- `bootstrap.sh` with full error handling and logging
- `README.md` documenting every flag and expected behavior
- Tested on a fresh VM from scratch


## Commands Mastered So Far

| Command | Purpose | Example |
|---------|---------|---------|
| `pwd` | Print working directory | `pwd` |
| `cd /` `cd ~` | Change directory to root/home | `cd ~/devops-lab` |
| `ls -la` | List all files with details | `ls -la projects/` |
| `mkdir -p` | Create parent directories | `mkdir -p a/b/c` |
| `touch` | Create empty file | `touch file.txt` |
| `cat` | View file contents | `cat script.sh` |
| `cp` | Copy file | `cp source dest` |
| `mv` | Move/rename file | `mv old new` |
| `chmod +x` | Make executable | `chmod +x script.sh` |
| `ln` | Create hard link | `ln original hard` |
| `ln -s` | Create soft link | `ln -s original soft` |
| `ls -li` | Show inode numbers | `ls -li` |
| `chmod +t` | Add sticky bit | `chmod +t /shared` |
| `chmod u+s` | Add SetUID | `chmod u+s /bin/prog` |
| `chmod g+s` | Add SetGID | `chmod g+s /team-dir` |
| `chattr +i` | Make immutable | `sudo chattr +i config` |
| `lsattr` | List file attributes | `lsattr file.txt` |
| `groups` | Show user's groups | `groups` |
| `usermod -aG` | Add user to group | `sudo usermod -aG docker $USER` |

---

## Setup Guide — Ubuntu Server on VirtualBox

Follow these steps to recreate my exact learning environment.

### 1. Download Required Software

| Software | Download Link | Purpose |
|----------|---------------|---------|
| VirtualBox | [virtualbox.org](https://www.virtualbox.org/) | Run Ubuntu VM |
| Ubuntu Server 24.04 LTS | [ubuntu.com/download/server](https://ubuntu.com/download/server) | Linux distro for learning |

### 2. Create Virtual Machine

Open VirtualBox → Click **New** → Use these settings:

| Setting | Value |
|---------|-------|
| Name | `Ubuntu-Server-DevOps` |
| Folder | Anywhere you like |
| ISO Image | Select the downloaded Ubuntu Server ISO |
| Type | Linux |
| Version | Ubuntu (64-bit) |

**Hardware settings:**

| Component | Value |
|-----------|-------|
| RAM | 2048 MB (2GB) minimum, 4096 MB (4GB) recommended |
| CPU Cores | 2 |
| Disk Size | 25 GB (thin provisioned) |

**Network settings (IMPORTANT):**

| Setting | Value |
|---------|-------|
| Adapter 1 | Bridged Adapter (or NAT for offline learning) |
| Name | Your host's WiFi/Ethernet adapter |

### 3. Install Ubuntu Server

1. Start the VM
2. Choose **Try or Install Ubuntu Server**
3. Select language: **English**
4. Keyboard layout: **English (US)** — or your preference
5. Installation type: **Ubuntu Server**
6. Network connections: **DHCP** (default, auto-detects IP)
7. Proxy: Leave **blank**
8. Mirror: Keep **default**
9. Storage layout: **Use an entire disk** (default)
10. Storage encryption: **No** (optional for learning)
11. Profile setup:
    - Your name: `Your Name`
    - Server name: `devops-lab`
    - Username: `jad` (or your choice)
    - Password: Choose a strong password
12. **SSH setup screen — IMPORTANT:**
    - Check **Install OpenSSH server**
13. Featured snaps: **None** (skip)
14. Wait for installation to complete → **Reboot**

### 4. First Login

After reboot, login with your username and password:

```bash
# You'll see:
devops-lab login: jad
Password: [your password]

# Welcome message appears
jad@devops-lab:~$



### 5. Install Essential Tools

# Update package list and upgrade all packages
sudo apt update && sudo apt upgrade -y

# Install essential DevOps tools
sudo apt install -y \
    net-tools \        # Network utilities (ifconfig, netstat)
    curl \             # Transfer data from/to servers
    wget \             # Download files from the internet
    git \              # Version control system
    vim \              # Advanced terminal text editor
    nano \             # Simple terminal text editor
    htop \             # Interactive process viewer (better than top)
    tree \             # Display directory structure as a tree
    tmux \             # Terminal multiplexer (multiple windows)
    ufw \              # Uncomplicated Firewall
    rsync \            # Fast file copying and synchronization
    man-db \           # Manual pages database (man command)
    bash-completion    # Tab completion for bash commands


### 6. Enable SSH for Remote Access (from your host machine)

# Enable SSH to start on boot
sudo systemctl enable ssh --now

# Check SSH is running
sudo systemctl status ssh

# Find your VM's IP address
ip a | grep inet

# Look for something like: inet 192.168.x.x or 172.20.x.x


### 7. Connect from Your Host Machine
ssh jad@[VM-IP-ADDRESS]
