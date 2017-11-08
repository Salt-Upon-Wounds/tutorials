# Bash Scripting

## The first line of our Bash Script
```
#!/bin/bash
# A sample Bash script, by Dzianis
```
* `#!/bin/bash` - This is the first line of the script above. The hash exclamation mark ( `#!` ) character sequence is referred to as the Shebang.
* `#...` - Anything after `#` is not executed. It is for our reference only.

## Variables

__A variable is a temporary store for a piece of information.__

The variable `$1` represents the 1st command line argument.
The variable `$2` represents the 2nd command line argument and so on.

These are automatically set by the system when we run our script so all we need to do is refer to them.

* `$1, $2, ...` - The first, second, etc command line arguments to the script.
* `variable=value` - To set a value for a variable. Remember, no spaces on either side of `=`.
* Quotes `"..."` and `'...'` - Double will do variable substitution, single will not.
* `variable=$( command )` - Save the output of a command into a variable.
* `export var1` - Make the variable var1 available to child processes.
* `echo $myvariable $anothervar` - To check the variables have been set as intended.
* `echo` (with no arguments) - This is a good way to get a blank line on the screen. 

__Special Variables__

* `$0` - The name of the Bash script.
* `$1 - $9` - The first 9 arguments to the Bash script (as mentioned above).
* `$#` - How many arguments were passed to the Bash script.
* `$@` - All the arguments supplied to the Bash script.
* `$?` - The exit status of the most recently run process.
* `$$` - The process ID of the current script.
* `$USER` - The username of the user running the script.
* `$HOSTNAME` - The hostname of the machine the script is running on.
* `$SECONDS` - The number of seconds since the script was started.
* `$RANDOM` - Returns a different random number each time is it referred to.
* `$LINENO` - Returns the current line number in the Bash script.

## User Input

* `read varName` - Read input from the user and store it in the variable `varName`.

## Arithmetic

* `let expression` - Make a variable equal to an expression.
* `expr expression` - print out the result of the expression.
* `$(( expression ))` - Return the result of the expression.
* `${#var}` - Return the length of the variable var.

## Operators

* `! EXPRESSION` - The EXPRESSION is false.
* `-n STRING` - The length of STRING is greater than zero.
* `-z STRING` - The lengh of STRING is zero (ie it is empty).
* `STRING1 = STRING2` - STRING1 is equal to STRING2.
* `STRING1 != STRING2` - STRING1 is not equal to STRING2.
* `INTEGER1 -eq INTEGER2` - INTEGER1 is numerically equal to INTEGER2.
* `INTEGER1 -gt INTEGER2` - INTEGER1 is numerically greater than INTEGER2.
* `INTEGER1 -lt INTEGER2` - INTEGER1 is numerically less than INTEGER2.
* `-d FILE` - FILE exists and is a directory.
* `-e FILE` - FILE exists.
* `-r FILE` - FILE exists and the read permission is granted.
* `-s FILE` - FILE exists and it's size is greater than zero (ie. it is not empty).
* `-w FILE` - FILE exists and the write permission is granted.
* `-x FILE` - FILE exists and the execute permission is granted.

__Boolean__
* `&&` - Perform the and operation.
* `||` - Perform the or operation.
* `if [ -r $1 ] && [ -s $1 ]` - If the file is readable and has a size greater than zero.
* `if [ $USER == 'bob' ] || [ $USER == 'andy' ]` - If the user is either bob or andy. 

## If Statements

__Basic__

```
if [ <some test> ]
then
    <commands>
fi
```

__Nested__

```
if [ <some test> ]
then
    <commands>
        if (( <some test> ))
        then
            <other commands>
        fi
fi
```

__If Else__

```
if [ <some test> ]
then
    <commands>
else
    <other commands>
fi
```

__If Elif Else__
```
if [ <some test> ]
then
   <commands>
elif [ <some test> ] 
then
   <different commands>
else
   <other commands>
fi
```

## Case Statements
```
case <variable> in
<pattern 1>)
    <commands>
    ;;
<pattern 2>)
    <different commands>
    ;;
*)
    <other commands>
    ;;
esac
```

## While

Perform a set of commands while a test is true.

```
while [ <some test> ]
do
    <commands>
done
```

## Until

Perform a set of commands until a test is true.

```
until [ <some test> ]
do
    <commands>
done
```

## For

Perform a set of commands for each item in a list.

```
for var in <list>
do
    <commands>
done
```

## Ranges
```
# Basic range in for loop
for value in {1..5}
do
    echo $value
done
```

```
# Basic range with steps for loop
for value in {10..0..2}
do
    echo $value
done
```

## Break and Continue

__Break__

Exit the currently running loop.

The `break` statement tells Bash to leave the loop straight away.

__Continue__

Stop this iteration of the loop and begin the next iteration.

The `continue` statement tells Bash to stop running through this iteration of the loop and begin the next iteration.

## Select

Display a simple menu system for selecting items from a list.

```
select var in <list>
do
    <commands>
done
```

## Functions

Functions in Bash Scripting are a great way to reuse code.

```
function_name () {
    <commands>
}
```

or

``` 
function function_name {
    <commands>
}
```

__Passing Arguments__

Within the function they are accessible as `$1`, `$2`, etc.

```
#!/bin/bash

# Passing arguments to a function
print_something () {
    echo Hello $1
}

# Setting a return status for a function
print_something () {
    echo Hello $1
    return 5
}

print_something Mars
print_something Jupiter
echo The previous function has a return value of $?

```

* `$?` - Contains the return status of the previously run command or function.
* `local <name>=<value>` - Create a local variable within a function.

__Overriding Commands__

```
#!/bin/bash
# Create a wrapper around the command ls

ls () {
    command ls -lh
}

ls
```