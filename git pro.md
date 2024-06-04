
# Getting Started - About Version Control

## Introduction

This chapter covers the basics of version control, explains how to install Git, and guides you through the initial setup.

## About Version Control

### What is Version Control?

Version control is a system that records changes to files over time, allowing you to recall specific versions later. It's essential for software development and useful for other fields like graphic design.

### Benefits of Version Control

- Revert files or projects to previous states
- Compare changes over time
- Identify who last modified a file
- Recover lost or corrupted files
- Low overhead with high benefits

## Types of Version Control Systems

### Local Version Control Systems

- **Method:** Copying files into another directory
- **Tool Example:** RCS (Revision Control System)
- **How it Works:** Keeps patch sets to recreate file states
- **Limitations:** Error-prone and simple

### Centralized Version Control Systems (CVCS)

- **Method:** Single server stores all versioned files
- **Tool Examples:** CVS, Subversion, Perforce
- **Benefits:** 
  - Centralized knowledge of changes
  - Fine-grained control over access
- **Drawbacks:**
  - Single point of failure
  - Risk of total data loss if the server fails

### Distributed Version Control Systems (DVCS)

- **Method:** Each client mirrors the entire repository
- **Tool Examples:** Git, Mercurial, Darcs
- **Benefits:**
  - Full backups on every client
  - Resilient to server failures
  - Supports multiple workflows and collaborations
 
# What is Git?

## Overview
Git is a distributed version control system that simplifies managing changes to files and collaborating on projects. Understanding its core concepts will make using Git easier.

## Snapshots, Not Differences
Unlike other VCSs that store data as changes (deltas) to files, Git stores data as snapshots of the entire project at specific points in time. Each commit saves a snapshot, storing links to unchanged files to optimize space.

## Local Operations
Most Git operations are local, requiring no network access. This makes actions like viewing history or comparing versions fast and available offline. You can work and commit changes locally even without network access, unlike some other VCSs.

## Integrity
Git ensures data integrity by checksumming everything with SHA-1 hashes. Every file, commit, and repository state is referenced by a hash, making it impossible to alter data undetected.

## Data Persistence
Git primarily adds data, making it difficult to lose committed snapshots. Once you commit changes, they are safely stored and hard to delete accidentally, especially when regularly pushing to remote repositories.

## The Three States
Files in Git can be:
- **Modified:** Changed but not committed.
- **Staged:** Marked for inclusion in the next commit.
- **Committed:** Stored in the local database.

## Git Workflow
1. **Modify:** Change files in the working tree.
2. **Stage:** Add changes to the staging area.
3. **Commit:** Save changes from the staging area to the Git directory.

## Key Components
- **Working Tree:** Your local checkout of the project.
- **Staging Area:** Files marked for the next commit.
- **Git Directory:** Where metadata and object database are stored.

## Summary
- **Git uses snapshots:** Efficient storage by saving complete project states.
- **Local operations:** Fast, offline capabilities.
- **Data integrity:** Secure with SHA-1 checksums.
- **Persistence:** Difficult to lose committed data.
- **Three states:** Modified, staged, committed files.

# Installing Git

## Linux

