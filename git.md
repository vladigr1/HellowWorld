* progit
:PROPERTIES:
:NOTER_DOCUMENT: ../../Google Drive/College-Material/self-git/progit.pdf
:END:
** Basic
*** clean
=git clean -fd= delete all untraced files (not staged)
*** Restore
pick single file to your branch
=git restore --source=mybranch --toc.txt=
*** Commit
=git commit -am "message"= add all modified
*** remove file
=rm file.txt= remove using unix command
=git add file2.txt= delete from staging
*** git ingore
some files you dont want to share in the repoistory
the add file named =.gitignore=
this file single in the root direcotrt of the repistory
_note_: only works if didnt include file in repoistory
        to solve it remove from "stagin area" by
        =git rm --cached -r bin/= remove inter bin direcotrty
** Branching
:PROPERTIES:
:NOTER_PAGE: 70
:END:
diverge form the main line of development

=git log --oneline= see from the this branch
=git log --oneline --all= see from the all branch
=git diff master..mybranch= comapre
=git diff mybranch= ccompare current branch with `branch`
*** Switch
:PROPERTIES:
:NOTER_PAGE: 77
:END:
=git switch mybranch= switch to an existing branch
=git siwtch -C mybranch= create and switch
*** Stashing
:PROPERTIES:
:NOTER_PAGE: 240
:END:
switching brnaches will _delete_ change you made on the branch if you didnt commited.
Stashing is saving changed
=git stash push -m "message"= stash changed in the branch
_note_: new untracked files are not defaulty add to the stash
for that we use:
=git stash push -am "messeage"= add all(include untracted) to stash to a new stash
=git stash list= show stashes
=git stash show stash@{1}= =git stash show 1= show what changes the stash will make
=git stash apply 1= apply change to current directory
=git stash drop 1= removing stash
=git stash clear= delete all stashes
*** Merging
=git merege --abort= cancel merge stage
:PROPERTIES:
:NOTER_PAGE: 70
:END:
**** fast-forward merger
in case if their is linear changes merging will be the same as changing the name.

=git merge --no-ff mybranch= all change bring to master without fast-forword merge
_note_:this `--no-ff` will show the old branch in the log rather the using fast-forward that will make it _linear_.
You will 'fill' it when `revrte` the git:
- fast-forword: reverting will be in the linear way
- no-ff: you will branch out
**** 3-way merge
branches were divorce git deside how to merge
=git log --online --all --graph= better log for working with merges
**** Viewing Branches
=git branch --merges= show all merged branches (can be deleted)
=git branch -d mybranch= delete branch
=git branch --no-merged= show list branches that doesnt merged
**** Conflicts
conflict occur when in the same file you:
- change in two branches
- change and delete in two branches
- added in two branches
 3 party app
**** Squash merging
merging branches but it this time destory the commit in the brnach you we see it only brnach
=git merge --squash mybranch= squash merging
**** Rebase
"move the branch to master like add it in top"
=git rebase master= rebasing the branch with master
_note_: not contributer safe (only for solo project)
_note_: you do rebase from the feartere branch!

in case of cnflict
=git rebase --continue= in case of conflict apears again
=git rebase --skip= skip commit we are on it
=git rebase --abort= abort from current place
**** Cherrypick
pick a log and copy to current branch
=git cherry-pick 5670ecc= cherry pick this log

** logs
tips:
- never log praticular file.
** Remotes
:PROPERTIES:
:NOTER_PAGE: 56
:END:
when want to work ditrubuted
*** Centric workflow
when everyone work alone but their center server that all upload ther.
the advantage is no centric server failure.
The steps in this workflow:
- cloning
- commit
- push
- pull
- resolve conflict
*** Integration manager
only the mainter has push access.
The steps in this workflow:
- fork
- clone
- commit
- push
- pull request to the maintiner
mainter may:
  - pull or repoistory
  - review and fork our repoistory
