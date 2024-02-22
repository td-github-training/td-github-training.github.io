# What is a Repository?

A _repository_ is a centralized location that stores a collection of files along with their git history.

## Creating a repository

Repositories are created in one of two ways depending on whether you are starting from scratch or from an existing repository.

### git init

Creates a new local repository in the current directory.

```bash
git init 
Initialized empty Git repository in /home/me/newrepo/.git/
```

### git init _repo_

Creates a new local repository in the specified directory.

```bash
git init repo
Initialized empty Git repository in /home/me/repo/.git/
```

### git clone

```bash
git clone
Initialized empty Git repository in /home/me/repo/.git/
```

TODO: 

## Using a repository

### git status

To verify the current state of your repository type: `git status`

```sh
git status
On branch main
Your branch is up-to-date with 'origin/main'.
nothing to commit, working tree clean
```

In the above example, we can see that we are on branch `main`, everything is up-to-date with `origin/main` and our working tree is clean.

## Configuration

TODO: Add line ending configuration

### .gitignore

A `.gitignore` file in your repository stores names and file types. This file and its contents instruct Git to stop tracking changes of certain files, which means that these files will not be pushed to GitHub from your local.

**Example files that you might want Git to ignore:**

1. Secrets, e.g. `*.pem`, `*.key`
1. Binary files, e.g. `*.pdf`, `*.docx`
1. Log files, e.g. `*.log`
1. Build files, e.g. `Build/*`

#### Links  
- Collection of .gitignore templates from GitHub: [github/gitignore repository](https://github.com/github/gitignore)
- Collection of .gitignore templates from toptal: [gitignore.io](https://www.toptal.com/developers/gitignore) 