### Package Manager Installation (Fedora)
```sh
$ sudo dnf install git-all
Package Manager Installation (Debian/Ubuntu)
sh
Copy code
$ sudo apt install git-all
For more options and distributions, visit the Git website.

macOS
Xcode Command Line Tools Installation
sh
Copy code
$ git --version
Binary Installer
Download from the Git website.

Windows
Official Git for Windows
Download from the Git website.

Chocolatey Package (Community maintained)
sh
Copy code
$ choco install git
Installing from Source
Dependencies Installation (Fedora)
sh
Copy code
$ sudo dnf install dh-autoreconf curl-devel expat-devel gettext-devel openssl-devel perl-devel zlib-devel
Dependencies Installation (Debian/Ubuntu)
sh
Copy code
$ sudo apt-get install dh-autoreconf libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
For additional documentation formats, install:

AsciiDoc, XMLto, DocBook2X (Fedora)
AsciiDoc, XMLto, DocBook2X, Install-info (Debian/Ubuntu)
Clone the Git repository:

sh
Copy code
$ git clone https://git.kernel.org/pub/scm/git/git.git
Compile and install from source:

sh
Copy code
$ tar -zxf git-2.8.0.tar.gz
$ cd git-2.8.0
$ make configure
$ ./configure --prefix=/usr
$ make all doc info
$ sudo make install install-doc install-html install-info


# First-Time Git Setup

## Configuration Locations

Git configuration variables can be stored in three places:
- System-wide: `/etc/gitconfig`
- User-specific: `~/.gitconfig` or `~/.config/git/config`
- Repository-specific: `.git/config`

Each level overrides values in the previous level.

## Viewing Configuration

To view all configuration settings and their origins:
```sh
$ git config --list --show-origin
Setting Your Identity
Set your user name and email address:

sh
Copy code
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
Configuring Your Editor
Set the default text editor:

sh
Copy code
$ git config --global core.editor emacs
On Windows, specify the full path:

sh
Copy code
$ git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
Setting Default Branch Name
Set the default branch name (from Git version 2.28):

sh
Copy code
$ git config --global init.defaultBranch main
Checking Settings
To check configuration settings:

sh
Copy code
$ git config --list
To check a specific setting:

sh
Copy code
$ git config user.name
To determine the origin of a setting:

sh
Copy code
$ git config --show-origin rerere.autoUpdate


# Getting Help

If you ever need assistance while using Git, there are several ways to get the help you need.

## Comprehensive Manual Page Help

You can access the comprehensive manual page (manpage) help for any Git command using one of the following commands:

```sh
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
For example, to get the manpage help for the git config command, you can run:

sh
Copy code
$ git help config
These commands are accessible anywhere, even offline.

IRC Channels for In-Person Help
If you require in-person help beyond the available documentation, you can join the following IRC channels on the Libera Chat server:

#git
#github
#gitlab
These channels are filled with hundreds of knowledgeable individuals who are often willing to assist with Git-related queries.

Quick Refresher on Command Options
If you only need a quick overview of the available options for a Git command, you can use the -h option. For example:

sh
Copy code
$ git add -h
This command provides a concise summary of the available options for the git add command.

```markdown
# Git Basics - Getting a Git Repository

Learn the essential Git commands to configure and initialize a repository, track files, and manage changes. By the end, you'll know how to set up a repository, stage and commit changes, undo mistakes, view project history, and work with remote repositories.

## Getting a Git Repository

You can either:
1. Initialize a new Git repository in an existing directory.
2. Clone an existing Git repository.

### Initializing a Repository

To start version control in an existing directory:

```sh
$ cd /path/to/your/project
$ git init
```

This creates a `.git` subdirectory. To track files and make an initial commit:

```sh
$ git add *.c LICENSE
$ git commit -m 'Initial project version'
```

### Cloning an Existing Repository

To clone a repository:

```sh
$ git clone <url>
```

Example:

```sh
$ git clone https://github.com/libgit2/libgit2
```

This creates a `libgit2` directory with the repository's data. To clone into a different directory name:

```sh
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

Git supports various protocols like `https://`, `git://`, and `ssh://`.
```

### Git Basics - Recording Changes to the Repository

#### Understanding Tracked and Untracked Files
In Git, files in your working directory can either be **tracked** or **untracked**:
- **Tracked Files**: These are files that Git is aware of because they were in the last snapshot (commit) or have been staged for the next commit. Tracked files can be in one of three states: unmodified, modified, or staged.
- **Untracked Files**: These are files that Git does not know about because they were not in the last snapshot and have not been staged.

#### Checking the Status of Your Files
To see which files are in which state, you use the `git status` command:
```sh
$ git status
```
Immediately after cloning a repository, all files should be tracked and unmodified.

#### Tracking New Files
To start tracking a new file, use `git add`:
```sh
$ git add README
```
Running `git status` again will show that the file is now tracked and staged for commit:
```sh
$ git status
```
Output will include:
```sh
Changes to be committed:
  new file:   README
