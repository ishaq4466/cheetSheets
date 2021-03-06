Table of conntent:
===================
1. [Git Archi.](#1git-basic-Archi.)
2. [Checkout](#2Checkout)
3. [Branching](#3branching)
4. [Reflogging](#4Reflogging)
5. [Stashing](#5Stashing)
6. [\*\*Merge and Conflict](#6Merge-And-Conflict)
7. [BFG](#7bfg)
8. [Cherry-Picking](#)
### 1.Git basic Archi.

![Git Architecture](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/11/Git-Architechture-Git-Tutorial-Edureka-2-768x720.png)
1. git status #showing all **modified and untracked** file in the repo

2. git add . # adding all files which are added and modified to the staging area

3. git commit -m "commit message"  # committing all the files into local repo from the staging area

4. git commit -am "Commit without adding to staging" # all the **modified files only** are commit without adding them to staging area

5. git log --oneline --decorate --color # showing all the logs in oneline with HEAD position 

6. git log -p -1 --color  	# shows the changes in files in the last commit

&. git config --list # getting all the configured username and password
### 2.Checkout 

1. git checkout

* showing all the modified file names in the **working directory**
* Also it shows all the modified and added files in the **staging area** 

2. git diff --color <filename>   # showing all the **changes done to a file**


### 3.Branching

1. git checkout -b new # creating and checking out new branch
2. git checkout -b new <sha-id> # creating a branch from **commit id**
3. git branch 			# showing the branch
4. git branch -r 		# **showing all remote branches** -a all for branches
5. git branch -D branch_name # deleting a local repo branch
6. git branch 
7. git push origin --delete dev # deleting a remote branch from local 

### [4.Reflogging](https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog)

* Git keeps track of updates to the tip of branches using a mechanism called reference logs, or "reflogs."
* Reflogs track when Git refs were updated in the local repository. 
* In addition to branch tip reflogs, a special reflog is maintained for the **Git stash**.
* Reflogs are stored in directories under the local repository's .git directory.
* git reflog directories can be found at .git/logs/refs/heads/., .git/logs/HEAD, and also .git/logs/refs/stash if the git stash has been used on the repo
* **git reflog** can be used for **Redoing after undo** like if we hard reset 

### [5.Stashing](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#stashing-your-work)

* git stash temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on
* Stashing is handy if you need to quickly switch context and work on something else, 
  but you're mid-way through a code change and aren't quite ready to commit.
* Note that the stash is local to your Git repository; stashes are not transferred to the server when you push.
* Also remember, by default Git won't stash **changes made to untracked or ignored files.**

1. git stash save or git stash save -u or git stash save -a //
2. git stash show

### [6.Merge And Conflict](https://www.git-tower.com/learn/git/faq/solve-merge-conflicts)

![Merge-conflict](merge-conflict.png)
![Merge-conflict-2](merge-conflict-2.png)
* Conflict suitations normally happens when the **same line/s of same the filename** has been modified by two diff. users(dev)eloper) co-incidently
* By Merging these changes, we are knowing the "single source of truth" for that piece of code or file by eithering discarding "our" changes or "thier" changes.
* Sorting out the merge-conflict condition
```
 git status # will show the conflicting file name to be merged 
 git checkout --ours <file-name> # keeping our changes and discarding the other 
 git checkout --theirs <file-name> # keeping the other changes and discarding our change 
 git commit -am "Conflict resolved" # After resolving the confilct ,merging it by commiting
```

### [7.BFG](https://github.com/IBM/BluePic/wiki/Using-BFG-Repo-Cleaner-tool-to-remove-sensitive-files-from-your-git-repo)

* Sometimes we might added some large files or some sensitive files to our git repo and pushed it to the remote repo.
* Though we can remove that file and put the entry in the .gitignore file for such file extension. But still we might find that file in our git commit history on the Remote Repo. 
* In order to remove that file permenantly from the repo commit history, we can either make use of 
**git filter-branch** or a super cool repo cleaner tool called **"BFG"** 

### Resetting/Rolling-back the changes (Playing with HEAD Pointer)

* Revert back the modified files/file to their original state or to **last commit state** in Working Directory 
```
git checkout . or git checkout <filename>
```
* Reverting the files from staging area to **working directoty or last commit**
```
git reset HEAD 
```

* Reverting the file changes "between two commits"
Some times it might happen we want to revert back the changes to the previous commit or to a specific commit state.
The below image illust the scenerio:  
![Revert](revert.png)

```
git log -p -2 FILE1.txt # see the changes done in file1.txt in last 2 commits and getting the hash value for the desired
git revert <SHA2>
git checkout --their FILE1.txt #solving the merge and conflict
git commit -m "Chnges reverted w.r.t last commit"
git push origin 
```

### [8.Cherry-picking](https://www.devroom.io/2010/06/10/cherry-picking-specific-commits-from-another-branch/)

* Cherry-picking is one of the most powerfull feature of git which **allows one to only pick certain commits
from other branch and merge it with the corresponding desired branch**

* Cherry-picking allows us to only merge the specific file changes in two different branches, leaving the other files unchanged in other branch.











