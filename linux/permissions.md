# Linux file and directory permissions

## Permissions diagram

<pre>
 -rwxrw-r-x 1 owner group  
 |...................... file type
  |||................... owner's permissions
     |||................ group's permissions
        |||............. other's permissions
            |........... # of hardlinks
</pre>

## File Permission types

- read – allows to read the contents of the file.

- write – allows to write or modify a file or directory.

- execute – allows to execute a file or view the contents of a directory.

## Directory Permissions types

- read - allows to list content of the directory (x attribute needs to be set at the same time).

- write - allows to create, deleted or rename
  files within the directory (x attribute needs to be set at the same time).

- execute - allows to enter to a directory.

## Modifying the permissions

chmod command is used to modify the permissions. There are two defined ways to set permissions: symbolic and absolute.

### Symbolic Mode

Use combinations of letters and symbols to add permissions or remove permissions.

Examples

<pre>
chmod a+rw file.txt
chmod o-w file.txt
</pre>

Values

| Groups        | Types       | Operator   |
| ------------- | ----------- | ---------- |
| u – Owner     | r – Read    | + - Add    |
| g – Group     | w – Write   | - - Remove |
| o – Others    | x – Execute | = - Assign |
| a – All users |             |            |

### Absolute Mode

Use numbers to represent file permissions.

Examples

<pre>
chmod 777 file.txt
chmod 644 file.txt
</pre>

Values

| Octal Value | File Permissions Set | Permissions Description              |
| ----------- | -------------------- | ------------------------------------ |
| 0           | ---                  | No permissions                       |
| 1           | --x                  | Execute permission only              |
| 2           | -w-                  | Write permission only                |
| 3           | -wx                  | Write and execute permissions        |
| 4           | r--                  | Read permission only                 |
| 5           | r-x                  | Read and execute permissions         |
| 6           | rw-                  | Read and write permissions           |
| 7           | rwx                  | Read, write, and execute permissions |

## Most common file permissions

| Value | Representation | Meaning                                                                                      |
| ----- | -------------- | -------------------------------------------------------------------------------------------- |
| 777   | rwxrwxrwx      | Anybody may do anything.                                                                     |
| 755   | rwxr-xr-x      | Owner has all permissions. All others may read and execute the file.                         |
| 700   | rwx------      | Owner has all permissions. Others has none                                                   |
| 666   | rw-rw-rw       | All users may read and write the file.                                                       |
| 644   | rw-r--r--      | The owner may read and write a file. Others may only read the file.                          |
| 600   | rw-------      | Only the owner may read and write to a file. No one else can read, write or execute the file |

## Most common directory permissions

| Value | Representation | Meaning                                                                               |
| ----- | -------------- | ------------------------------------------------------------------------------------- |
| 777   | rwxrwxrwx      | No restrictions on permissions.                                                       |
| 755   | rwxr-xr-x      | The owner has full access. Others may list files, but cannot create nor delete files. |
| 700   | rwx------      | Only the owner has full access. Others can't even list files.                         |
