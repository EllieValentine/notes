# Allow sudo commands for a specific user without a password promt.

## Debin based OS.

- in `/etc/sudoers`

```
# Allows user 'myuser' to reboot, update, upgrade, and remove.
myuser ALL=NOPASSWD:/sbin/reboot
myuser ALL=NOPASSWD:/usr/bin/apt update
myuser ALL=NOPASSWD:/usr/bin/apt -y upgrade
myuser ALL=NOPASSWD:/usr/bin/apt -y autoremove
```

### User may not be in sudoers.
