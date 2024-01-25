## What is a Repository?

A Git repository is a centralized location that stores a collection of files along with their revision history.  Each developer maintains a local copy of the entire repository, including all files and their complete history, enabling seamless offline work and efficient merging of changes at a later stage. 

#### Creating a Repository

Repositories are created by using `git init`, for example:

```shell
mkdir practice-repo && cd practice-repo

git init
Initialized empty Git repository in /home/me/practice-repo/.git/
```

Alternatively, you can do all of the above in one-line:

```sh
git init practice-repo
Initialized empty Git repository in /home/me/practice-repo/.git/
```

#### Repository Status

To verify the current state of your repository type: `git status`. 

```sh
git status
On branch main
Your branch is up-to-date with 'origin/main'.
nothing to commit, working tree clean
```

Right now, we can see that we are on branch `main`, everything is up-to-date with `origin/main` and our working tree is clean.

---

### Ignoring Files

Git enables you to ignore specific files, files types, and folders through the use of a text file you can add to your repository titled `.gitignore`. This file instructs Git to stop tracking changes of certain files, which means that these files will not be pushed to GitHub from your local machine.

**Example files that you might want Git to ignore:**

1. Secrets, e.g. `*.pem`, `*.key`
1. Binary files, e.g. `*.pdf`, `*.docx`
1. Log files, e.g. `*.log`
1. Build files, e.g. `Build/*`

#### github/gitignore

The [github/gitignore repository](https://github.com/github/gitignore) is a collection of `.gitignore` templates based on popular programming languages.

#### gitignore.io

[This website](https://www.toptal.com/developers/gitignore) is another resource for you to find appropriate `.gitignore` templates when your project contains multiple programming languages.
