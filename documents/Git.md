# Git

## Links

- [Git Home](https://git-scm.com)
- [git ignore](http://gitignore.io)

## Configuration

git config --global user.name "K. Kolb"  
git config --global user.email "kkolb@sit.de"  
git config --global core.editor "code --wait"

git config --list

## Initialization

git init

git clone copy remote files assoziated with the repository to local machine

## Basic commands

### Status

git status

### Add

git add file1 file2  
git add .

### Commit

git commit -m "commit message"  
git commit -a -m "commit message"
git commit --amend

### Log

git log  
git log --oneline

### Branching

git branch
git branch -v
git branch <branch-name>
git branch -m <new branch-name>

git switch <branch-name> change branch
git checkout <branch-name> change branch

git switch -c <branch-name> create branch and switch to it
git checkout -b <branch-name> create branch and switch to it
git checkout <commit-hash> checkout special commit, detached HEAD, re-attach by switching to a branch
git checkout HEAD~1 checkout previous commit (relative to current commit), refers to commit before HEAD
git checkout HEAD <file name> revert file to last commit
git checkout -- <file-name> revert file to last commit

git restore <file-name> revert file to last commit
git restore --source HEAD~1 <file-name> restore to commit prior to HEAD
git restore --staged <file-name> remove file from staging area, unstage it

git reset <commit-hash> removes the commits, not the changes
git reset -- hard <commit-hash> removes the commits AND the changes

git revert <commit-hash> makes new commit and undos the changes, the commit history is not changed

### Merging

- Fast-Forward
- Merge Commit

git switch master
git merge <branch-name>

### Diff

git diff
git diff HEAD
git diff --staged
git diff branch1..branch2 [filename]
git diff commit1..commit2 [filename]

### Stashing

git stash
git stash pop
git stash apply

git stash list

git stash apply stash@{2}
git stash drop stash@{2}
git stash clear

### Remotes

git remote  
git remote -v

git remote add origin

git push origin master

### Git alias

[alias]  
co = checkout  
br = branch  
com = commit  
st = status  
lg = log --graph --color --abbrev-commit --date=format:'%Y-%m-%d %H:%M' --pretty=format:'%Cred%h%Creset %Cgreen%ad%Creset %C(cyan)%<(10,trunc)%aN%Creset %C(yellow)%d%Creset %s %Cgreen(%cr)%Creset'

## Github

### Existing local Repo

- create new repo on Github
- connect local repo (add remote)
- push changes to Github

### No local Repo

- create repo on Github
- clone repo
- work in repo
- push changes to Github

### Bash commands

- cd
- ls
- pwd
- open . (MAC)
- start . (Windows)
- touch tmp.txt
- mkdir
- rm tmp.txt
- rm -rf folderToDelete
