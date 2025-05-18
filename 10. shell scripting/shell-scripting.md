# shell scripting

It is used to Automate tasks, simplify workflows, and boost efficiency with Bash scripts

### What is Bash?

**Bash (Bourne Again SHell)** is the default command-line shell in most Linux distributions.

Shell scripting involves writing **.sh files** that contain a sequence of shell commands.

**#!/bin/bash** is called the **shebang**, which tells the system to execute the script with Bash. (it's a interpreter)

## Script with Arguments

1. create  `vi welcome.sh`

2. add content as
   `#!/bin/bash
echo "Hello $1, welcome to $2!"
`
3. give permission to execute or run with bash

   `chmod +x welcome.sh`

4. run

   `./welcome.sh Alice DevOps`

   **output:**

   Hello Alice, welcome to Devops!


## Script with Variables

```
#!/bin/bash
name="Alice"
echo "Welcome, $name!"
```
 **output:** welcome, Alice!

**note**: You define variables without = spaces. Use $varname to access them

## Conditionals (if, else, elif)


Basic if block

```
#!/bin/bash
num=10

if [ $num -gt 5 ]; then
    echo "Greater than 5"
else
    echo "5 or less"
fi
```

### operators

| Expression | Meaning           |
| ---------- | ----------------- |
| `-eq`      | Equal             |
| `-ne`      | Not equal         |
| `-gt`      | Greater than      |
| `-lt`      | Less than         |
| `-ge`      | Greater or equal  |
| `-le`      | Less or equal     |
| `==`       | String equality   |
| `!=`       | String inequality |


### Example: Check file existence
```
if [ -f "/etc/passwd" ]; then
    echo "File exists"
else
    echo "File not found"
fi
```

## for loop

```
for i in 1 2 3
do
  echo "Number $i"
done
```

**output:** 
Number 1

Number 2

Number 3

## while loop

```
count=1
while [ $count -le 5 ]
do
  echo "Count: $count"
  ((count++))
done
```

**output:**
Count: 1

Count: 2

Count: 3

Count: 4

Count: 5

## Loop through files:
```
for file in /var/log/*.log
do
  echo "Log File: $file"
done
```
**output:**
Log File: /var/log/alternatives.log

Log File: /var/log/auth.log

Log File: /var/log/bootstrap.log

Log File: /var/log/dpkg.log

Log File: /var/log/fontconfig.log

Log File: /var/log/kern.log

Log File: /var/log/ubuntu-advantage-apt-hook.log

## Case Statement (Like Switch)

```
#!/bin/bash
read -p "Enter a fruit: " fruit

case $fruit in
  apple) echo "Red fruit";;
  banana) echo "Yellow fruit";;
  *) echo "Unknown fruit";;
esac
```
**output:**

 `bash case.txt`
 
Enter a fruit: apple

Red fruit

ubuntu@LAPTOP-L592SHA5:~$ `bash case.txt`

Enter a fruit: cherry

Unknown fruit


## Returning Values

Bash functions **don’t return values** the way other languages do. You can return **exit codes (0–255) using return**, or pass values using **echo**.

### Defining the Function
```
sum() {
  result=$(( $1 + $2 ))
  echo $result
}
```

`sum()` → Defines a function named sum.

`$1 and $2` → Represent the first and second arguments passed to the function.

`$(( $1 + $2 ))` → Performs the addition of both arguments.

`echo $result` → Prints the result.

### Calling the Function & Storing Output

```
total=$(sum 5 10)
```
`sum 5 10` → Calls the function with arguments 5 and 10.

`$(sum 5 10)` → Captures the output of sum 5 10 and stores it in total.

### Printing the Final Result

```
echo "Total: $total"
```
Displays Total: 15, because 5 + 10 = 15.


### questions
Q: How do you return a value from a Bash function?

A: Use **echo** and capture it with **$( )**.

Q: What is the difference between source and ./script.sh?

A: source runs in the current shell, useful for exporting environment variables.

Q: What does trap do in a shell script?

A: Catches signals (like Ctrl+C) and handles them gracefully.
