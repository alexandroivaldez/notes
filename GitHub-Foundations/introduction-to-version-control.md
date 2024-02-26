# Introduction to Version Control with Git

**Git** - a distributed version control system (DVCS) that multiple developers and other contributors can use to work on a project.

## Git terminology

**Working Tree** - The set of nested directories and files that contain the project that's being worked on.

**Repo** - The directory, located at the top level of a working tree, where Git keeps all the history and metadata for a project.
  
- **bare repository** -  a repo that isn't part of a working tree; it's used for sharing or backup.

**Hash** - A number produced by a hash function that represents the contents of a file or another object as a fixed number of digits.

- Git uses hashes that are 160 bits long.

**Object** - A Git repo contains four types of objects, each uniquely identified by an SHA-1 hash.

- **blob** - An object contains an ordinary file.
- **tree** - an object represents a directory; it contains names, hashes, and permissions.
- **commit** - An object represents a specific version of the working tree.
- **tag** - A name attached to a commit.

**Branch** - A branch is a named series of linked commits. The most recent commit on a branch is called the **head**. The default branch, which is created when you initialize a repository, is called **main**, often named master in Git. The head of the current branch is named **HEAD**.

- Branches are an incredibly useful feature of Git because they allow developers to work independently (or together) in branches and later merge their changes into the default branch.

**Remote** - A remote is a named reference to another Git repository. When you create a repo, Git creates a remote named origin that is the default remote for push and pull operations.

**Commands, subcommands, and options** - Git operations are performed by using commands like git push and git pull. git is the command, and push or pull is the subcommand. The subcommand specifies the operation you want Git to perform. Commands frequently are accompanied by options, which use hyphens (-) or double hyphens (--).

- For example: `git reset --hard`

## Git VS GitHub

**Git** - a distributed version control system (DVCS) that multiple developers and other contributors can use to work on a project. It provides a way to work with one or more local branches and then push them to a remote repository.

**GitHub** - a cloud platform that uses Git as its core technology. GitHub simplifies the process of collaborating on projects and provides a website, more command-line tools, and overall flow that developers and users can use to work together. GitHub act s as the remote repository mentioned earlier.

Key features provided by GitHub include:

- Issues
- Discussions
- Pull requests
- Notifications
- Labels
- Actions
- Forks
- Projects


## Trying Git Out

`git --version` - Checks the version of Git that is installed.

`git config --global user.name "<USER_NAME>"` - Configures the global username for git.

`git config --global user.email "<USER_EMAIL>"` - Configures the global email for git.

`git config --list` - Prints out the contents of config.

`git init -b main` - Initializes git and checkouts to main branch.

`git status` - Shows the status of the working tree.

`git --help` - Gives you help with git

`git add` - Tells Git to start keeping track of changes in certain files.

`git commit` - Saves your stage changes to a snapshot.


