# Git Basics

## What is Git?

Git is a version control system

### What is a version control system

A version control system allows you to track and manage changes made to your source files over time.

### Why should we care as developers?

Because we can review the project's history and find out:

- Which changes were made?
- Who made those changes?
- When were the changes made?
- Why were changes needed?

### Typical features include

- Revert selected files to a previous state
- Revert the entire project back to a previous state
- Compare changes over time
- See who introduced an issue and when

## Types of version control systems

- Local
- Centralized
- Distributed

### Local VCS

- Local VCS stored tracked different file versions as independent files and kept these versions in a database.
- Versioning took place on the developer's local computer, and the idea was to keep a single "check out" copy of the project at any given time.

### Centralized VCS

- Have a single server that contains all the file versions, and different clients would then "check out" files from that central server.
- Using these VCS systems prevented users from overriding others' work. However, if two changes conflicted, someone had to manually go and merge the differences. It can be hard to scale when you have dozens of developers. There was latency b/c you had to send requests over a network.

### Distributed VCS (e.g. Git)

- The entire working repository is copied across many distributed computers. Introduced the concept of "branches" that allowed developers to work independently, and to experiment with new ideas.
- Having the local repository makes development much faster, because you no longer have to send requests over a network, and since everyone has a complete copy of the project, any data lost in one node can be recovered.

### Delta-based version control

- Most Version Control Systems (e.g. CVS, Subversion, Perforce, Bazaar, and others) think of the information they store as a set of files and the changes made to each file over time (this is commonly described as delta-based version control.

### Stream of snapshots

- Git thinks of its data more as a series of snapshots of a miniature filesystem.
- With git, every time you commit or save the state of your project, Git basically takes a picture of what all your files look like at the moment and stores a reference to that snapshot.
- To be efficient, if files have not changed, Git doesn't store the file again, just a link to the previous identical file it has already in store.

### Integrity

- Everything in Git is checksummed before it is stored and is then referred to by that checksum. This means it’s impossible to change the contents of any file or directory without Git knowing about it. This functionality is built into Git at the lowest levels and is integral to its philosophy. You can’t lose information in transit or get file corruption without Git being able to detect it.
- The mechanism that Git uses for this checksumming is called a SHA-1 hash. This is a 40-character string composed of hexadecimal characters (0–9 and a–f) and calculated based on the contents of a file or directory structure in Git. A SHA-1 hash looks something like this:

```sh
24b9da6552252987aa493b52f8696cd6d3b00373
```

You will see these hash values all over the place in Git because it uses them so much. In fact, Git stores everything in its database not by file name but by the hash value of its contents.

```sh
git log

# or

git log --oneline
```

### Git states

- **modified**: means that you have changed the file, but have not committed to your database yet.
- **staged**: means that you have marked a modified file in its current version to go into your next commit snapshot.
- **committed**: means that your data is stored in your local database.

### These 3 stages are related to the three main section of a git project:

- **the working tree**: is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.
- **the staging area**: is a file, generally contained in your git directory, that stored information about what will got into your next commit. Its technical name is git parlance is the "index", but the phrase "staging area" works just as well.
- **the git directory**: is where git stores the metadata and object database for your project. This is the most important part of git, and is what is copied when you clone a project from another computer.

### Basic git workflow

1. You modify a file in your working tree
2. You selectively stage those changes you want to be part of your next commit, which only adds those changes to the staging area.
3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your git directory.

### Install git on mac

```sh
# installing git
brew update
brew install git
brew install git-gui

# checking installation
git --version
```

### Install git on windows

```sh
# 1. Install chocolatey
# https://chocolatey.org/install

# 2. Install git
choco install git.install
```

### Install git on Linux

```sh
# install git on ubuntu
sudo apt update
sudo git install git
```

## Configuring Git

git comes with a tool called git config that enables you to configure variables that control all aspects of how Git looks and operates.

```sh
git config --list --show-origin

# configuring user's name and email
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"

# unix users
git config --global core.editor vim

# setting your default branch
git config --global init.defaultBranch main

# fetch user name
git config user.name
```

## Finding Help in Git

Displaying man (manual) pages for specific commands with git help command:

```sh
# example 1
git help config
git help add

# example 2
git add --help
git add -h # concise output

# example 3
man git-add
```

### Other resources

- [Learn Git Branching](https://learngitbranching.js.org/)
- [What is a working tree in git?](https://craftquest.io/articles/what-is-the-working-tree-in-git#:~:text=Th%20Working%20Tree%20in%20Git,which%20you%20remove%20unneeded%20files)
- [Git Workflow](https://backlog.com/git-tutorial/git-workflow/)
- [Difference between HEAD, working tree and index in Git?](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)