```

#### Staging Modified Files
If you modify an already tracked file and want to stage these changes, use `git add`:
```sh
$ git add CONTRIBUTING.md
```
Before staging, `git status` will show:
```sh
Changes not staged for commit:
  modified:   CONTRIBUTING.md
```
After staging, `git status` will update:
```sh
Changes to be committed:
  modified:   CONTRIBUTING.md
```

#### Using Short Status
For a more compact view of your changes, use:
```sh
$ git status -s
```
This gives a simplified output showing the state of the staging area and the working directory.

#### Ignoring Files
To prevent certain files from being tracked, create a `.gitignore` file with patterns for the files you want to ignore:
```sh
$ cat .gitignore
*.log
*.tmp
```
You can specify rules for ignoring files using standard glob patterns.

#### Viewing Changes
To see the exact changes made but not yet staged, use:
```sh
$ git diff
```
To see changes that are staged for the next commit:
```sh
$ git diff --staged
```

#### Committing Your Changes
To commit staged changes, use:
```sh
$ git commit
```
This will open your default editor to enter a commit message. Alternatively, use the `-m` flag to include a message directly:
```sh
$ git commit -m "Commit message"
```

#### Skipping the Staging Area
To commit all tracked changes directly without staging them first, use:
```sh
$ git commit -a -m "Commit message"
```

#### Removing Files
To remove a file from the working directory and stop tracking it:
```sh
$ git rm FILE_NAME
```
To remove a file only from the staging area but keep it in the working directory:
```sh
$ git rm --cached FILE_NAME
```

#### Moving Files
To move or rename a file:
```sh
$ git mv OLD_NAME NEW_NAME
```
This is equivalent to manually moving the file, removing the old name, and adding the new name:
```sh
$ mv OLD_NAME NEW_NAME
$ git rm OLD_NAME
$ git add NEW_NAME
```

By following these steps and commands, you can effectively manage the state of your files within a Git repository, ensuring that your project is tracked accurately and efficiently.

### Git Basics - Viewing the Commit History

When working on a project, it's essential to understand the history of changes. Git provides powerful tools to view this history through the `git log` command.

#### Cloning the Example Repository
To follow along with the examples, you can clone a simple project repository:
```sh
$ git clone https://github.com/schacon/simplegit-progit
```

#### Basic `git log` Command
Running `git log` in your project directory gives you a list of commits:
```sh
$ git log
```
This will display:
- The commit's SHA-1 checksum
- Author's name and email
- Date of the commit
- Commit message

Example output:
```sh
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```

#### Useful `git log` Options

- **Show differences introduced by each commit (-p or --patch):**
    ```sh
    $ git log -p
    ```
- **Limit the number of commits displayed (-<n>):**
    ```sh
    $ git log -2
    ```
- **Show abbreviated stats (--stat):**
    ```sh
    $ git log --stat
    ```

#### Formatting Log Output

- **Predefined formats (oneline, short, full, fuller):**
    ```sh
    $ git log --pretty=oneline
    ```
- **Custom format with --pretty=format:**
    ```sh
    $ git log --pretty=format:"%h - %an, %ar : %s"
    ```

##### Useful Specifiers for Custom Formatting
| Specifier | Description                     |
|-----------|---------------------------------|
| %H        | Commit hash                     |
| %h        | Abbreviated commit hash         |
| %an       | Author name                     |
| %ae       | Author email                    |
| %ad       | Author date                     |
| %ar       | Author date, relative           |
| %s        | Subject                         |

- **Graphical representation of the commit history (--graph):**
    ```sh
    $ git log --pretty=format:"%h %s" --graph
    ```

#### Limiting Log Output

- **Show commits from a specific date range (--since, --until):**
    ```sh
    $ git log --since="2023-01-01" --until="2023-01-31"
    ```
- **Filter by author (--author):**
    ```sh
    $ git log --author="Scott Chacon"
    ```
- **Search commit messages (--grep):**
    ```sh
    $ git log --grep="bugfix"
    ```

##### Other Limiting Options
| Option      | Description                                      |
|-------------|--------------------------------------------------|
| -<n>        | Show only the last n commits                     |
| --since     | Limit commits to those made after the given date |
| --until     | Limit commits to those made before the given date|
| --committer | Filter by committer                              |
| -S          | Show commits that add or remove a string         |

- **Example combining multiple filters:**
    ```sh
    $ git log --author="Junio C Hamano" --since="2008-10-01" --until="2008-11-01" --no-merges -- t/
    ```

By leveraging these `git log` options and filters, you can tailor the commit history view to your specific needs, making it easier to understand and manage your project's evolution.


### Git Basics - Undoing Things

At any stage, you may want to undo something. Here, we’ll review a few basic tools for undoing changes that you’ve made. Be careful, because you can’t always undo some of these undos. This is one of the few areas in Git where you may lose some work if you do it wrong.

#### Amending a Commit

One common undo happens when you commit too early and possibly forget to add some files or mess up your commit message. If you want to redo that commit, make the additional changes you forgot, stage them, and commit again using the `--amend` option:

```sh
$ git commit --amend
```

This command takes your staging area and uses it for the commit. If you’ve made no changes since your last commit (for instance, you run this command immediately after your previous commit), then your snapshot will look exactly the same, and all you’ll change is your commit message.

As an example, if you commit and then realize you forgot to stage the changes in a file you wanted to add to this commit, you can do something like this:

```sh
$ git commit -m 'Initial commit'
$ git add forgotten_file
$ git commit --amend
```

You end up with a single commit—the second commit replaces the results of the first.

**Note**: When you amend your last commit, you’re effectively replacing it entirely with a new, improved commit that pushes the old commit out of the way and puts the new commit in its place. The previous commit won’t show up in your repository history.

The obvious value to amending commits is to make minor improvements to your last commit, without cluttering your repository history with commit messages of the form, “Oops, forgot to add a file” or “Darn, fixing a typo in last commit”.

**Important**: Only amend commits that are still local and have not been pushed somewhere. Amending previously pushed commits and force pushing the branch will cause problems for your collaborators.

#### Unstaging a Staged File

Let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type `git add *` and stage them both. How can you unstage one of the two? The `git status` command reminds you:

```sh
$ git add *
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
    modified:   CONTRIBUTING.md
