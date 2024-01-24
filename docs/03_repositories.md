## Using Repositories

A Git repository is a centralized location that stores a collection of files along with their revision history. It is a crucial component of the Git version control system, which enables collaborative development and allows multiple developers to work on a project simultaneously. Each developer maintains a local copy of the entire repository, including all files and their complete history, enabling seamless offline work and efficient merging of changes at a later stage. 

### Creating Repositories

Repositories are created by using `git init`:

```sh
mkdir practice-repo

cd practice-repo

git init
```

Alternatively, you can use:

```sh
git init practice-repo
```

### Repository Status

`git status` is a command to verify the current state of your repository and the files it contains. Right now, we can see that we are on branch main, everything is up-to-date with origin/main and our working tree is clean.

```shell-session
git status
On branch main
Your branch is up-to-date with 'origin/main'.
nothing to commit, working tree clean
```
