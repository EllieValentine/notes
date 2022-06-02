# Bash Find command

Find is a command line utility that can be used to find files and directories which satisfy certain conditions, and perform some operations on them.

## Basic syntax

<pre>
$ find [options] [path...] [expression]
</pre>

Example

<pre>
$ find . -name "*.log"
</pre>

## Symbolic link options

| Option | Description                                                                      |
| ------ | -------------------------------------------------------------------------------- |
| -P     | Never follow symbolic links. Default behaviour if no option specified            |
| -L     | Follow symbolic links                                                            |
| -H     | Do not follow symbolic links, except while processing the command line arguments |

If more than one options is specified, the only last one will be taken to effect.

## Depth of the directory traversal

How many subdirectories include/exlude from search

| Option    | Description                                                                                                    |
| --------- | -------------------------------------------------------------------------------------------------------------- |
| -maxdepth | How many levels of directories to include below the starting point. maxdepth 0 means start from starting point |
| -mindepth | From what levels of directories to start from. -mindepth 1 means skip the starting point                       |

Search in the starting point and one level down

<pre>
find / -maxdepth 2 -name
</pre>

Do not search in the starting point and one level down. Start from sub-directory level 2

<pre>
find / -mindepth 2 -name
</pre>

Search between sub-directory level 1 and 2.

<pre>
find / -mindepth 1 -maxdepth 2 -name
</pre>

## Type

-type

| Option | Description                    |
| ------ | ------------------------------ |
| f      | regular file                   |
| d      | directory                      |
| l      | symbolic link                  |
| b      | block (buffered) special       |
| c      | character (unbuffered) special |
| p      | named pipe (FIFO)              |
| s      | socket                         |
| D      | door (Solaris)                 |

<pre>
$ find . -type f -name 'new*'
</pre>

## Size

-size

| Option | Description               |
| ------ | ------------------------- |
| b      | 512-byte blocks (default) |
| c      | bytes                     |
| w      | two-byte words            |
| k      | Kilobytes                 |
| M      | Megabytes                 |
| G      | Gigabytes                 |

Exactly 1024k

<pre>
find . -type f -size 1024k
</pre>

less than 1MB

<pre>
find . -type f -size -1M
</pre>

greater than 1Gb

<pre>
find . -type f -size +1G
</pre>

between 1Gb and 2Gb

<pre>
find . -type f -size +1G -size -2G
</pre>

## Permissions

-perm

search for files based on the file permissions

<pre>
find . -perm 777
</pre>

## Owner

-user

<pre>
find . -user ellie
</pre>

-group

<pre>
find . -group hr
</pre>

## Time

| Option       | Description                                                  |
| ------------ | ------------------------------------------------------------ |
| -amin n      | accessed n minutes ago.                                      |
| -anewer file | file was last accessed more recently than file was modified. |
| atime n      | last accessed n\*24 hours ago                                |
| -cmin n      | last changed n minutes ago                                   |
| -cnewer file | file was last changed more recently than file was modified.  |
| -ctime n     | last changed n\*24 hours ago                                 |
| -mmin n      | last modified n minutes ago.                                 |
| -mtime n     | last modified n\*24 hours ago.                               |

Possible arguments

<pre>
+n for greater than n
-n for less than n
n for exactly n
</pre>

Arguments Examples

<pre>
+7 = more than 7 days ago
2 = between 2 and 3 days ago
-2 = within the past 2 days
+1 = more than 1 day old
1 = between 1 and 2 days ago
-1 = within the past 1 day
0 = within the past 1 day
</pre>
