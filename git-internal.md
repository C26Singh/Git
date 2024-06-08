# Git Internals: Plumbing and Porcelain
## Plumbing vs. Porcelain
- **Plumbing Commands**: Low-level commands designed to be combined in scripts (e.g., `git cat-file`, `git hash-object`).
- **Porcelain Commands**: High-level, user-friendly commands (e.g., `git checkout`, `git branch`).
### Typical .git Directory Structure
### Key Components
- **config**: Project-specific configuration options.
- **info**: Contains a global exclude file.
- **hooks/**: Client- or server-side hook scripts.
- **objects/**: Stores all the content of your database.
- **refs/**: Stores pointers to commit objects (branches, tags, remotes).
- **HEAD**: Points to the current branch.
- **index**: Stores staging area information.

## Core Parts of Git
1. **Objects Directory**: Stores all content as objects.
2. **Refs Directory**: Pointers to commit objects (branches, tags, remotes).
3. **HEAD File**: Indicates the current branch.
4. **Index File**: Contains the staging area information.