*** Github
**** add contributer
setting -> send invitation->manage access
**** clone
git clone myrepoistory
**** orgin/master
is tarcking branch
*** remote repository
not in current working direcotry(server)
=git remote=  show remote repoistory
=git remote -v= info about remote
*** fetch
when the remote updated `fetching` is download the new update.
After that you will have new commits for you to update your local repisotry you must merge with `orgin/master`
work flow:
=git fetch= download from remote defaulty (from origin)
=git branch -vv= info status between `local` and `remote`
=git merge origin/master= update the `master` pointer to `origin/master`
*** pull
download remote change to what `remote/master` currenly has.
=git pull= branch the work and pull
=git pull --rebase= change the base master to `origin/master` <-
*** push
=git push= update `remote`
=git push -f= chnage to you exact local status
_note_: not recommanded to force push beacuse you destory colborator work.
*** Save git password
**** windows
something base
git config --global cardiental.helper ...
*** tags
=git push origin v1.0= add tag to your remoter
=git push origin --delete v1.0= add tag to your remoter
=git tag -d v1.0= delete tag from local repoistory
*** version
hand to hand fiter to tag using github
*** Remote branches
=git switch -C mybranch= create switch to branch
=git brnach -r= see remote branches
=git push -u origin title/mybranch= pus the branch upstream this branch to `origin` remote.
_note_: upstream means "create branch in remote"
=git push -d origin title/mybranch= delete the branch from remote
_note_: delete only remote
for delete in you local repository:
- =git switch diffrentbranch=
- =git branch -d title/mybranch= delete in local
*** Workflow example
...changes mad in reimote repoistory
=git fetch=
=git branch -r= checking remote
=git switch -C mybranch origin/feature/mybranch= create the remote repistory in my local repo

... changes made by colebrator
=git pull=
=git switch master=
=git merge feature/mybranch= join the feature with main line
=git push=
=git push -d origin feature/mybranch=

delete old remote branch
=git branch -r=
=git remote prune origin= delete remote branches that arent on local system
delete remote brancehs the the remote dont have (saved in our local but deleted)
*** Pull request
work flow is:
create branch ..
make feature ..
=git add .=
=git commit -m "messeage"=
=git push -u orgin feature/master=

- github and create pull request
- reviewer add team leader to review my change in the branch
- from the website you can see review and continue fix if need in your local repoisotory

  Reviewr will:
- when adding a reviewer the reviewr will get from github review request (top part in pull request tab).
- press review changes
- open an changes the change will request check view if all right (press view)
- pull request should close or reviewr or pull requset open
- and delete branch

  in case of conflicts:
- when you eneter github you will see a button to pull request your last commit
- when you etner you may see 'x' because thier is a conflict for this pull request
  _note_: merge masater not branches
*** Issues
  a fiter in github that like form of issues:W

**** label
issue calsifer
**** Milstones
are goals that you suppose to acommplish in issues tab
*** Fork
when conterubting to `Ingergation manager` workflow, you must:
- fork - generete my own repository
- add -> commit -> push
- pull request
**** Update your Fork repoistory
we update our local repoistory for updating the forked
we add remote of the original repository
=git remote add upstream https:..= add remote
_note_: `upstream` is common name for the main repoistory
=git remote rm upstream= remove remote
_note_: better to merge from the branch not to master because it easyer for mainter to check pull request
** History
=git reset HEAD~1 --hard=
in git we say:
- working directory: our file directory
- staging area: when you use `git add` it added staging
- commit: version of directory

  bad histoory:
  - poor commit
  - large commit
  - small commit

tools
- squash: make commit of fixes to feature
- split:
- reword: chnage naming
- drop:
- modify:
  _note_: dont modify public history because it will make B* git cant push will reject the commit.
*** Reset
=git reset --soft HEAD~1=
**** Soft
staging and working not change
just move HEAD to HEAD~1
**** mixed
place to staging and move HEAD
**** hard
change working dir staging, and HEAD
**** Revert
=git revert -m 1 HEAD= move head to look like perrent

=git revert HEAD~1= will create new commit do all change
= git
**** reflog
when a commit doesnt point to any branch it deletes from the log.
In this case for restoring this commit we need to che the reflog
=git reflog=
=git reflog show bugfix= show history for the branch bugfix
=git reset --hard HEAD@{1}= restore for this reflog
**** amend
adding to the last commit
=git commit --amend=

**** git rebase
Edit history.
=git rebase -i HEAD~3=
In can you want to do something in commit you must edit the parent commit.
- p, pick <commit> = use commit
- r, reword <commit> = use commit, but edit the commit message
- e, edit <commit> = use commit, but stop for amending
- s, squash <commit> = use commit, but meld into previous commit
- f, fixup <commit> = like "squash", but discard this commit's log message
- x, exec <command> = run command (the rest of the line) using shell
- b, break = stop here (continue rebase later with 'git rebase --continue')
- d, drop <commit> = remove commit
- l, label <label> = label current HEAD with a name
- t, reset <label> = reset HEAD to a label
- m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
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

