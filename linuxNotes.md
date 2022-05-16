# Kill

## -9 (SIGKILL)

immidiately stop the process; the most unsafe way to kill a process that terminates a process without saving; use for misbehaving processes.

## -15 (SIGTERM)

a graceful shutdown; the default and safest way to kill a process.

## usage

### kill -9 1234

same as

### kill -SIGKILL 1234

---

# Permissions

## If root can't remove its file, check attributes

### # lsattr

if you notice i (immutable) or a (append-only), remove those attributes:

### # chattr -i [filename]

### # chattr -a [filename]

---

# Hardening:

## Disable root login (4 ways)

### 1. Set "PermitRootLogin no" in /etc/ssh/sshd_config

### 2. Change the Login Shell to /usr/sbin/nologin in /etc/passwd

sudo usermod -s /usr/sbin/nologin root
The account will automatically exit the shell

### 3. Disable Root Login in Linux with passwd Command

### # sudo passwd -l root

It locks the password for the root user until a new one is set

### 4. Disable Root Login Using the usermod Command

### # sudo usermod -L root

It locks the password for the root user until a new one is set

---

# Performance

## CPU

### top command

Continuously monitoring top CPU consuming processes in Linux

### # top

### htop utility

Same monitoring with nice visualization and preset filters

### # htop

# SSH

## Quiet mode

To suppress most warning and diagnostic messages add -q

### #ssh -q USER@SERVER "YOUR COMMAND"

## sudo via SSH

Add -t to the SSH command

### #ssh -t USER@SERVER "sudo YOUR COMMAND"
