# What is a Repository?

A _repository_ is a centralized location that stores a collection of files along with their change history.

## Local vs Remote

As a **distributed** version control system, Git has the concept of _**local**_ and _**remote**_ repositories.

![text](../../../img/img-6.png)

**Local repositories** consists of _three_ main areas:

1. **Working directory**: This is where you do your work - creating, editing, deleting and organizing files.
2. **Staging area**: This is where Git tracks and saves changes that will go into your next commit.
3. **Repository**: This is where Git permanently stores changes as commits.

**Remote repositories**, like those hosted on GitHub, are where teams collaborate on a given codebase.

## Creating repositories

Repositories are created in one of two ways depending on whether you are starting from scratch or from an existing repository.

### git init

`git init` creates a new ***local*** repository in the current directory.

```bash
git init
Initialized empty Git repository in /home/.git/
```

`git init <directory>` creates a new local repository in the specified directory.

```bash
git init repo
Initialized empty Git repository in /home/repo/.git/
```

### git clone

`git clone <repository>` clones a ***remote*** repository into a new directory.

```bash
> git clone https://github.com/githubschool/repo.git
Cloning into 'repo'...
remote: Enumerating objects: 452, done.
...
```

`git clone <repository> <directory>` clones a ***remote*** repository into the specified directory.

```bash
> git clone https://github.com/githubschool/repo.git newrepo
Cloning into 'newrepo'...
remote: Enumerating objects: 452, done.
...
```

## Using repositories

### git status

`git status` displays the status of the working directory and the staging area.

Files can be in one of three statuses:

1. **Untracked**: Files that have not yet been staged or committed.
1. **Modified**: Modified files that have not yet been staged.
1. **Staged**: Modified files that have been marked to go into the next commit.

For example:

```bash
> git status
On branch main
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
    modified: hello.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
    modified: main.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
    hello.pyc
```

## Understanding remotes

In distributed version control systems, it is common for many copies of a repository to exist, with each of these copies, or "clones" being located on different machines and locations.

Git helps you manage these connections between these repositories using a concept known as `remotes`.

In conclusion, when you clone a repository, Git automatically sets up a remote named `origin` that points to the cloned repository. But when you initialize a new repository, Git does not set up any remotes, and you need to do this manually if you want to push to or pull from a remote repository.

### Initializing a Repository

When you create a new repository on your local machine using the `git init` command, Git initializes a new repository, but it does not add any remotes. This is because Git doesn't know where you want to push to or pull from.

### Cloning a Repository

When you clone a repository using the `git clone` command, Git does a few things:

1. It creates a new directory on your local machine with the same name as the repository.
2. It initializes a new Git repository in this directory (`git init`).
3. It adds a remote named `origin` that points to the URL of the cloned repository.
   - This is done using the `git remote add` command, but you don't see this because it's done automatically by `git clone`.

You can see this remote by navigating to the repository directory and running `git remote -v`. The output will look something like this:

```bash
origin  https://github.com/user/repo.git (fetch)
origin  https://github.com/user/repo.git (push)
```

This means that when you run `git push` or `git pull` while on a branch that has an upstream set to `origin`, Git knows that it needs to push to or pull from the repository at `https://github.com/user/repo.git`.

### `origin`

When you clone a repository, Git automatically creates a remote named 'origin' that points to the location of the cloned repository. This is your main connection to the original repository: you can pull changes from it and push your updates to it.

### git remote

`git remote` allows you to create, view, and delete connections to other repositories.

```bash
git remote
```

To view the remote connections along with their URLs, use the `-v` option:

```bash
git remote -v
```

### git remote add

`git remote add <name> <url>` allows you to add a new remote connection.

```bash
git remote add origin https://github.com/user/repo.git
```

In this example, `origin` is the name of the remote connection and `https://github.com/user/repo.git` is the URL of the remote repository.

### git remote rename

`git remote rename <old> <new>` allows you to rename a remote connection.

```bash
git remote rename origin destination
```

In this example, the remote named `origin` is renamed to `destination`.

### git remote remove

`git remote remove <name>` allows you to remove a remote connection.

```bash
git remote remove destination
```

In this example, the remote named `destination` is removed.

### git remote set-url

`git remote set-url <name> <newurl>` allows you to change the URL of a remote connection.

```bash
git remote set-url origin https://github.com/user/newrepo.git
```

