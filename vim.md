# Vim - Editor

editor that more appropriate  for a programmer.\
for first time user try `vimtutor` great tutorial.

Vim is programmable (with Vimscript and other languages like Python).

## Modal editing 


Vim is a modal editor which means _it has different modes for inserting text_.

* Normal == for movement and changing modes (by pressing esc from any other mode)
* Insert == for inserting text ( by pressing i or cl in normal mode)
* Replace == for replacing text ( by pressing r)
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
ctrl-w= == make all equal size
ctrl-w-o == only windows
:vert sf file == vert split with file
:20vs . == split current directory

## tabs - seperate windows collection
gt next tab
gT prev tab
:tabc == close tab
:tabe open tab
:tabo == close all other tabs

### commands
 d p r c g o O a A e\
//in Command-line mode (:) their is auto-completion tab or ctrl-d

`\v` == very magic better regex

### write and quit
:q! == quit with out save\
:wq == save and quit\
:wq \<file\> == save into file and quit\
:!\<command\> == check written by :!ls

### Basic Rule: operator-[number]-motion 

### motion
w == word\
b == back a word\
e == end word\
^ == start line\
$ == end line\
\<count\>-\<motion\>//count==number of time you want to do motion

### deletion 
x == delete single char\
d\<motion\> == delete operator motion parameter\
d\<count\>\<motion\>\
dw == delete word (can be de if you don't want to delete the space)\
d$ == delete [cursor,end line]\
dd == delete whole line\
\<count\>-dd\
di) == delete inside group\
da) == delete all group 

### put replace change

Deleting a line in vim will stored it for pasting.

p == put\
r == replace char\
shift-r == Replace mode replace until pressed esc\
ce == correct word\
c-[number]-\<motion\>\
ci( == cut inside\
cip == cut in paragraph\
da) == delete all\
gi == insert from your last place you insert in the file
### normal mode unique action

~ == flip the case of character\
J == join

### undo and redo
u == undo once\
U == undo whole line\
ctrl-r == redo

### location navigation search
\<line number\>-shift-g == go to line\
ctrl-g == ruler by %\
\<num precentage\>% == go to %\
gg == go start\
shift-g == got bottom\
/ == search forward\
f t == find next apearence of a charcter in current line(forword ; back ,)\
{ } == jump between paraghraph\
? == search backward\
\* \# == find word next or before\
// n to next found \
// shift-n to back found\
ctrl-o == go back to where you came\
ctrl-i == go forward to where you came\
% == jump from start end of group E.g (),[]\
:set ic == ignore case sensitivity (disable :set noise)\
:set hls is == highlighting matches (disable :nohlsearch)\
/\<pattern\>\c == ignore case sensitive only to this search

### auto-completion

**ctrl-n == start a word and look at file to autocomplete base on it**\
**ctrl-p == scroll upword in option**\
**ctrl-x-ctrl-f == autocomplite for a file in the system**


### substitute command

[vim documentation : pattern](http://vimdoc.sourceforge.net/htmldoc/pattern.html#perl-patterns)

:s/thee/the == first occurrence of "thee" in the line.\
:s/thee/the/g == Adding the g flag means to substitute globally in the line.\
:s/old/new/g == where #,# are the line numbers of the range\
 == of lines where the substitution is to be done.\
:%s/old/new/g == to change every occurrence in the whole file.\
:%s/old/new/gc == to find every occurrence in the whole file,\
 == with a prompt whether to substitute or not.\
:,$s/old/new/g == from current place to end search and replace\

[Making a list of numbers](https://vim.fandom.com/wiki/Making_a_list_of_numbers)\
:let i=1 | g/PATTERN/s//\='REPLACE_'.i/ | let i=i+1

### selecting text to write
v == view mode\
: == in view mode will typed :'\<,'\>\
:'\<,'\>w \<file name\> == write selected lines to the file\
\<operator\> == in view mode you can use d y c\
:r \<file name\> == retrieve file\
y == in view mode yank\
y-\<motion\>\
i-ctlr-r-: == paste last command\
:read file == paste file in current place of currsor

## Cool stuffs on vim

### file browser

:edit . == will open file browser\
help netrw-browse-maps == nevigation file browser

### copy past

y/p == as wirten before will yank and paste from buffer\
:read ./file == read a file and paste in current location in buffer 

### set screan placement

zz == center to middle screen\
zt == to top  screen\
zb == to buttom  screen\
ctrl-e == move sceen one to end\
ctrl-y = move screen on to up\

:e == edit the file from current work 
:find == better :e
:find \*x == "like fuzzy find" 
g; g, == go to your last change
gd == go definition (def func():)
gf == go file that cursor sends on

## buffer

:ls -- show open buffers\
:bn next buffer
**ctrl-6 == switch buffer**
:b file
:bd delet buffer
:3,4bd == delete buffr in runge
:bo 15sp +te == terminal buffer

**note**: args are argmunet when you open a file.
:arga {files}
:arg file = make a local arg copy via files
:args print args

## bookmarks of vim

m[a-zA-Z] == mark
\`[a-zA-Z]

### regex - uniq cases for vim 

It is writen poorly read from 'vim help @!'

*non-greedy*

	If a "-" appears immediately after the "{", then a shortest match\
	first algorithm is used (see example below).  In particular, "{-}" is\
	the same as "*" but uses the shortest match first algorithm.  BUT: A\
	match that starts earlier is preferred over a shorter match: "a\{-}b"\
	matches "aaab" in "xaaab".
<pre>
	Example			matches ~
	ab\{2,3}c		"abbc" or "abbbc"
	a\{5}			"aaaaa"
	ab\{2,}c		"abbc", "abbbc", "abbbbc", etc.
	ab\{,3}c		"ac", "abc", "abbc" or "abbbc"
	a[bc]\{3}d		"abbbd", "abbcd", "acbcd", "acccd", etc.
	a\(bc\)\{1,2}d		"abcd" or "abcbcd"
	a[bc]\{-}[cd]		"abc" in "abcd"
	a[bc]*[cd]		"abcd" in "abcd"
</pre>

\\@=

	Matches the preceding atom with zero width.
	Like "(?=pattern)" in Perl.
	Example			matches ~
	foo\\(bar\\)\\@=		"foo" in "foobar"
	foo\\(bar\\)\\@=foo	nothing
							*/zero-width*
	When using "\\@=" (or "^", "$", "\\<", "\\>") no characters are included
	in the match.  These items are only used to check if a match can be
	made.  This can be tricky, because a match with following items will
	be done in the same position.  **The last example above will not match
	"foobarfoo", because it tries match "foo" in the same position where
	"bar" matched.**

	Note that using "\\&" works the same as using "\\@=": "foo\\&.." is the
	same as "\\(foo\\)\\@=..".  But using "\\&" is easier, you don't need the
	braces.


\\@!

	Matches with zero width if the preceding atom does NOT match at the
	current position. |/zero-width|
	Like "(?!pattern)" in Perl.
<pre>
	Example			matches ~
	foo\\(bar\\)\\@!		any "foo" not followed by "bar"
	a.\\{-}p\\@!		"a", "ap", "app", "appp", etc. not immediately
				followed by a "p"
	if \\(\\(then\\)\\@!.\\)*$	"if " not followed by "then"
</pre>

	Using "\\@!" is tricky, because there are many places where a pattern
	does not match.  "a.*p\\@!" will match from an "a" to the end of the
	line, because ".*" can match all characters in the line and the "p"
	doesn't match at the end of the line.  "a.\\{-}p\\@!" will match any
	"a", "ap", "app", etc. that isn't followed by a "p", because the "."
	can match a "p" and "p\\@!" doesn't match after that.

	You can't use "\\@!" to look for a non-match before the matching
	position: "\\(foo\\)\\@!bar" will match "bar" in "foobar", because at the
	position where "bar" matches, "foo" does not match.  To avoid matching
	"foobar" you could use "\\(foo\\)\\@!...bar", but that doesn't match a
	bar at the start of a line.  Use "\\(foo\\)\\@<!bar".

<pre>
	Useful example: to find "foo" in a line that does not contain "bar":
		/^\\%(.*bar\\)\\@!.*\\zsfoo
	This pattern first checks that there is not a single position in the
	line where "bar" matches.  If ".*bar" matches somewhere the \\@! will
	reject the pattern.  When there is no match any "foo" will be found.
	The "\\zs" is to have the match start just before "foo".
</pre>

\\@<=

	Matches with zero width if the preceding atom matches just before what
	follows. |/zero-width|
	Like "(?<=pattern)" in Perl, but Vim allows non-fixed-width patterns.
	Example			matches ~
	\\(an\\_s\\+\\)\\@<=file	"file" after "an" and white space or an
				end-of-line
	For speed it's often much better to avoid this multi.  Try using "\\zs"
	instead |/\\zs|.  To match the same as the above example:
		an\\_s\\+\\zsfile
	At least set a limit for the look-behind, see below.

	"\\@<=" and "\\@<!" check for matches just before what follows.
	Theoretically these matches could start anywhere before this position.
	But to limit the time needed, only the line where what follows matches
	is searched, and one line before that (if there is one).  This should
	be sufficient to match most things and not be too slow.

	In the old regexp engine the part of the pattern after "\\@<=" and
	"\\@<!" are checked for a match first, thus things like "\\1" don't work
	to reference \\(\\) inside the preceding atom.  It does work the other
	way around:

<pre>
	Bad example			matches ~
	\\%#=1\\1\\@<=,\\([a-z]\\+\\)		",abc" in "abc,abc"

	However, the new regexp engine works differently, it is better to not
	rely on this behavior, do not use \\@<= if it can be avoided:
	Example				matches ~
	\\([a-z]\\+\\)\\zs,\\1		",abc" in "abc,abc"
</pre>

\\@\<!

	Matches with zero width if the preceding atom does NOT match just
	before what follows.  Thus this matches if there is no position in the
	current or previous line where the atom matches such that it ends just
	before what follows.  |/zero-width|
	Like "(?<!pattern)" in Perl, but Vim allows non-fixed-width patterns.
	The match with the preceding atom is made to end just before the match
	with what follows, thus an atom that ends in ".*" will work.
	Warning: This can be slow (because many positions need to be checked
	for a match).  Use a limit if you can, see below.

\\@>

	Matches the preceding atom like matching a whole pattern.
	Like "(?>pattern)" in Perl.
	Example		matches ~
	\\(a*\\)\\@>a	nothing (the "a*" takes all the "a"'s, there can't be
			another one following)

	This matches the preceding atom as if it was a pattern by itself.  If
	it doesn't match, there is no retry with shorter sub-matches or
	anything.  Observe this difference: "a*b" and "a*ab" both match
	"aaab", but in the second case the "a*" matches only the first two
	"a"s.  "\\(a*\\)\\@>ab" will not match "aaab", because the "a*" matches
	the "aaa" (as many "a"s as possible), thus the "ab" can't match.

### register

vim save some information and you may use them

* "" == unamed for deleter and yank\
* "0 == yank register\
* "1 == delete register

**note**: move for every delete register 1 to 9

register for your use from a-z

* "a == overwrites the "a register\
* "A appends to the "a register

* full-magic reigster == cant write to ther

* ". == the last insert like .

* :registers == show register info

* q a q = clear register a 

### count lines print

`:%s/^/\=printf('%-4d', line('.'))` == number the line and tab from start/

### Ctag
**think its plugin that jump between fileby def** == when i have linux should use it

### snipping

nnoremap ,html :-1read $HOME/.vim/.skeletion.html\<CR\>3jwf\>a

### foldmethod

using {{{ }}} for define fold will learn it later
* zc = fold 
* zc = open
* zr = reduce
* zR = un reduce

 Folds

* zo / zO 	Open
* zc / zC 	Close
* za / zA 	Toggle
* zv 	Open folds for this line
* zM 	Close all
* zR 	Open all
* zm 	Fold more (foldlevel += 1)
* zr 	Fold less (foldlevel -= 1)
* zx 	Update folds

## make

co,piling build in on vim

## Recording a macro

Each register is identified by a letter a to z.

To enter a macro, type:

q<letter><commands>q

To execute the macro <number> times (once by default), type:

<number>@<letter>

## vimdiff
 Navigating
* ]c 	Next difference
* [c 	Previous difference

 Editing

* do 	Diff Obtain!
* Pull the changes to the current file.
* dp 	Diff Put!
* Push the changes to the other file.
* :diffupdate 	Re-scan the files for differences.
* ZQ 	Quit without checking changes

