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
git status

## Basic commands

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

git switch <branch-name>
git checkout <branch-name>

git switch -c <branch-name>
git checkout -b <branch-name>

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

### Git alias

[alias]  
co = checkout  
br = branch  
com = commit  
st = status  
lg = log --graph --color --abbrev-commit --date=format:'%Y-%m-%d %H:%M' --pretty=format:'%Cred%h%Creset %Cgreen%ad%Creset %C(cyan)%<(10,trunc)%aN%Creset %C(yellow)%d%Creset %s %Cgreen(%cr)%Creset'

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
