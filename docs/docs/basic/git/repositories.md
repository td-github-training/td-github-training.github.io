# What is a Repository?

A _repository_ is a centralized location that stores a collection of files along with their git history.

## Local vs Remote

As a **distributed** version control system, Git has the concept of _**local**_ and _**remote**_ repositories.

![text](../../../img/img-6.png)

### Local repositories

A local repository is located on your personal computer, where you're doing the work, and you can work on it without an internet connection.

Local repositories consists of three main areas managed by Git:

1. **Working directory**: This is where you do your work: creating, editing, deleting and organizing files. 
2. **Staging area**: This is where Git tracks and saves changes that will go into your next commit.
3. **Repository**: This is where Git permanently stores changes as commits. 

### Remote repositories

Remote repositories are _shared_ repositories where teams can collaborate on the same codebase. 

Changes made in a local repository won't affect a remote repository until the changes are _**pushed**_ and changes made in the remote repository won't affect a local repository until they are _**pulled**_ or _**fetched**_.

## Creating repositories

Repositories are created in one of two ways depending on whether you are starting from scratch or from an existing repository.

### git init

Creates a new local repository in the current directory.

```bash
git init 
Initialized empty Git repository in /home/me/newrepo/.git/
```

#### git init _repo_

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

## Using repositories

### git status

Displays the state of the working directory and the staging area. 

Git has three main statuses for your files: 

1. **Untracked**: Files that have not yet been staged or committed.
1. **Modified**: Modified files that have not yet been staged.
1. **Staged**: Modified files that have been marked to go into the next commit.

#### Sample output

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

## Quiz

<div class="quizdown">
  <div id="repositories-quiz.js" ></div>
</div>