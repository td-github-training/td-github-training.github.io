# What is a Commit?

A **commit** is a **snapshot** of an _entire_ repository at a given point in time.

## A typical workflow

As we mentioned in [How Git Works](git_101?id=how-git-works), Git has a two-step process to save changes to a repository.

![alt text](../../../img/image-24.png ':size=550px')

In practice, this looks like:
1. You make changes in your **working directory**
2. When you're ready to save these changes, you **stage** them using `git add`
3. Then you the **commit** the staged changes to the repository using `git commit`

## Staging changes

### git add

Copies changes from the working directory to the staging area.

**Staging files**

The simplest way to use `git add` is to add all changes (new, modified, and removed files) in the current directory and its subdirectories:

```bash
git add .
```

If you want to add changes from a specific file, you can do so by specifying the file:

```bash
git add filename
```

You can also add multiple files at once:

```bash
git add filename1 filename2
```

**Staging hunks**

If you've made several changes to a file but only want to stage some of them, you can use `git add -p`:

```bash
git add -p filename
```

This command will prompt you to stage individual changes (or 'hunks') in the file. You can choose to stage, skip, or split each hunk.

**Viewing Staged Changes**

After you've staged some changes, you can view them with `git diff --staged`:

```bash
git diff --staged
```

This command will show you a diff of what's been staged but not yet committed.

**Unstaging Changes**

If you've staged some changes with `git add` but then decide you don't want to commit them, you can unstage them with `git restore --staged`:

```bash
git restore --staged filename
```

This command will remove the changes from the staging area but won't alter the working directory. The changes will still be there, but they won't be included in the next commit.


## Committing changes

### git commit

Saves a snapshot of the changes in staging area to the local repository as a commit.

**Committing staged changes**

The simplest way to use `git commit` is to commit all staged changes with a message:

```bash
git commit -m "Your commit message"
```

> The `-m` option allows you to write the commit message directly in the command line

**Committing all changes**

If you've made several changes but haven't staged them yet, you can commit all changes (modified and deleted files, but not new files) with one command:

```bash
git commit -a -m "Your commit message"
```

> The `-a` option automatically stages every file that is tracked and has been modified or deleted

## Viewing history

### git log

The git log command is used to view the commit history of your Git repository. It shows the commit hashes, authors, dates, and commit messages.

```bash
git log
```

**Output:**

```bash
commit 4a8e17d7f593a3c0ad626648175e8b4858e77f2c (HEAD -> main)
Author: Your Name <your.email@example.com>
Date:   Thu Sep 30 14:33:50 2021 -0700

    Update file1.txt

commit 9d3a192570a772443332d6c55b3002a5d7e2c1b5
Author: Your Name <your.email@example.com>
Date:   Thu Sep 30 14:31:26 2021 -0700

    Initial commit
```

---

> The `--oneline` option can be used to display the commit history in a more compact format:

```bash
git log --oneline
```


**Output:**

```bash
4a8e17d (HEAD -> main) Update file1.txt
9d3a192 Initial commit
```

---

> The `--oneline --graph --decorate --all` command provides a visual representation of the commit history. 

```bash
git log --oneline --graph --decorate --all
```

**Output:**

```bash
* 7a8b9cd (HEAD -> main, origin/main) Fix bug
* 6b7c8de Implement feature
| * 5c6d7ef (feature-branch) Update feature
| * 4e5f6dg Add feature
|/  
* 3d4e5cf Refactor code
* 2c3d4bf Update README
* 1b2c3ad Initial commit
```


## Comparing changes

### git diff

Allows you to see the difference between any two refs in a repository. 

The diagram below shows how you can compare the content of your working area, staging, and HEAD (or the most recent commit):

<center>

![Git Diff Options](../../../img/diff-options.png ':size=500')

</center>

```bash
git diff
```

**Output:**

