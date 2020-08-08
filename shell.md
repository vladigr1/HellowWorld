# Shell

Shell is textual interface.\
bash == Bourne Again SHEll.

Note: shell parse the arugment by white space.\
optinal Solution:

* single quates == inhabit all interptation of sequence of char  ` 'my photo' ` 
* double quates == surpress  ` "my photo" ` 
* escape charcter == remove special meaning `my\ photo ` 

In case you are stuck use man or --help/-h flag (on windows `/?`).\
note: **itldr** man page with examples

Start a command with a leading space it wont be added to your shell history.

## Job control 

`jobs` command that list the unfinshed jobs associated with the curren terminal session. 

`fg` place a job into the foreground shall 
`bg` place a job into the background jobs
`&` suffix in a command that will make the command run in the background

Signals are message pro process that interrupt the process.

* SIGINT , when typing `ctrl-c`
* SIGQUIT , when typing `ctrl-\\`
* SIGTERM , generic signal for asking a process to exit gracefully (`kill -TERM <PID>`)
* SIGTSTP , `ctrl-z`
* SIGKILL , terminate imdiatly not recommanded may leave orphaned children processes.

Example in python

```python

#!/usr/bin/env python
import signal, time

def handler(signum, time):
    print("\nI got a SIGINT, but I am not stopping")

signal.signal(signal.SIGINT, handler)
i = 0
while True:
    time.sleep(.1)
    print("\r{}".format(i), end="")
    i += 1

```

## Shell environment

List of name-value pairs,
when executing a command that doesn't match to programming keywords,
it consults an environment variable called `$PATH`.

## Nevigating in the shell
The path is sperated by 
`/`
character.\
The path 
`/`
is the "root" of the file system.

* absolute path == 
`/...dir.../../`
* relative path ==
`./`

* pwd == current location
* cd /home == enter dir 'home'
* cd .. == go back to parent directory
* ls == list what live in a given directory\
* cp = copy
* mv = move
* mkdir = make dir

## Find files

```bash
# Find all directories named src
find . -name src -type d
# Find all directories named src (case insensitive)
find . -iname src -type d
# Find all python files that have a folder named test in their path
find . -path '*/test/*.py' -type f
# Find all files modified in the last day
find . -mtime -1
# Find all zip files with size in range 500k to 10M
find . -size +500k -size -10M -name '*.tar.gz'
# Delete all files with .tmp extension
find . -name '*.tmp' -exec rm {} \;
# Find all PNG files and convert them to JPG
find . -name '*.png' -exec convert {} {}.jpg \;
```

`fd` is simple,fast, and user-friendly alternative to `find`.

`locate` is alternative to find.

## Stream
Redirecting IO.

* \> == write to file
* \>> == append to file
* < == read from file
* | == pipe (chain command outputs to diffrent command)

note: | > < operations are done by shell In case of sudo use
`echo 3 | sudo tee brightness`
tee program for writing

## Shell scripting

### Variables

Same aspect to normal programming lanugages.

* `var=bar' == assign vairables in bash
* `$var` == access the value

note: `foo = bar` would not work because it is intrepreted as calling the foo program with armuments = and bar.

String is defined by `'$var'` or `"$var"`.\
The diffrence is that `''` only string but `""` check for variables too.

### Arguments

basic script will look like this:\
`name(){\
...\
}`\

the arugments are special variables (must use " " as mention before)

* `$0` == name of the script
* `$1` == first argument, script can contain 1-0 arugments
* `$@` == all the arugments
* `$#` == number of arguments
* `$?` == return code of prvious command
* `!!` == last command
*  note: in case of **missing premission** use ` sudo !!`.

### Short circuiting operators

```bash
false || echo "Oops, fail"
# Oops, fail

true || echo "Will not be printed"
#

true && echo "Things went well"
# Things went well

false && echo "Will not be printed"
#

true ; echo "This will always run"
# This will always run

false ; echo "This will always run"
# This will always run
```

### Commmand substituion

getting output as a command variable.

* `for file in $(ls)` == shell will first call ls and then iterate ove thos values.
* `diff <(ls foo) <(ls bar))` == shows diffrence between files in dirs.

### Condtions

use **[[]]** rather then **[]** (less mistakes)

* `[[ $? -ne 0 ]]` == check if last result not equal zero
* `[[ $? -ge 0 ]]` == greater equal
* `[[ -f regularfile]]` == chekc if exist and regular file

The structure of if statement
```bash
if [[ $? -ne 0 ]]; then
        echo "File $file does not have any foobar, adding one"
        echo "# foobar" >> "$file"
    fi
```

The structure of loop:
```bash
for file in "$@"; do
    grep foobar "$file" > /dev/null 2> /dev/null
done
```

### Wild card

* Whenever you want to perform some sort of wildcard matching, you can use `?` and `*` `to match one or any amount of characters respectively.\
  For instance, given files foo, foo1, foo2, foo10 and bar, the command rm foo? will delete foo1 and foo2 whereas rm foo* will delete all but bar.
* Curly braces {} - Whenever you have a common substring in a series of commands, you can use curly braces for bash to expand this automatically.\
  This comes in very handy when moving or converting files.
  ```bash
# Globbing techniques can also be combined
mv *{.py,.sh} folder
# Will move all *.py and *.sh files
```
