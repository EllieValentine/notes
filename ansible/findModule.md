# Find module

A convinient way to search for files and/or directories. The result can be stored in a variable (for example, matches). Note: By default, the Find module only looks for files, and examines the given directory itself without searching in subdirectories.

Example

```
- name: find example
    find:
      paths: /home/example/findmodule
      patterns: "*.txt"
      register: matches

  - debug:
      msg: "{{ matches.files }}"
```

## Search for directories

add file_type: "directory"

```
- name: find example
    find:
      paths: /home/example/findmodule
      patterns: "backup_*"
      file_type: "directory"
      register: matches

- debug:
    var: matches.stdout
```

## Recursive search

add recurse: yes

```
- name: find example
    find:
      paths: /home/example/findmodule
      patterns: "backup_*"
      recurse: yes
      register: matches

- debug:
    var: matches.stdout
```

## Use multiple patterns in a single search

```
- name: find example
    find:
      paths: /home/example/findmodule
      patterns: "*.backup,*.log"
      recurse: yes
      register: matches

- debug:
    var: matches.stdout
```

## Use Python regex

add use_regex: yes

The example below will look for a filename followed by 1 digit, such as filename1.log, filename2.log

```
- name: find example
    find:
      paths: /home/example/findmodule
      patterns: "filename[\\d].log"
      use_regex: yes
      recurse: yes
      register: matches

- debug:
    var: matches.stdout
```

## Other options

- hidden: yes - include hidden files, otherwise they'll be ignored.
- size: "5m" or size: "100k" - specify the size. Command looks for files that are equal to or greater than the specified size.
- follow: yes - follow symlinks.
- excludes: 'pattern1,pattern2' - Multiple patterns can be specified using a list.
- age: 30d - In seconds, minutes, hours, days, or weeks (use the first letter of any of those words (e.g., "1s")
- age_stamp: mtime - Choose the file property against which we compare age (atime, ctime, mtime).

## Ansible Find and Delete files playbook example

```
---
- name: Ansible Find Example
  hosts: all
  tasks:
   - name : Find temporary files
     become: yes
     find:
       paths: /home/example/findmodule
       patterns: '*.tmp'
       recurse: yes
       register: matches

   - name: Delete the temporary files
     become: yes
     file:
       path: "{{item.path}}"
       state: absent
     with_items: "{{ matches.files }}"

```
