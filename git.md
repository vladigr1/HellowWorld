# Git

Standart VCS, tool that help maintain a history of change, and collaboration.

# Git's data model

in git teminology:

* _blob_ == file, bunch of bytes
* _tree_ == directory, maps names to blobs or trees
* _snapshot_ || _commit_ == state of of blob or tree in specific point in time
* _history_ == list of snapshots in time-order
* _object_ == blob || tree || commit
* _reference_ == human readble pointer to commits, mutable
* _branch_ == refenece that sotres the new Git commit hash
* _master_ == main product line branch
* _HEAD_ == current branch
* _Repositories_ == data objects and references for project
* _staging area_ == `git add`, adding current staging area ("temporary stage")

In Git, a history is directed acyclic graph(DAG) of snapshots.

```
o <-- o <-- o <-- o
            ^
             \
              --- o <-- o
```

newly merge commit look like this,

```
<pre>
o <-- o <-- o <-- o <---- <strong>o</strong>
            ^            /
             \          v
              --- o <-- o
</pre>
```
Commits in Git are immutable.
This doesn’t mean that mistakes can’t be corrected,
however; it’s just that “edits” to the commit history are actually creating entirely new commits,
and references are updated to point to the new ones.

All objects are content-adressed by their SHA-1 hash
```python
objects = map<string, object>

def store(object):
    id = sha1(object)
    objects[id] = object

def load(id):
    return objects[id]
```

git cat-file -p 698281bc680d1995c5f4caaf3359721a5a58d48d` == Provide content, type,and size for repositroy objects 

## git command-line interfcae

[git book](https://git-scm.com/book/en/v2)

### git save credential
`git config --global credential.helper store` == remmber the user name and password after the first time 

### git basic
`git help <command>` == git help
`git status` == tells what going on

### setting the user
`git config --global user.name`
`git config --get user.name`
`git config --list`

### setting Repository
`git init`
`git remote add origin https://github.com/user/repo.git`
`git remote -v`

`git remote remove origin`

`git add -A` == adding all to staging directory
`git add -p` == choose what to add
`git reset calc.py` == remove file from staging area

`git commit -m "commit message"`
`git push -u origin calc-divide` == push the branch to the origin next time use git push git pull to it

### cloning a remote repo
`git clone`
`git remote add <shortname> <url>` == origin is default remote
`git remote -v` == the info repository
`git remote show origin`
`git branch -a` == list branches localy and remotly
`git pull origin master` == pulling from origin all updates
`git push origin master`

### gitignore:
`touch .gitignore` == create the files for ignore
.gitignore:
*.pyc == ignore all file ___.pyc

### branch: common work flow which work on single fitter on one branch
`git branch --merged` == filter which branch your not merged yet
`git branch` == show the current branch you are working on
`git fetch origin` == getting all new changes from origin in case you have the branch you can work with pull
`git pull origin lior` == update existed branch
`git branch substract` == create branch
`git chechkout calc-divide`
`git checkout calc-divide`

### git mergetool
###  try vimdiff
`git merge --abort`
`git merge --continue`
`git add animal.py`
`git commit -m merge`

### delete master commit
`git checkout master`
`git reset --hard 5d83f9e`

### delete files 
`git rm a.txt`
`rm a.txt`

### delete changes
`git checkout <file>`

### delete modifires of staging
`git reset HEAD a.txt` == if you add -A and didnt wanted to add this file
`git checkout -- a.txt` == reverse the file back how it was dangoures
 
### delete branch
`git branch -d clac-divide` == delete local 
`git push origin --delete calc-divide`

### tag = constant branch

### log
`git log `
`git diff` == show changes that didnt added
`git log --all --graph --decorate --oneline`

### remote
`git init --bare` == make folder as remote
`git remote add origin ../remote`
### git push <remote> <localbranch>:<remote branch>
`git push -u origin master:master` == set upstream
`git branch ---set-upstream-to=origin/master`
`git push`
`git fetch <remote>` == only one talk with origin
`git pull == git fetch, git merge`

### gitconfig search in internet

### cool stuff
`git stash`
`git bisect` == unit test break test all before


### daily rutine:
`git branch substract `
`git checkout substract`
### modifiy substract
`git status` == check changes
`git add -A`
`git commit -m "substract"`
### git pull origin master
`git push -u origin substract`
### test substract
`git pull origin master`
`git merge substract`
`git push origin master`
