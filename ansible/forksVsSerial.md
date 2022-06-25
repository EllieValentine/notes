# Ansible forks and serial

Ansible uses forks and serial keywords to define how many hosts it should manage at a single time

## Forks

By default Ansible is configured to use 5 separate parallel processes to perform tasks on different servers. The setting can be found in the configuration file /etc/ansible/ansible.cfg

```
[defaults]
forks = 5
```

Today CPU capabilities on the management server and the communication channels allow more hosts to be served at the same time. The optimal value must be determined experimentally.

```
[defaults]
forks = 30
```

For a better performance, you can also increase internal_poll_interval which is indicates how often Ansible checks for the results of the module execution. The larger the value of the parameter, the lower the load of the control machine CPU, the more resources available for forking.

```
[defaults]
internal_poll_interval = 0.001
```