```bash
diff --git a/file1.txt b/file1.txt
index e965047..2c7ee5a 100644
--- a/file1.txt
+++ b/file1.txt
@@ -1 +1,2 @@
 Hello, World!
+Hello, Git!
```

#### Common flags

- `git diff --staged`
- `git diff HEAD`
- `git diff main feature`
- `git diff origin/main main`


## Fixing mistakes

### git reset

The `git reset` command is a powerful tool that allows you to manipulate the state of your Git repository. It can be used to unstage files, undo commits, and more.

#### Unstaging Files

If you've staged changes that you don't want to commit, you can use `git reset` to unstage them:

```bash
git reset <file>
```

This command will unstage the specified file, but it won't alter the file itself.

#### Undoing Commits

`git reset` can also be used to undo commits. There are three main modes: `--soft`, `--mixed`, and `--hard`.

* **Soft Reset**

A soft reset moves the HEAD pointer to a specified commit, but it leaves the staging area and the working directory unchanged. This is useful if you want to keep your changes, but move the HEAD pointer.

```bash
git reset --soft <commit>
```

* **Mixed Reset**

A mixed reset (the default mode) moves the HEAD pointer and alters the staging area to match the specified commit, but it leaves the working directory unchanged. This is useful if you want to undo a commit but keep your changes.

```bash
git reset --mixed <commit>
# or
git reset <commit>
```

* **Hard Reset**

A hard reset moves the HEAD pointer, alters the staging area, and alters the working directory to match the specified commit. This effectively undoes all changes since the specified commit. Be careful with this mode, as it can permanently delete your changes.

```bash
git reset --hard <commit>
```

### git revert

A safe way to undo changes by creating a new commit that undoes changes made in a previous commit.  It's useful for fixing mistakes and for safely removing changes without rewriting the project's history. 

#### Reverting with No Commit

If you run `git revert` without a commit hash, Git will ask you to enter a commit message for a new commit that undoes the changes made in the last commit:

```bash
git revert
```

#### Reverting a Single Commit

If you've made a mistake in a commit and want to undo the changes made in that commit, you can use `git revert`:

```bash
git revert <commit-hash>
```

This command will create a new commit that undoes the changes made in the commit specified by `<commit-hash>`. Your working directory will be updated to reflect the new commit.

#### Reverting a Range of Commits

If you've made mistakes in a range of commits and want to undo all of them, you can use `git revert` with a commit range:

```bash
git revert <older-commit-hash>..<newer-commit-hash>
```

This command will create new commits for each commit in the range that undo the changes made in those commits. Your working directory will be updated to reflect the new commits.

>Note: The older commit is not included in the range. If you want to include it, use three dots instead of two:
> 
> ```bash
> git revert <older-commit-hash>...<newer-commit-hash>
> ```


### git rebase

The `git rebase` command is a powerful tool that allows you to modify your commit history by moving or combining your commits. 

#### Interactive Rebase

Interactive rebase allows you to modify individual commits as they are moved. This is useful for combining, reordering, or modifying commits.

```bash
# Start an interactive rebase
git rebase -i HEAD~3
```

This command will start an interactive rebase for the last 3 commits. Git will open a text editor with a list of the commits and options for what to do with each commit:

```bash
pick 1fc6c95 do something
pick 6b2481b do something else
pick dd1475d changed some things
```

You can replace `pick` with an action keyword:

- `reword`: Change the commit message.
- `edit`: Amend the commit.
- `squash`: Combine this commit with the previous one.
- `fixup`: Like `squash`, but discard this commit's log message.
- `drop`: Remove the commit.

Save and close the file to continue the rebase.

#### Abort a Rebase

If you want to stop the rebase process at any time, you can use `git rebase --abort`:

```bash
git rebase --abort
```

This will stop the rebase and return your repository to the state it was in before you started the rebase.


## Syncing changes

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

## Quiz

<div class="quizdown">
  <div id="commit-quiz.js" ></div>
</div>