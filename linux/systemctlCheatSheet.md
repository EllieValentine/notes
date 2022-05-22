# systemctl Cheat Sheet

| Command | Descriptoion |
| ------------- | ------------- | 
| systemctl stop service | Stop a running service |
| systemctl start service | Start a service |
| systemctl restart service | Restart a running service |
| systemctl reload service | Reload all config files in service |
| systemctl daemon-reload | Must run to reload changed unit files |
| systemctl status service | See if service is running/enabled |
| systemctl --failed | Shows services that failed to run |
| systemctl reset-failed | Resets any units from failed state |
vsystemctl enable service | Enable a service to start on boot |
| systemctl disable service | Disable service--won’t start at boot |
| systemctl show service | Show properties of a service (or other unit) |
| systemctl edit service | Create snippit to drop in unit file |
| systemctl edit --full service | Edit entire unit file for service |
| systemctl -H host status network | Run any systemctl command remotely |