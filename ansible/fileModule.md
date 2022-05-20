# File module

The File module simplifies the process of creating and deleting files, directories, soft and hard links, changing permissions, and more.

## Create a file

```
  - name: create a file
    file:
      path: /home/example/filemodule/new_file
      state: touch
```

## Create a directory

```
- name: create a directory if it does not exist
  file:
    path: /home/example/filemodule/new_dir
    state: directory
    mode: '0755'
```

## Change file ownership, group and permissions recursively

```
- name: change permissions
    file:
      path: /home/example/filemodule/test
      state: directory
      owner: root
      group: root
      mode: 0755
      recurse: true
```

## Delete a directory, file

```
- name: delete a directory recursively
  file:
    path: /home/example/filemodule/test
    state: absent
```

```
- name: delete files in a directory
    file:
      path: "{{ item }}"
      state: absent
    with_items:
    - /home/example/filemodule/test1.txt
    - /home/example/filemodule/test2.txt
    - /home/example/filemodule/test3.txt
```

## Create a link

```

- name: create a symbolic link
  file:
    src: /home/example/filemodule/from
    dest: /home/example/filemodule/dest
    owner: root
    group: root
    state: link

```

```

- name: Create a hard link
  file:
    src: /home/example/filemodule/from
    dest: /home/example/filemodule/dest
    state: hard

```

## The most useful parameters

| Parameter                   | Options                                           | Description                                   |
| --------------------------- | ------------------------------------------------- | --------------------------------------------- |
| recurse                     | yes/no                                            | Recursively set the specified file attributes |
| owner/group                 |                                                   | To set/change ownership                       |
| mode                        | any standart permissions                          | To set/change permissions                     |
| path                        |                                                   | Path to the file / dir                        |
| state                       | absent / directory / file / hard / link / touch / | Triggers an action                            |
| dest / src / force / follow |                                                   | Parameters for links                          |
