
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

