# - copy:

## Copies files to remote locations

```
- copy:
    src: /mine/ntp.conf
    dest: /etc/ntp.conf
    owner: root *
    group: root *
    mode: 0644 *
    backup: yes *

           * - optional
```

## Other options 

- remote_src: yes - will search for src at remote/target machine
- force: yes - will replace the remote file when contents are different than the source. If No - the file will only be transferred if the destination does not exist. 
- directory_mode: - the entire directory and its contents will be recursively copied to the destination. If only the contents of the directory need to be copied leaving out the outer directory, then src should end with a forward slash /