```

Right below the “Changes to be committed” text, it says use `git reset HEAD <file>` to unstage. So, let’s use that advice to unstage the `CONTRIBUTING.md` file:

```sh
$ git reset HEAD CONTRIBUTING.md
Unstaged changes after reset:
M    CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

The command is a bit strange, but it works. The `CONTRIBUTING.md` file is modified but once again unstaged.

**Note**: It’s true that `git reset` can be a dangerous command, especially if you provide the `--hard` flag. However, in the scenario described above, the file in your working directory is not touched, so it’s relatively safe.

#### Unmodifying a Modified File

What if you realize that you don’t want to keep your changes to the `CONTRIBUTING.md` file? How can you easily unmodify it—revert it back to what it looked like when you last committed (or initially cloned, or however you got it into your working directory)? Luckily, `git status` tells you how to do that, too. In the last example output, the unstaged area looks like this:

```sh
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

It tells you pretty explicitly how to discard the changes you’ve made. Let’s do what it says:

```sh
$ git checkout -- CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
```

You can see that the changes have been reverted.

**Important**: It’s important to understand that `git checkout -- <file>` is a dangerous command. Any local changes you made to that file are gone—Git just replaced that file with the last staged or committed version. Don’t ever use this command unless you absolutely know that you don’t want those unsaved local changes.

If you would like to keep the changes you’ve made to that file but still need to get it out of the way for now, we’ll go over stashing and branching in Git Branching; these are generally better ways to go.

#### Undoing things with git restore

Git version 2.23.0 introduced a new command: `git restore`. It’s basically an alternative to `git reset`, which we just covered. From Git version 2.23.0 onwards, Git will use `git restore` instead of `git reset` for many undo operations.

#### Unstaging a Staged File with git restore

The next two sections demonstrate how to work with your staging area and working directory changes with `git restore`. The nice part is that the command you use to determine the state of those two areas also reminds you how to undo changes to them. For example, let’s say you’ve changed two files and want to commit them as two separate changes, but you accidentally type `git add *` and stage them both. How can you unstage one of the two? The `git status` command reminds you:

```sh
$ git add *
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
    modified:   CONTRIBUTING.md
    renamed:    README.md -> README
