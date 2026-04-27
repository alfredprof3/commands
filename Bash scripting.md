# Shell/Bash scripting

1. Create the sh file

touch first.sh

2. Inside the file, add the shebang `#!` and type the command

#!/bin/bash
echo "My first script in bash"

3. Execute the script

bash first.sh

# Executing a Linux command

1. Declare a variable and print it with the `echo` command to ensure you do it great

#!/bin/bash
var=`pwd` # or another Linux command
echo "Your current working directory is -> $var"

> [!NOTE]
> Is important to type the command inside ˋ ˋ
