# Exercises

Short file of exercises and solution base on `missing-sysmeter` course.

## Shell Exercise

this exercises will be around shell, bash scripting.

### Exercise 1:

read man ls and write an ls command that lists files in the following manner

* includes all files, including hidden files
* sizes are listed in human readable format (e.g. 454M instead of 454279954)
* files are ordered by recency
* output is colorized

```bash
ls -Alht --color=auto
```
### Exercise 2

write bash function `marco` and `polo`.
* `marco` == current working directory is saved
* `polo` == `cd` to directory where you executed `marco`

To use the function you must reload them on the shell.
```bash
source ./marco.sh
```

#### `marco.sh` file

```bash
marco(){
marcoPwd="$(pwd)"
}

polo(){
cd "$marcoPwd"
}
```
### Exercise 3

You have a command that fails rarely.

```bash

 #!/usr/bin/env bash

 n=$(( RANDOM % 100 ))

 if [[ n -eq 42 ]]; then
    echo "Something went wrong"
    >&2 echo "The error was using magic numbers"
    exit 1
 fi

 echo "Everything went according to plan"

```
You must log std,error stream and report how many runs it took for the script to fail.

```bash

#!/usr/bin/env bash
>error.log #clear log
>std.log
while :; do
	($1) 1>> std.log 2>>error.log
	if [[ $? -ne 0 ]]; then
		less ./std.log | wc -l
		break
	fi
done
```

note: streaming to the same file you must use\
` command1 >> log_file 2>&1 `
### Exercise 4

Write a task the recursively find all mark-down files in the folder and makes a zip with them.

:note use `tar -tvf archive.tar` too check what inside

```bash
find -name '*.md' | xargs tar -cf archive.tar -v
```
### Exercise 9

use `|` nad `>` to write the "last modified" date

```bash
./semster | grep last-m > last-modified.txt
```
## Data Wrangling Exercise

Here is a data of multi graph and exercise on him.

### Data
100 101
100 101
100 102
100 103
100 103
100 103
100 103
100 104
101 100
102 100

### Exercise

Transfer from multi graph to weighted graph

```bash
 awk '$1 > $2 { print $2,  $1 ; next } {print $1, $2}' data.out |
 sort |
uniq -c |
awk '{print $2, $3, $1}'
```
# Exercise

## exercise 2

teaching about the log and how to watch history

### 2.1

Explore the version history

```bash
log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(bold blue)<%an>%Creset' --abbrev-commit
```
### 2.2

Who last modified 'README.md`

```bash
log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(bold blue)<%an>%Creset' --abbrev-commit 'README.md`
```

### 2.3

info:
`git blame` == show what revision and author last modified each line of a file.\
`git show` == show one or more objects (blobs, tress, tags and commits).

what was the commit message associated with the last modification to 'collections:' line of '_config.yml'

```bash
git blame _config.yml |grep collections: | sed 's/\s.*//' |git show
```

## Exercise 3

sensitive information may end up on repository how to delete it ?

remove from history a file

```bash
git filter-branch --force --index-filter "git rm --cached --ignore-unmatch _config.yml --prune-empty --tag-name-filter cat -- --all
```