```

Right below the “Changes to be committed” text, it says use `git restore --staged <file>` to unstage. So, let’s use that advice to unstage the `CONTRIBUTING.md` file:

```sh
$ git restore --staged CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
    renamed:    README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
    modified:   CONTRIBUTING.md
```

The `CONTRIBUTING.md` file is modified but once again unstaged.

#### Unmodifying a Modified File with git restore

What if you realize that you don’t want to keep your changes to the `CONTRIBUTING.md` file? How can you easily unmodify it—revert it back to what it looked like when you last committed (or initially cloned, or however you got it into your working directory)? Luckily, `git status` tells you how to do that, too. In the last example output, the unstaged area looks like this:

```sh
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
    modified:   CONTRIBUTING.md
```

It tells you pretty explicitly how to discard the changes you’ve made. Let’s do what it says:

```sh
$ git restore CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
    renamed:    README.md -> README
```

**Important**: It’s important to understand that `git restore <file>` is a dangerous command. Any local changes you made to that file are gone—Git just replaced that file with the last staged or committed version. Don’t ever use this command unless you absolutely know that you don’t want those unsaved local changes.

Remember, anything that is committed in Git can almost always be recovered. Even commits that were on branches that were deleted or commits that were overwritten with an `--amend` commit can be recovered (see Data Recovery for data recovery). However, anything you lose that was never committed is likely never to be seen again.

## 2.5 Git Basics - Working with Remotes

To collaborate effectively on any Git project, understanding how to manage remote repositories is essential. Remote repositories are versions of your project hosted on the Internet or network. You can have several remote repositories, each of which can be read-only or read/write. This section covers skills for managing remote repositories, including adding and removing remotes, managing remote branches, and tracking them.

### Showing Your Remotes

To see which remote servers you have configured, use the `git remote` command:

```sh
$ git remote
origin
```

You can add the `-v` option to see the URLs associated with each remote:

```sh
$ git remote -v
origin https://github.com/schacon/ticgit (fetch)
origin https://github.com/schacon/ticgit (push)
```

If you have multiple remotes, the command lists them all. For example:

```sh
$ git remote -v
bakkdoor  https://github.com/bakkdoor/grit (fetch)
bakkdoor  https://github.com/bakkdoor/grit (push)
cho45     https://github.com/cho45/grit (fetch)
cho45     https://github.com/cho45/grit (push)
defunkt   https://github.com/defunkt/grit (fetch)
defunkt   https://github.com/defunkt/grit (push)
koke      git://github.com/koke/grit.git (fetch)
koke      git://github.com/koke/grit.git (push)
origin    git@github.com:mojombo/grit.git (fetch)
origin    git@github.com:mojombo/grit.git (push)
```

### Adding Remote Repositories

To add a new remote repository with a shortname, use `git remote add <shortname> <url>`:

```sh
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin  https://github.com/schacon/ticgit (fetch)
origin  https://github.com/schacon/ticgit (push)
pb      https://github.com/paulboone/ticgit (fetch)
pb      https://github.com/paulboone/ticgit (push)
```

Now, you can use the shortname `pb` on the command line instead of the full URL. To fetch all the information from `pb`:

```sh
$ git fetch pb
```

### Fetching and Pulling from Your Remotes

To get data from your remote projects, use:

```sh
$ git fetch <remote>
```

For example, fetching from the default `origin` remote:

```sh
$ git fetch origin
```

The `git fetch` command only downloads data to your local repository; it doesn't automatically merge it. You can merge it manually when ready.

If your branch is set up to track a remote branch, you can use `git pull` to automatically fetch and merge:

```sh
$ git pull
```

### Pushing to Your Remotes

To push your changes to the remote repository, use `git push <remote> <branch>`:

```sh
$ git push origin master
```

This command pushes your changes to the `master` branch of the `origin` remote. If someone else has pushed changes upstream before you, your push will be rejected until you fetch and merge their changes.

### Inspecting a Remote

To see more information about a remote, use `git remote show <remote>`:

```sh
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/schacon/ticgit
  Push  URL: https://github.com/schacon/ticgit
  HEAD branch: master
  Remote branches:
    master                               tracked
    dev-branch                           tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

