# The Basics

`git init`
Create a Git repository in the current folder.  

`git status`  
View the status of each file in a repository.  

`git add <file>`  
Stage a file for the next commit.  

`git commit`  
Commit the staged files with a descriptive message.  

`git log`  
View a repository’s commit history.  

`git config --global user.name "<name>"`  
Define the author name to be used in all repositories.  

`git config --global user.email <email>`  
Define the author email to be used in all repositories.

# Undoing Changes

`git checkout <commit-id>`  
View a previous commit.  

`git tag -a <tag-name> -m "<description>"`  
Create an annotated tag pointing to the most recent commit.  

`git revert <commit-id>`  
Undo the specified commit by applying a new commit.  

`git reset --hard`  
Reset tracked files to match the most recent commit.  

`git clean -f`  
Remove untracked files.  

`git reset --hard / git clean -f`  
Permanently undo uncommitted changes.

