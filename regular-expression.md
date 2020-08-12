# Regular Expression

Languages for matching pattern of string

```
/ pattern / flag
```
[regular expression online debugger](https://regex101.com)\
[doc for regular expression in vim](https://www.regular-expressions.info/refflavors.html)

note: regular expression by default is greedy (non-greedy `.\{-}`)
which mean, _continue from the first match pattern forward_

## flag:

* `/./g` == global
* `/./c` == case sensitive ignore

## counting selector 

Special combination that has the effect to decide the amount 

* `/c+/g` == c appears once or more
* `/c?/g` == c appears 1 or less
* `/*/g` == c appears 0 or more
* `/c{4}/g` == c appears exact 4 times
* `/c{4,}/g` = c appears 4 or more w

## wild card

Special character that fit for a group of characters

* `/./g` == everything except white spaces 
* `/\\./g` == escape expanded character
* `/\\w/g` == any word
* `/\\W/g` == any not word
* `/\\s/g` == white space
* `/\\S/g` == not white space

## range

Declare the options of combination

* `/[fc]/g` == f or c
* `/[a-c]/g` == a or b or c (same for [a-z,A-Z,0-9])

## group

choose a part of pattern (have the abilities to change only him) 

* `/(t|T)/g` == t or T\
 note: in case off t|The will be or between t or The
(r|e){2,3} == r or e combination 2 to 3 time


* `/^/g` == match the beginning statement
 note: default flag setting are is set per chunk of text and not multi line
this why must add '/.../g**m**'
* `/$/g` == end of line

## special groups

Example for text:
>"All we have to decide is what to do with the time that is given us"

* `/(?<=to )\w*/g` == Positive lookbehind, find _decide_ in (vim version \zs)
* `/(?<!have) to d\w*/g` == negative look behind, find all but _to do_  
* `/\w*(?= to) /g` == Positive lookahead, find _have_ in  (vim version \ze)
* `/(?! world)/g` == Negative Lookahead  **world**

## naming group

mainly for easier replace 

* `/(?<name>\\d{3})/g` == named group

## non capture

when a group you set you on want to capture

* `/(?:\\d{3})/g` == not capture group

when replacing each capture group can be mention by
* `/$1/g` == capture group 1 (vim \1)
* `/$&/g` == all groups (vim \0)