### Renaming and Removing Remotes

To rename a remote, use `git remote rename`:

```sh
$ git remote rename pb paul
$ git remote
origin
paul
```

To remove a remote, use `git remote remove` or `git remote rm`:

```sh
$ git remote remove paul
$ git remote
origin
```

Removing a remote also deletes all remote-tracking branches and configuration settings associated with that remote.
2.6 Git Basics - Tagging
Tagging
Like most VCSs, Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (v1.0, v2.0 and so on). In this section, you’ll learn how to list existing tags, how to create and delete tags, and what the different types of tags are.

Listing Your Tags
Listing the existing tags in Git is straightforward. Just type git tag (with optional -l or --list):

$ git tag
v1.0
v2.0
This command lists the tags in alphabetical order; the order in which they are displayed has no real importance.

You can also search for tags that match a particular pattern. The Git source repo, for instance, contains more than 500 tags. If you’re interested only in looking at the 1.8.5 series, you can run this:

$ git tag -l "v1.8.5*"
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5
Note
Listing tag wildcards requires -l or --list option
If you want just the entire list of tags, running the command git tag implicitly assumes you want a listing and provides one; the use of -l or --list in this case is optional.

If, however, you’re supplying a wildcard pattern to match tag names, the use of -l or --list is mandatory.

Creating Tags
Git supports two types of tags: lightweight and annotated.

A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

Annotated Tags
Creating an annotated tag in Git is simple. The easiest way is to specify -a when you run the tag command:

$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
The -m specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

You can see the tag data along with the commit that was tagged by using the git show command:

$ git show v1.4
tag v1.4
Tagger: Ben Straub <ben@straub.cc>
Date:   Sat May 3 20:19:12 2014 -0700

my version 1.4

commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
That shows the tagger information, the date the commit was tagged, and the annotation message before showing the commit information.

Lightweight Tags
Another way to tag commits is with a lightweight tag. This is basically the commit checksum stored in a file — no other information is kept. To create a lightweight tag, don’t supply any of the -a, -s, or -m options, just provide a tag name:

$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
v1.5
This time, if you run git show on the tag, you don’t see the extra tag information. The command just shows the commit:

$ git show v1.4-lw
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
Tagging Later
You can also tag commits after you’ve moved past them. Suppose your commit history looks like this:

