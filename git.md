# Git
Version Control System and Source Code Management Tool

## Setup and Configuration
Installed via Homebrew
    brew install git
Ensure $PATH looks to /usr/local/bin

### Configuration levels
1. System (All users on the system) /etc/gitconfig
2. Global (Global to User) ~/.gitconfig
3. Local (per Repository) .git/config

    git config --global user.name "Full Name"
    git config --global user.email "name@place.com"
    git config --global color.ui true

### Recommended Global ignores
Create a global ignore file
    git config --global core.excludesfile ~/.gitignore_global

and add the following: [from OctoCat](https://gist.github.com/octocat/9257657)

    # Compiled source #
    ###################
    *.com
    *.class
    *.dll
    *.exe
    *.o
    *.so

    # Packages #
    ############
    # it's better to unpack these files and commit the raw source
    # git has its own built in compression methods
    *.7z
    *.dmg
    *.gz
    *.iso
    *.jar
    *.rar
    *.tar
    *.zip

    # Logs and databases #
    ######################
    *.log
    *.sql
    *.sqlite

    # OS generated files #
    ######################
    .DS_Store
    .DS_Store?
    ._*
    .Spotlight-V100
    .Trashes
    ehthumbs.db
    Thumbs.db

## Repository Basics
Within selected directory

Create a Repository
    git init

See what's tracked, what's not, and changes not committed
    git status

Move file changes to staging area
    git add filename, git add -a, git add .

Commit the changes
    git commit -m "message"

Create .gitignore to ignore specific local files and folders

## Effective use of the Staging Area
It's important to remember that the Staging Area allows you commit specific incremental changes and annotate them. Commit messages should be clear and concise to enable anyone to know exactly what was done. If a lot of changes are made, either added features or fixed bugs, care should be used to ensure each meaningful change is individually committed. By selectively choosing precisely what to commit, these changes remain organized so that if a reversion is necessary you'll know exactly where to go and what to expect.

## Under the Hood
Git creates a tree structure. The tree contains header info, and for each file and directory: the file permissions, the object - either a blob or another tree, a SHA1, and the file/directory name. A Blob is a Git Object referred to via the SHA1, compressed with zlib containing the contents of the file.
A commit contains the author info, committer info, the commit message, SHA1 of any parent commits, and the SHA1 of the tree the commit points to.

## Diff
See changes (prior to staging)
    git diff filename

Compare Staging Area with Working Directory
    git diff --staged filename

## Log
git log

git log --stat

git log --oneline

git log --graph

git log --pretty "..."

git log --graph --all --decorate

HEAD HEAD~ HEAD~2

## Branches
Create a branch
    git branch name

Move to branch
    git checkout name

    git branch

    git branch -b name

    git merge name

    git branch -d name

    git rebase name

## Working with Remotes

### SSH Key
Create the key pair. Github recommends using an email as the message
    ssh-keygen -t rsa -C 'message'

Test Authentication
    ssh -T git@github.com

## Github Pages
