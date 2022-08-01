## Stage 0

This is a crib for git commands. Based on Coursera free git course. 
[Week 1](https://www.coursera.org/learn/introduction-git-github/home/week/1)

### First Steps with Git conspect 

* **Working tree** - working directory where git was inited
* **Stage area (index)** - file that contains all information and changes of a file, that will going to next commit

* `git init` - init repository on the current directory
* `git config -l` - check config
* `git config --global user.email "my@e.mail"` - save user's email to global config
* `git config --global user.name "username"` - save username email to global config
* `git clone path_to_repo` - clone existing repository
* `git add path_to_file` - add file to staging area. This means that git for now will track file 
	and all changes was made to file 
* `git status` - information about working tree and changes 
* `git dcommit` - save changes to VCS. Massage it is a commentary about what changes for 
	and other information that commit author whant to be stored
* `git log` - show git commit history

### Tracking files

Tracked files can be in three states:
* **Modefied** - changes that we made to a file is not commited yet. 
	This changes would not stored until we commited em
* **Staged** - all changes are ready to be commited to the project. 
	All part of current stage will be in next commit ("snapshot") that we will take 
* **Commited** - all changes was made to file are become a pert of "snapshot" we made

Commit message should be a short description of the change (up to 50 characters), 
	followed by one or more paragraphs giving more details of the change (if needed).

## Learn Git Branching conspect

### Branches

* `git branch branch_name` - create new branch
* `git checkout branch_name` - switch to branch_name
* `git checkout -b branch_name` - create new branch and switch to it
* `git branch` - list of existing branches
* `git merge branch_name` - merge branch_name with current brunch
* `git rebase branch_name` - move all commits from current branch to branch_name
* `git branch -f branch_to_move hash_to_move` - move and reattach branch_to_move to commit with hash_to_move

HEAD - is a link to current working commit. 

* `git checkout commit_hash` - for moving head to exact commit
* `git checkout main^` - move HEAD to to commit right before last on the main branch. 
	Same for HEAD - HEAD^ or HEAD^^^ etc.
* `git chechout HEAD~4` - move up for 4 commits of HEAD
* `git branch -f branch_to_move HEAD~3` - move branch_to_move to 3 commits before current HEAD

### Undo changes

* `git reset hash` - reset changes to hash on local repo
* `git revert hash` - make new commit hash' with undoned changes that was made for hash. Use for remote repo

### cherry-picking, interactive rebase

* `git cherry-pick hash1 hash2 ...` - copy changes from hash1, hash2 etc. after current HEAD as hash1', hash2' etc.
* `git rebase -i hash` - will open interactiv rebase editor for commits from hash to HEAD 
	for choosing needed commits
* `git commit --amend` - change last commit
* `git rebase hash1 hash2` - move commits from hash2 to hash1

### Tags

* `git tag tag_name hash` - attach tagname to hash
* `git describe CurrentHash` - show how long HEAD from nearest tag. Output be like nearestTag_howFarHeIs_gCurrentHash

### Remote repos

* `git clone URL` - clone remote repo to local
* `git fetch` - sync changes from remote repo to local 
* `git pull` - merge fetched repo. `git pull` works the same way as `git fetch; git merge origin/main`
* `git push` - opposite to pull. Upload all changes from local repo to remo
* `git branch -u origin/main foo` - track origin/main by branch foo
* `git push remote_repo_name branch_name` - push changes from local brunch branch_name to 
	remote_repo_name on branch_name
* `git push remote_repo_name local_branch:remote_branch` - push changes from local branch_name from 
	local_branch on remote_repo_name

