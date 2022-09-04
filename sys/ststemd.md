# Systemd

## Main commands

```sh
# List services
# https://www.tecmint.com/list-all-running-services-under-systemd-in-linux/
systemctl list-units --type=service

# Log at different levels what is in systemctl/journalctl (change up to 6(?) to see more stuff)
sudo journalctl -p 3 -xb
sudo journalctl -u xxx.service -p 6 -xb

# Edit unit file
vim /etc/systemd/system/xxxxxx.service

# Reload all systemd unit files (to do after a change in those)
systemctl daemon-reload

# Restart service
systemctl restart rsyslog
```

## Sidekicks
```sh
# Get the environment variables (and other things, from the PID of a process, listed by status command)
strings /proc/78747/environ

# Get the user running a process by PID
ps -u -p 78747
```