# WaffenShell
my own linux terminal

Implementation

To install the readline library, open the terminal window and write

sudo apt-get install libreadline-dev
It will ask for your password. Enter it. Press y in the next step.

Printing the directory can be done using getcwd.
Getting user name can be done by getenv(“USER”)Parsing can be done by using strsep(“”).
It will separate words based on spaces.Always skip words with zero length to avoid storing of extra spaces.
After parsing, check the list of built-in commands, and if present, execute it.If not, 
execute it as a system command. To check for built-in commands, store the commands in an array of character pointers,
and compare all with strcmp().


Note: “cd” does not work natively using execvp, so it is a built-in command, executed with chdir().
For executing a system command, a new child will be created and then by using the execvp, execute the command,
and wait until it is finished.
Detecting pipes can also be done by using strsep(“|”).To handle pipes,
first separate the first part of the command from the second part.
Then after parsing each part, call both parts in two separate new children, 
using execvp. Piping means passing the output of first command as the input of second command.
