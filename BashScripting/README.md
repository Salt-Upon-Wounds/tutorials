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
* `$1 - $9` - The first 9 arguments to the Bash script. (As mentioned above.)
* `$#` - How many arguments were passed to the Bash script.
* `$@` - All the arguments supplied to the Bash script.
* `$?` - The exit status of the most recently run process.
* `$$` - The process ID of the current script.
* `$USER` - The username of the user running the script.
* `$HOSTNAME` - The hostname of the machine the script is running on.
* `$SECONDS` - The number of seconds since the script was started.
* `$RANDOM` - Returns a different random number each time is it referred to.
* `$LINENO` - Returns the current line number in the Bash script.