# progit
:PROPERTIES:
:NOTER_DOCUMENT: ../../Google Drive/College-Material/self-git/progit.pdf
:END:
## Basic
### clean
* git clean -fd= delete all untraced files (not staged)
### Restore
pick single file to your branch
* git restore --source=mybranch --toc.txt=
### Commit
* git commit -am "message"= add all modified
### remove file
* rm file.txt= remove using unix command
* git add file2.txt= delete from staging
### git ingore
some files you dont want to share in the repoistory
the add file named =.gitignore=
this file single in the root direcotrt of the repistory
_note_: only works if didnt include file in repoistory
        to solve it remove from "stagin area" by
        =git rm --cached -r bin/= remove inter bin direcotrty
## Branching
:PROPERTIES:
:NOTER_PAGE: 70
:END:
diverge form the main line of development

* git log --oneline= see from the this branch
* git log --oneline --all= see from the all branch
* git diff master..mybranch= comapre
* git diff mybranch= ccompare current branch with `branch`
### Switch
:PROPERTIES:
:NOTER_PAGE: 77
:END:
* git switch mybranch= switch to an existing branch
* git siwtch -C mybranch= create and switch
### Stashing
:PROPERTIES:
:NOTER_PAGE: 240
:END:
switching brnaches will _delete_ change you made on the branch if you didnt commited.
Stashing is saving changed
* git stash push -m "message"= stash changed in the branch
_note_: new untracked files are not defaulty add to the stash
for that we use:
* git stash push -am "messeage"= add all(include untracted) to stash to a new stash
* git stash list= show stashes
* git stash show stash@{1}= =git stash show 1= show what changes the stash will make
* git stash apply 1= apply change to current directory
* git stash drop 1= removing stash
* git stash clear= delete all stashes
### Merging
* git merege --abort= cancel merge stage
:PROPERTIES:
:NOTER_PAGE: 70
:END:
#### fast-forward merger
in case if their is linear changes merging will be the same as changing the name.

* git merge --no-ff mybranch= all change bring to master without fast-forword merge
_note_:this `--no-ff` will show the old branch in the log rather the using fast-forward that will make it _linear_.
You will 'fill' it when `revrte` the git:
- fast-forword: reverting will be in the linear way
- no-ff: you will branch out
#### 3-way merge
branches were divorce git deside how to merge
* git log --online --all --graph= better log for working with merges
#### Viewing Branches
* git branch --merges= show all merged branches (can be deleted)
* git branch -d mybranch= delete branch
* git branch --no-merged= show list branches that doesnt merged
#### Conflicts
conflict occur when in the same file you:
- change in two branches
- change and delete in two branches
- added in two branches
 3 party app
#### Squash merging
merging branches but it this time destory the commit in the brnach you we see it only brnach
* git merge --squash mybranch= squash merging
#### Rebase
"move the branch to master like add it in top"
* git rebase master= rebasing the branch with master
_note_: not contributer safe (only for solo project)
_note_: you do rebase from the feartere branch!

in case of cnflict
* git rebase --continue= in case of conflict apears again
* git rebase --skip= skip commit we are on it
* git rebase --abort= abort from current place
#### Cherrypick
pick a log and copy to current branch
* git cherry-pick 5670ecc= cherry pick this log

## logs
tips:
- never log praticular file.
## Remotes
:PROPERTIES:
:NOTER_PAGE: 56
:END:
when want to work ditrubuted
### Centric workflow
when everyone work alone but their center server that all upload ther.
the advantage is no centric server failure.
The steps in this workflow:
- cloning
- commit
- push
- pull
- resolve conflict
### Integration manager
only the mainter has push access.
The steps in this workflow:
- fork
- clone
- commit
- push
- pull request to the maintiner
mainter may:
  - pull or repoistory
  - review and fork our repoistory
