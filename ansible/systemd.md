# Manage services with systemd

The module helps to control systemd services on remote hosts

## Check if a service is running and start it, if it is not running

```
- name: Run service
  systemd:
    state: started
    name: httpd
```

## Check if a service is running and stop it, if it is running

```
- name: Run service
  systemd:
    state: stopped
    name: httpd
```

Other options for "state:" are

- reloaded - reload a service anyway
- restarted - restart a service

## Other parameters

| Parameter     | Choices | Comments                                                                                        |
| ------------- | ------- | ----------------------------------------------------------------------------------------------- |
| daemon_reload | yes/no  | runs daemon-reload                                                                              |
| daemon_reexec | yes/no  | Reexecute systemd manager                                                                       |
| force         | yes/no  | Yes option will override existing symlinks                                                      |
| masked        | yes/no  | A masked unit is impossible to start                                                            |
| enabled       | yes/no  | If Yes option selected, a service will start on boot                                            |
| no_block      | yes/no  | Asynchronous execution. Ansible will not wait for the job to complete to execute the other jobs |

Example

```
- name: enable a service and ensure it is not masked
  systemd:
    name: httpd
    enabled: yes
    masked: no
```
