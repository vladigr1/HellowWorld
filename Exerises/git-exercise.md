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

what was the commit message associataed with the last modifacation to 'collections:' line of '_config.yml'

```bash
git blame _config.yml |grep collections: | sed 's/\s.*//' |git show
```

## Exercise 3

sensitive information may end up on repository how to delete it ?

remove from history a file

```bash
git filter-branch --force --index-filter "git rm --cached --ignore-unmatch _config.yml --prune-empty --tag-name-filter cat -- --all
```
