# Git Commands: Beginner to Advanced

## Beginner Level

### 1. git init
Initializes a new Git repository.

```sh
git init
2. git clone
Clones an existing repository.


git clone [repository_url]
3. git status
Displays the state of the working directory and the staging area.

git status
4. git add
Adds changes to the staging area.


git add [file_name]
To add all changes:


git add .
5. git commit
Records changes to the repository.


git commit -m "Commit message"
6. git log
Shows the commit history.


git log
7. git branch
Lists, creates, or deletes branches.

List branches:


git branch
Create a new branch:


git branch [branch_name]
8. git checkout
Switches branches or restores working tree files.

Switch branches:


git checkout [branch_name]
Create and switch to a new branch:


git checkout -b [new_branch_name]
9. git merge
Merges changes from one branch into another.


git merge [branch_name]
10. git remote
Manages set of tracked repositories.

Add a remote repository:


git remote add [remote_name] [repository_url]
Intermediate Level
1. git pull
Fetches from and integrates with another repository or a local branch.


git pull [remote] [branch]
2. git push
Updates remote refs along with associated objects.


git push [remote] [branch]
3. git fetch
Downloads objects and refs from another repository.


git fetch [remote]
4. git rebase
Reapplies commits on top of another base tip.


git rebase [branch]
5. git stash
Stashes changes in a dirty working directory away.

Save changes:


git stash
Apply stashed changes:


git stash apply
6. git tag
Creates, lists, deletes, or verifies a tag object signed with GPG.

Create a new tag:

git tag [tag_name]
Push tags to remote:


git push [remote] [tag_name]
7. git diff
Shows changes between commits, commit and working tree, etc.


git diff
8. git reset
Resets current HEAD to the specified state.


git reset [commit]
9. git rm
Removes files from the working tree and from the index.


git rm [file_name]
10. git mv
Moves or renames a file, a directory, or a symlink.


git mv [old_name] [new_name]
Advanced Level
1. git cherry-pick
Apply the changes introduced by some existing commits.


git cherry-pick [commit]
2. git bisect
Use binary search to find the commit that introduced a bug.

Start bisecting:


git bisect start
Mark the current commit as bad:


git bisect bad
Mark the current commit as good:


git bisect good
3. git blame
Show what revision and author last modified each line of a file.


git blame [file_name]
4. git reflog
Manage the information recorded in the reflogs.

git reflog
5. git submodule
Initialize, update, or inspect submodules.

Add a new submodule:


git submodule add [repository_url]
Initialize submodules:


git submodule init
Update submodules:


git submodule update
6. git archive
Create an archive of files from a named tree.


git archive -o [archive_name.tar] HEAD
7. git filter-branch
Rewrite branches.


git filter-branch --tree-filter '[command]' HEAD
8. git gc
Optimize the repository.


git gc
9. git fsck
Verifies the connectivity and validity of the objects in the database.


git fsck
10. git worktree
Manage multiple working trees.

Add a new working tree:


git worktree add [path] [branch]
