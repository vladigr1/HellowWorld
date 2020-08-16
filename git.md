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

All objects are content-addressed by their SHA-1 hash
```python
objects = map<string, object>

def store(object):
    id = sha1(object)
    objects[id] = object

def load(id):
    return objects[id]
```

git cat-file -p 698281bc680d1995c5f4caaf3359721a5a58d48d` == Provide content, type,and size for repositroy objects 

# git command-line interfcae

[git book](https://git-scm.com/book/en/v2)

### git save credential
* `git config --global credential.helper store` == remmber the user name and password after the first time 

## git basic

Like must things the basic is to find help

* `git help <command>` == git help
* `git status` == tells what going on

The basic is branches are sepretation of code control and the idea is joining the code.\
Merging is one of joining the code way, it create a special commit that has two uniqu parents.\
Rebase is the other way, it takes the branch you work currently and 'push' it to other branch.

Rebase example
```
<pre>
o <-- o <-- o <-- o <---- <strong>o</strong>
            ^            
             \          
              --- x <-- x
</pre>
```
---

```
<pre>
o <-- o <-- o <-- o <---- <strong>o</strong> <-- x <-- x
</pre>
```

interactive rebase using UI like vim to:

1. reorder commits
2. drop commits

`git rebase -i HEAD~4`

### setting the user
* `git config --global user.name`
* `git config --get user.name`
* `git config --list`

### setting Repository

* `git init`
* `git remote add origin https://github.com/user/repo.git`
* `git remote -v`
* `git remote remove origin`
* `git add -A` == adding all to staging directory
* `git add -p` == choose what to add
* `git reset calc.py` == remove file from staging area
* `git commit -m "commit message"`
* `git push -u origin calc-divide` == push the branch to the origin next time use git push git pull to it

### cloning a remote repo
* `git clone`
* `git remote add <shortname> <url>` == origin is default remote
* `git remote -v` == the info repository
* `git remote show origin`
* `git branch -a` == list branches localy and remotly
* `git pull origin master` == pulling from origin all updates
* `git push origin master`

### gitignore:
* `touch .gitignore` == create the files for ignore
.gitignore:
*.pyc == ignore all file ___.pyc

### branch: common work flow which work on single fitter on one branch
* `git branch --merged` == filter which branch your not merged yet
* `git branch` == show the current branch you are working on
* `git fetch origin` == getting all new changes from origin in case you have the branch you can work with pull
* `git pull origin lior` == update existed branch
* `git branch substract` == create branch
* `git chechkout calc-divide`
* `git checkout calc-divide`

### git mergetool
###  try vimdiff
* `git merge --abort`
* `git merge --continue`
* `git add animal.py`
* `git commit -m merge`

### Undoing commit

* `git commit --amend` == make additional change to current commit 

### delete master commit
* `git checkout master`
* `git reset --hard 5d83f9e`

### delete files 
* `git rm a.txt`
* `rm a.txt`

### delete changes
* `git checkout <file>`

### delete modifires of staging
* `git reset HEAD a.txt` == if you add -A and didnt wanted to add this file
* `git checkout -- a.txt` == reverse the file back how it was dangoures
 
### delete branch
* `git branch -d clac-divide` == delete local 
* `git push origin --delete calc-divide`

### tag = constant branch

### log
* `git log `
* `git diff` == show changes that didnt added
* `git log --all --graph --decorate --oneline`

## remote
git remote rpoistories have a lot of great properties:

* great backup
* make the code social.

* `git clone https://github.com/vladigr1/vladigr1.git`

Remote branches has this naming convention

```
<remote name>/<branch name>
```

* `git fetch` == download missing commit from branch and update our remote branches
* `git init --bare` == make folder as remote
* `git remote add origin ../remote`

### git push <remote> <localbranch>:<remote branch>
* `git push -u origin master:master` == set upstream
* `git branch ---set-upstream-to=origin/master`
* `git push`
* `git fetch <remote>` == only one talk with origin
* `git pull == git fetch; git merge
* `git pull --rebase` == git fetch; git rebase C3

Remote rejecter the push of commits directly to master because of the plicy on master requiring pull requests to instead be used. 

## moving around in git

* `HEAD` == is the symbolc name for the currently checked out commit.
* `git checkout branch` == move to latest commit of the branch.
* `git checkout _hash_` == move to hash commit

<pre>
		git checkout C1;
`git commit` == git checkout master;
	        git commit;	
		git checkout C2;
</pre>

## Relative Refs

Relative refs are memorable refs.

* `git log` == show hased of commit tree (can neter shor hash)
* `git checkout master^` == checkout master parent
* `git checkout HEAD^`
* `git checkout HEAD~2 == checkout grand parent of 'HEAD'
* `git branch -f master master^` == move to parent branche by force

note: HEA can only move by checkout (cant move by force).

Reverse changes in git has: (changes are for branch you are on)
1. low-level component (stagin individual files or chunks)
2. hiigh level component (how the changes are actually revesed) 

* `git reset HEAD^` == move the branch backwards as if the commit had never been made in the first place.
* `git revert HEAD` == commit that `reset` back (patch in the remote the intire team get the revert)


`git cherry-pick C2 C4` == way to copy a series of commits below your current location (`HEAD`)

## cool stuff

* `git stash`
* `git bisect` == unit test break test all before
* `gitconfig` == search in internet

## daily routine:

1. `git branch substract `
2. `git checkout substract`
#### modify substract
3. `git status` == check changes
4. `git add -A`
5. `git commit -m "substract"`
#### git pull origin master
6. `git push -u origin substract`
#### test substract
7. `git pull origin master`
8. `git merge master`
9. `git checkout master`
10. `git merge substract`
11. `git push origin master`
