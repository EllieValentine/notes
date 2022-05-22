# How to degug Bash scripts

## Execute code step by step

Add a line after #!/bin/bash

```
#!/bin/bash

trap 'echo "# $BASH_COMMAND";read' DEBUG

add your code

```

When you run your script, you will be able to see the part of the code that is about to be executed (marked with #). You need to hit ENTER to proceed or Ctrl+C to exit

Script Example

```
#!/bin/bash

trap 'echo "# $BASH_COMMAND";read' DEBUG

a=1
b=2
c=$(($a+$b))
echo $c

i=1
while [ $i -le 3 ]
do
        echo "Current iteration is $i"
              i=$(($i+1))
              echo $i
        done

echo Done

```

Output

```
# a=1

# b=2

# c=$(($a+$b))

# echo $c

3
# i=1

# [ $i -le 3 ]

# echo "Current iteration is $i"

Current iteration is 1
# i=$(($i+1))

# echo $i

2
# [ $i -le 3 ]

# echo "Current iteration is $i"

Current iteration is 2
# i=$(($i+1))

# echo $i

3
# [ $i -le 3 ]

# echo "Current iteration is $i"

Current iteration is 3
# i=$(($i+1))

# echo $i

4
# [ $i -le 3 ]

# echo Done

Done
```
