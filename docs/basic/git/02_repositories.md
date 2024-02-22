# What is a Repository?

* A centralized location that stores a collection of files along with their git history  
* Each developer maintains a local copy of the entire git repository

### Creating a Repository

Repositories are created with git on the command line by using `git init`, for example:

```sh
git init new-repo
Initialized empty Git repository in /home/me/practice-repo/.git/
```

### Repository Status

To verify the current state of your repository type: `git status`

```sh
git status
On branch main
Your branch is up-to-date with 'origin/main'.
nothing to commit, working tree clean
```

Right now, we can see that we are on branch `main`, everything is up-to-date with `origin/main` and our working tree is clean.

---

## Ignoring Files

A `.gitignore` file in your repository stores names and file types. This file and its contents instruct Git to stop tracking changes of certain files, which means that these files will not be pushed to GitHub from your local.

**Example files that you might want Git to ignore:**

1. Secrets, e.g. `*.pem`, `*.key`
1. Binary files, e.g. `*.pdf`, `*.docx`
1. Log files, e.g. `*.log`
1. Build files, e.g. `Build/*`

### Links  
- Collection of .gitignore templates from GitHub: [github/gitignore repository](https://github.com/github/gitignore)
- Collection of .gitignore templates from toptal: [gitignore.io](https://www.toptal.com/developers/gitignore) 