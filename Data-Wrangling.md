# Data Wrangling

Do some Transformation to the data.

## Online requests

Let request the log in 'myserver'
```bash
ssh myserver journalctl
```
filtering on the remote sever and then use `less` us a "pager".

```bash
ssh myserver 'journalctl | grep sshd | grep "Disconnected from"' | less
```

## sed

`sed` is a 'stream editor`.\
Their are tons of commands, but one of the most common ones,
* `s` == substitution

The format of `sed` argument are

```
\`s/REGEX/SUBSTITUTION/\`
```

note: Same Syntax for 'Search and Replace' of `vim`.

note: for easier syntax 'extend regular expressions'
```bash
sed -E s/.../.../
```

## awk

`awk` is a 'another editor'.\
`awk` programs take the form of an optional pattern plus a block saying what to do if the pattern matches a give line.\
The default pattern matches all lines.
Inside the block, `$0` is set the entire line's contents.
The `$1` though `$n` are set to the n'th field of the line, when separated by the `awk` field separator (whitespace by default, change with `-F`?)

Let's compute the number of single use usernames that start with 'c' and end with 'e':

```bash
| awk '$1 == 1 && $2 ~ /^c[^ ]*e$/ { print $2 }' | wc -l
```

* `$1 == 1` == first field should be equal to 1 
* `$2 ~ /^c[^ ]\*e$/` == second field should match the given regular expression 
* `{ print $2 }` == print the second field

However, `awk` is a programming language, remember?

```awk
BEGIN { rows = 0 }
$1 == 1 && $2 ~ /^c[^ ]*e$/ { rows += $1 }
END { print rows }
```

### more to know

* `{print $2, $1}` == separate between the column by the separator
* `next` == similar to continue in c

Good example similar to if else

```bash
awk '$1 > $2 { print $2,  $1 ; next } {print $1, $2}' data.out
```

### code with awk

`BEGIN` is a pattern that matches the start of the input (and `END`
matches the end). Now, the per-line block just adds the count from the
first field (although it'll always be 1 in this case), and then we print
it out at the end. In fact, we _could_ get rid of `grep` and `sed`
entirely, because `awk` [can do it
all](https://backreference.org/2010/02/10/idiomatic-awk/), but we'll
leave that as an exercise to the reader.

## Common tools

* `sort` == sort in lexicographic the input
* `sort -n` == sort in numeric
* `sort -k1,1` == sort by only the first whitespace-separated column
* `uniq -c` == collapse consecutive lines that are the same into a single line, prefixed with a count of the number of occurrences
* `tail -n10` == display only the 10 last lines
* `head -n10` == display only the 10 first lines

## Wrangling binary data

So far, we have mostly talked about wrangling textual data, but pipes
are just as useful for binary data. For example, we can use ffmpeg to
capture an image from our camera, convert it to grayscale, compress it,
send it to a remote machine over SSH, decompress it there, make a copy,
and then display it.

```bash
ffmpeg -loglevel panic -i /dev/video0 -frames 1 -f image2 -
 | convert - -colorspace gray -
 | gzip
 | ssh mymachine 'gzip -d | tee copy.jpg | env DISPLAY=:0 feh -'
```
