
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
