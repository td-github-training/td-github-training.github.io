# What is a Repository?

A _repository_ is a centralized location that stores a collection of files along with their change history.

## Local vs Remote

As a **distributed** version control system, Git has the concept of _**local**_ and _**remote**_ repositories.

![text](../../../img/img-6.png)

### Local repositories

Local repositories consists of _three_ main areas:

1. **Working directory**: This is where you do your work: creating, editing, deleting and organizing files. 
2. **Staging area**: This is where Git tracks and saves changes that will go into your next commit.
3. **Repository**: This is where Git permanently stores changes as commits. 

### Remote repositories

Remote repositories, like those hosted on GitHub, are generally _shared_ repositories where teams can collaborate on the same codebase. 

Changes made in a local repository won't affect a remote repository until the changes are _**pushed**_ and changes made in the remote repository won't affect a local repository until they are _**pulled**_ or _**fetched**_.

## Creating repositories

Repositories are created in one of two ways depending on whether you are starting from scratch or from an existing repository.

### git init

`git init` creates a new local repository in the current directory.

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

`git clone <repository>` clones a repository into a new directory.

```bash
TODO: 
git clone 
Initialized empty Git repository in /home/.git/
```

`git clone <repository> <directory>` clones a repository into the specified directory.

```bash
TODO:
git clone repo
Initialized empty Git repository in /home/repo/.git/
```

## Using repositories

### git status

Displays the status of the working directory and the staging area. 

Files can be in one of three statuses:

1. **Untracked**: Files that have not yet been staged or committed.
1. **Modified**: Modified files that have not yet been staged.
1. **Staged**: Modified files that have been marked to go into the next commit.

**Output:**

```bash
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

## Syncing repositories 

### git fetch

`git fetch` This command downloads commits, files, and refs from a remote repository to your local repository, but it does not merge them with your local branches. 

It's a safe way to see what's happening on the remote repository before integrating changes into your local working copy. After fetching, you can inspect the changes or merge them manually with `git merge`.

### git pull

`git pull` This command is essentially a combination of `git fetch` followed by `git merge`. It downloads changes from the remote repository and immediately applies those changes to your current branch. 

This is typically used when you want to update your local branch with all data from its remote counterpart.

### git push

The `git push` command is used to upload local repository content to a remote repository. It's a fundamental command in Git that allows you to share your commits with others.

#### Basic Push

The simplest use of `git push` is to upload your commits to the default remote repository (usually called `origin`) and the branch that you're currently on:

```bash
git push
```

#### Pushing to a Specific Remote

If you have multiple remote repositories, you can specify which one to push to:

```bash
git push <remote-name>
```

Replace `<remote-name>` with the name of the remote repository you want to push to.

#### Pushing a Specific Branch

You can also specify which branch you want to push:

```bash
git push <remote-name> <branch-name>
```

Replace `<branch-name>` with the name of the branch you want to push.

#### Setting the Upstream Branch

The first time you push a branch, you may need to set the upstream branch:

```bash
git push -u <remote-name> <branch-name>
```

The `-u` option sets the upstream branch, which means that future `git push` commands without a branch specified will know to push to `<branch-name>` on `<remote-name>`.

#### Force Pushing

If your local branch and the remote branch have diverged (i.e., they both have commits that the other doesn't have), `git push` will fail. You can force Git to overwrite the remote branch with your local branch using the `--force` option:

```bash
git push --force <remote-name> <branch-name>
```

Be careful with this command, as it can permanently delete commits on the remote branch.

#### Deleting a Remote Branch

You can use `git push` to delete a branch on the remote repository:

```bash
git push <remote-name> --delete <branch-name>
```


## Configuration

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

## Quiz

<div class="quizdown">
  <div id="repositories-quiz.js" ></div>
</div>