$ git log --pretty=oneline
15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
a6b4c97498bd301d84096da251c98a07c7723e65 Create write support
0d52aaab4479697da7686c15f77a3d64d9165190 One more thing
6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
0b7434d86859cc7b8c3d5e1dddfed66ff742fcbc Add commit function
4682c3261057305bdd616e23b64b0857d832627b Add todo file
166ae0c4d3f420721acbb115cc33848dfcc2121a Create write support
9fceb02d0ae598e95dc970b74767f19372d61af8 Update rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc Commit the todo
8a5cbc430f1a9c3d00faaeffd07798508422908a Update readme
Now, suppose you forgot to tag the project at v1.2, which was at the “Update rakefile” commit. You can add it after the fact. To tag that commit, you specify the commit checksum (or part of it) at the end of the command:

$ git tag -a v1.2 9fceb02
You can see that you’ve tagged the commit:

$ git tag
v0.1
v1.2
v1.3
v1.4
v1.4-lw
v1.5

$ git show v1.2
tag v1.2
Tagger: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Feb 9 15:32:16 2009 -0800

version 1.2
commit 9fceb02d0ae598e95dc970b74767f19372d61af8
Author: Magnus Chacon <mchacon@gee-mail.com>
Date:   Sun Apr 27 20:43:35 2008 -0700

    Update rakefile
...
Sharing Tags
By default, the git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them. This process is just like sharing remote branches — you can run git push origin <tagname>.

$ git push origin v1.5
Counting objects: 14, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (14/14), 2.05 KiB | 0 bytes/s, done.
Total 14 (delta 3), reused 0 (delta 0)
To git@github.com:schacon/simplegit.git
 * [new tag]         v1.5 -> v1.5
If you have a lot of tags that you want to push up at once, you can also use the --tags option to the git push command. This will transfer all of your tags to the remote server that are not already there.

$ git push origin --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 160 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To git@github.com:schacon/simplegit.git
 * [new tag]         v1.4 -> v1.4
 * [new tag]         v1.4-lw -> v1.4-lw
Now, when someone else clones or pulls from your repository, they will get all your tags as well.

Note
git push pushes both types of tags
git push <remote> --tags will push both lightweight and annotated tags. There is currently no option to push only lightweight tags, but if you use git push <remote> --follow-tags only annotated tags will be pushed to the remote.

Deleting Tags
To delete a tag on your local repository, you can use git tag -d <tagname>. For example, we could remove our lightweight tag above as follows:

$ git tag -d v1.4-lw
Deleted tag 'v1.4-lw' (was e7d5add)
Note that this does not remove the tag from any remote servers. There are two common variations for deleting a tag from a remote server.

The first variation is git push <remote> :refs/tags/<tagname>:

$ git push origin :refs/tags/v1.4-lw
To /git@github.com:schacon/simplegit.git
 - [deleted]         v1.4-lw
The way to interpret the above is to read it as the null value before the colon is being pushed to the remote tag name, effectively deleting it.

The second (and more intuitive) way to delete a remote tag is with:

$ git push origin --delete <tagname>
Checking out Tags
If you want to view the versions of files a tag is pointing to, you can do a git checkout of that tag, although this puts your repository in “detached HEAD” state, which has some ill side effects:

$ git checkout v2.0.0
Note: switching to 'v2.0.0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 99ada87... Merge pull request #89 from schacon/appendix-final

$ git checkout v2.0-beta-0.1
Previous HEAD position was 99ada87... Merge pull request #89 from schacon/appendix-final
HEAD is now at df3f601... Add atlas.json and cover image
In “detached HEAD” state, if you make changes and then create a commit, the tag will stay the same, but your new commit won’t belong to any branch and will be unreachable, except by the exact commit hash. Thus, if you need to make changes — say you’re fixing a bug on an older version, for instance — you will generally want to create a branch:

$ git checkout -b version2 v2.0.0
Switched to a new branch 'version2'
If you do this and make a commit, your version2 branch will be slightly different than your v2.0.0 tag since it will move forward with your new changes, so do be careful.
