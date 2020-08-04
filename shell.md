# Shell

Shell is textual interface.\
bash == Bourne Again SHEll.

Note: shell parse the arugment by white space.\
optinal Solution:

* single quates == inhabit all interptation of sequence of char  ` 'my photo' ` 
* double quates == surpress  ` "my photo" ` 
* escape charcter == remove special meaning `my\ photo ` 

In case you are stuck use man or --help/-h flag (on windows `/?`). 

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

## Stream
Redirecting IO.

* \> == write to file
* \>> == append to file
* < == read from file
* | == pipe (chain command outputs to diffrent command)

note: | > < operations are done by shell In case of sudo use
`echo 3 | sudo tee brightness`
tee program for writing
