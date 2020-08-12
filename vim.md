# Vim - Editor

editor that more appropriate  for a programmer.\
for first time user try `vimtutor` great tutorial.

Vim is programmable (with Vimscript and other languages like Python).

## Modal editing 


Vim is a modal editor which means _it has different modes for inserting text_.\

* Normal == for movement and changing modes (by pressing esc from any other mode)
* Insert == for inserting text ( by pressing i or cl in normal mode)
* Replace == for replacing text ( by pressing ctrl-r)
* Visual 
 * Visual plain == for selecting character (by v)
 * Visual line == for selecting line (by shift-v )
 * Visual block == for selecting block (by ctrl-v )
* Command-line == for running a command (by :)

## Vim’s interface 

### moving the cursor
<pre>
 	 k	//up
//left	h l	//right 
	 j	//down
</pre>
ctrl-w-\<motion\> == move between windows\
ctrl-w-v == open window\
ctrl-w-s == open window to bottom \
ctrl-d == scroll window down\
ctrl-u == scroll window up\
ctrl-w_ == maximize current window\
ctrl-w= == make all equal size\

### commands
 d p r c g o O a A e\
//in Command-line mode (:) their is auto-completion tab or ctrl-d\

### write and quit
:q! == quit with out save\
:wq == save and quit\
:wq \<file\> == save into file and quit\
:ls -- show open buffers\
:!\<command\> == check written by :!ls\

### Basic Rule: operator-[number]-motion 

### motion
w == word\
b == back a word\
e == end word\
^ == start line\
$ == end line\
\<count\>-\<motion\>//count==number of time you want to do motion\

### deletion 
x == delete single char\
d\<motion\> == delete operator motion parameter\
d\<count\>\<motion\>\
dw == delete word (can be de if you don't want to delete the space)\
d$ == delete [cursor,end line]\
dd == delete whole line\
\<count\>-dd\
di) == delete inside group\
da) == delete all group \

### put replace change
//deleted line stored in a vim register.\
p == put\
r == replace char\
shift-r == Replace mode replace until pressed esc\
ce == correct word\
c-[number]-\<motion\>\
ci( == cut inside\
da) == delete all\
~ == flip the case of character\

### undo and redo
u == undo once\
U == undo whole line\
ctrl-shift-r == redo\

### location navigation search
\<line number\>-shift-g == go to line\
ctrl-shft-g == ruler by %\
\<num precentage\>% == go to %\
gg == go start\
shift-g == got bottom\
/ == search forward\
? == search backward\
// n to next found \
// shift-n to back found\
ctrl-o == go back to where you came\
ctrl-i == go forward to where you came\
% == jump from start end of group E.g (),[]\
:set ic == ignore case sensitivity (disable :set noise)\
:set hls is == highlighting matches (disable :nohlsearch)\
/\<pattern\>\c == ignore case sensitive only to this search\

### substitute command
:s/thee/the == first occurrence of "thee" in the line.\
:s/thee/the/g == Adding the g flag means to substitute globally in the line.\
:s/old/new/g == where #,# are the line numbers of the range\
 == of lines where the substitution is to be done.\
:%s/old/new/g == to change every occurrence in the whole file.\
:%s/old/new/gc == to find every occurrence in the whole file,\
 == with a prompt whether to substitute or not.\
:,$s/old/new/g == from current place to end search and replace\

### selecting text to write
v == view mode\
: == in view mode will typed :'\<,'\>\
:'\<,'\>w \<file name\> == write selected lines to the file\
\<operator\> == in view mode you can use d y c\
:r \<file name\> == retrieve file\
y == in view mode yank\
y-\<motion\>\