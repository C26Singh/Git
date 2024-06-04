
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