In this example, the URL of the remote named `origin` is changed to `https://github.com/user/newrepo.git`.

### git remote show

`git remote show <name>` gives you information about a particular remote connection. It shows which branch is automatically fetched when you run `git pull` and which remote branch is pushed to when you run `git push`.

To inspect a remote, use the `git remote show` command followed by the name of the remote:

```bash
git remote show origin
```

This command displays information about the remote named `origin`. The output will include the fetch and push URLs for the remote, the remote branches that have been tracked, the local branches that are connected to remote branches, and more.

## Syncing repositories

### git fetch

`git fetch <remote> <branch>` downloads commits, files, and refs from a remote repository to your local repository, but it does not merge them with your local branches.

It's a safe way to see what's happening on the remote repository before integrating changes into your local working copy. After fetching, you can inspect the changes or merge them manually with `git merge`.

### git pull

`git pull <remote> <branch>` is essentially a combination of `git fetch` followed by `git merge`. It downloads changes from the remote repository and immediately applies those changes to your current branch.

This is typically used when you want to update your local branch with all data from its remote counterpart.

### git push

`git push <remote> <branch>` is used to upload local repository content to a remote repository.

To upload your commits to the **default** remote repository (usually called `origin`) and the branch that you're currently on:

```bash
git push
```

If you have **multiple** remote repositories, you can specify which one to push to:

```bash
git push <remote-name>
```

You can also specify a **specific** branch you want to push:

```bash
git push <remote-name> <branch-name>
```

#### Setting the Upstream Branch

The first time you push a branch, you may need to set the upstream branch:

```bash
git push -u <remote-name> <branch-name>
```

> The `-u` option sets the upstream branch, which means that future `git push` commands without a branch specified will know to push to `<branch-name>` on `<remote-name>`.

#### Force Pushing

If your local branch and the remote branch have diverged (they both have commits that the other doesn't have), `git push` will fail.

You can force Git to overwrite the remote branch with your local branch using the `--force` option:

```bash
git push --force <remote-name> <branch-name>
```

!> Be careful using `git push --force`, as it can permanently delete commits on the remote branch.


## Configuration

### .gitignore

The `.gitignore` file is used by Git to determine which files and directories to ignore when committing changes. It's a plain text file where each line contains a pattern for files/directories to ignore.

For example:

```bash
# No .log files
*.log

# No .tmp files
*.tmp

# Ignore the node_modules directory
node_modules/

# Ignore all files in the dist directory
dist/*

# Ignore the .env file
.env
```

> In this example, `.log` and `.tmp` files, the `node_modules` directory, all files in the `dist` directory, and the `.env` file will be ignored by Git.

**.gitignore Pattern Format**

- `*` matches zero or more characters
- `?` matches one character
- `[abc]` matches any character a, b, or c
- `**` matches any number of directories. For example, `**/foo` matches file or directory `foo` anywhere in the project
- `/` at the start of the pattern means the pattern will only match files and directories in the repository root. For example, `/foo` matches file or directory `foo` in the repository root, not `bar/foo`
- `/` at the end of the pattern specifies a directory
- `!` at the start of the pattern can be used to negate the pattern, making Git ignore files that would otherwise be ignored. For example, `!important.log` would track the file `important.log`, even if `.log` files were ignored with `*.log`

**Notes**

- Comments can be added in `.gitignore` with `#` at the start of the line.
- Blank lines are ignored.
- Standard glob patterns work.
- You can have multiple `.gitignore` files in a single repository. A `.gitignore` file in a specific directory applies to that directory and its subdirectories.
- If a file is already tracked by Git before it was added to `.gitignore`, you need to untrack it manually with `git rm --cached filename`.

**Example files that you might want Git to ignore:**

1. Secrets, e.g. `*.pem`, `*.key`
1. Binary files, e.g. `*.pdf`, `*.docx`
1. Log files, e.g. `*.log`
1. Build files, e.g. `Build/*`

**Links**

There are many online resources that provide comprehensive pre-built `.gitignore` files for a variety of project types.  Before you build your own, be sure to check the following sites:

- [github/gitignore repository](https://github.com/github/gitignore)
- [gitignore.io](https://www.toptal.com/developers/gitignore)

## Quiz

<div class="quizdown">
  <div id="repositories-quiz.js" ></div>
</div>