### Github
#### add contributer
setting -> send invitation->manage access
#### clone
git clone myrepoistory
#### orgin/master
is tarcking branch
### remote repository
not in current working direcotry(server)
* git remote=  show remote repoistory
* git remote -v= info about remote
### fetch
when the remote updated `fetching` is download the new update.
After that you will have new commits for you to update your local repisotry you must merge with `orgin/master`
work flow:
* git fetch= download from remote defaulty (from origin)
* git branch -vv= info status between `local` and `remote`
* git merge origin/master= update the `master` pointer to `origin/master`
### pull
download remote change to what `remote/master` currenly has.
* git pull= branch the work and pull
* git pull --rebase= change the base master to `origin/master` <-
### push
* git push= update `remote`
* git push -f= chnage to you exact local status
_note_: not recommanded to force push beacuse you destory colborator work.
### Save git password
#### windows
something base
git config --global cardiental.helper ...
### tags
* git push origin v1.0= add tag to your remoter
* git push origin --delete v1.0= add tag to your remoter
* git tag -d v1.0= delete tag from local repoistory
### version
hand to hand fiter to tag using github
### Remote branches
* git switch -C mybranch= create switch to branch
* git brnach -r= see remote branches
* git push -u origin title/mybranch= pus the branch upstream this branch to `origin` remote.
_note_: upstream means "create branch in remote"
* git push -d origin title/mybranch= delete the branch from remote
_note_: delete only remote
for delete in you local repository:
- =git switch diffrentbranch=
- =git branch -d title/mybranch= delete in local
### Workflow example
...changes mad in reimote repoistory
* git fetch=
* git branch -r= checking remote
* git switch -C mybranch origin/feature/mybranch= create the remote repistory in my local repo

... changes made by colebrator
* git pull=
* git switch master=
* git merge feature/mybranch= join the feature with main line
* git push=
* git push -d origin feature/mybranch=

delete old remote branch
* git branch -r=
* git remote prune origin= delete remote branches that arent on local system
delete remote brancehs the the remote dont have (saved in our local but deleted)
### Pull request
work flow is:
create branch ..
make feature ..
* git add .=
* git commit -m "messeage"=
* git push -u orgin feature/master=

- github and create pull request
- reviewer add team leader to review my change in the branch
- from the website you can see review and continue fix if need in your local repoisotory

  Reviewr will:
- when adding a reviewer the reviewr will get from github review request (top part in pull request tab).
- press review changes
- open an changes the change will request check view if all right (press view)
- pull request should close or reviewr or pull requset open
- and delete branch

  in case of conflicts:
- when you eneter github you will see a button to pull request your last commit
- when you etner you may see 'x' because thier is a conflict for this pull request
  _note_: merge masater not branches
### Issues
  a fiter in github that like form of issues:W

#### label
issue calsifer
#### Milstones
are goals that you suppose to acommplish in issues tab
### Fork
when conterubting to `Ingergation manager` workflow, you must:
- fork - generete my own repository
- add -> commit -> push
- pull request
#### Update your Fork repoistory
we update our local repoistory for updating the forked
we add remote of the original repository
* git remote add upstream https:..= add remote
_note_: `upstream` is common name for the main repoistory
* git remote rm upstream= remove remote
_note_: better to merge from the branch not to master because it easyer for mainter to check pull request
## History
* git reset HEAD~1 --hard=
in git we say:
- working directory: our file directory
- staging area: when you use `git add` it added staging
- commit: version of directory

  bad histoory:
  - poor commit
  - large commit
  - small commit

tools
- squash: make commit of fixes to feature
- split:
- reword: chnage naming
- drop:
- modify:
  _note_: dont modify public history because it will make B# git cant push will reject the commit.
### Reset
* git reset --soft HEAD~1=
#### Soft
staging and working not change
just move HEAD to HEAD~1
#### mixed
place to staging and move HEAD
#### hard
change working dir staging, and HEAD
#### Revert
* git revert -m 1 HEAD= move head to look like perrent

* git revert HEAD~1= will create new commit do all change
*  git
#### reflog
when a commit doesnt point to any branch it deletes from the log.
In this case for restoring this commit we need to che the reflog
* git reflog=
* git reflog show bugfix= show history for the branch bugfix
* git reset --hard HEAD@{1}= restore for this reflog
#### amend
adding to the last commit
* git commit --amend=

#### git rebase
Edit history.
* git rebase -i HEAD~3=
In can you want to do something in commit you must edit the parent commit.
- p, pick <commit> = use commit
- r, reword <commit> = use commit, but edit the commit message
- e, edit <commit> = use commit, but stop for amending
- s, squash <commit> = use commit, but meld into previous commit
- f, fixup <commit> = like "squash", but discard this commit's log message
- x, exec <command> = run command (the rest of the line) using shell
- b, break = stop here (continue rebase later with 'git rebase --continue')
- d, drop <commit> = remove commit
- l, label <label> = label current HEAD with a name
- t, reset <label> = reset HEAD to a label
- m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]

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

### restore a file from old commit

* `git checkout 0a24 -- VimGuide.txt`

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

**Relative refs are memorable refs.**

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

## Restore
new `git reset`

* `git restore --staged` == put local/head to your staged dir.
* `git restore` == put local/head to your working directory.
* `git restore --source=HEAD~1 file` == restore file from previous version

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
