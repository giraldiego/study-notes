https://hamwaves.com/collaboration/doc/rypress.com/index.html

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

# Branches I

`git branch`  

List all branches.  

`git branch <branch-name>`  

Create a new branch using the current working directory as its base.  

`git checkout <branch-name>`  

Make the working directory and the HEAD match the specified branch.  

`git merge <branch-name>`  

Merge a branch into the checked-out branch.  

`git branch -d <branch-name>`  

Delete a branch.  

`git rm <file>`

Remove a file from the working directory (if applicable) and stop tracking  
the file.

# Branches II

`git commit -a -m "<message>"`

Stage all tracked files and commit the snapshot using the specified message.

`git branch -D <branch-name>`

Force the removal of an unmerged branch (_be careful_: it will be lost forever).

# Rebasing

`git rebase <new-base>`

Move the current branch’s commits to the tip of `<new-base>`, which can be either a branch name or a commit ID.

`git rebase -i <new-base>`

Perform an interactive rebase and select actions for each commit.

`git commit --amend`

Add staged changes to the most recent commit instead of creating a new one.

`git rebase --continue`

Continue a rebase after amending a commit.

`git rebase --abort`

Abandon the current interactive rebase and return the repository to its former state.

`git merge --no-ff <branch-name>`

Force a merge commit even if Git could do a fast-forward merge.