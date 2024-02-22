# Merge strategies: Rebase

In this section, we will discuss another popular merge strategy, rebasing.

## Understanding Git merge strategies

Git uses three primary merge strategies:

### Recursive

A recursive merge means that changes have been made on both the base branch and the feature branch and git needs to recursively combine them. With a recursive merge, a new "merge commit" is made to mark the point in time when the two branches came together. This merge commit is used the most often when you click `merge` on a pull request.

### Fast-forward

A fast-forward merge assumes that no changes have been made on the base branch since the feature branch was created. This means that the branch pointer for base can simply be "fast forwarded" to point to the same commit as the feature branch.

### Octopus

A merge of 3 or more branches is an octopus merge. This will also create a merge commit with multiple parents.

## About Git rebase

`git rebase` should be used with purpose, as it will be rewriting the history of commits on a repository.

> For helpful scenarios for when to use rebase, amend, and reset try [this](https://dangitgit.com/) site

With that being said, `git rebase` enables you to modify your commit history in a variety of ways. For example, you can use it to reorder commits, edit them, squash multiple commits into one, and much more.

To enable all of this, `rebase` comes in several forms but we will use `git rebase --interactive`, or `git rebase -i` for short.

Typically, you would use `git rebase -i` to:

- Replay one branch on top of another branch
- Edit previous commit messages
- Combine multiple commits into one
- Delete or revert commits that are no longer necessary

## Creating a linear history with `git rebase`

One of the most common uses of rebase is to eliminate recursive merges and create a linear history.

![Git Rebase](./img/git-rebase.png)

### Setup

1. First, switch back to the `main` branch: `git switch main`
1. Find the SHA of the initial commit: `git log --oneline`
1. Reset to the SHA of the initial commit: `git reset --hard SHA`
1. Create a new branch and check out to it: `git switch -c rebase-me`
1. Cherry-pick files 4-6 onto the `rebase-me` branch using the reflog.
1. Switch to main: `git switch main`
1. Cherry-pick files 1-3 onto the `main` branch using the reflog.
1. Look at your history: `git log --oneline --graph --decorate --all`
1. If you merged now, it would be a recursive merge.

### Begin the rebase

1. Switch to the `rebase-me` branch: `git switch rebase-me`
1. Start the merge: `git rebase -i main`
1. Your text editor will open, allowing you to see the commits to be rebased.
1. Save and close the `rebase-todo`.
1. Watch your rebase happen on the command-line.
1. Take another look at your history: `git log --oneline --graph --decorate --all`
1. If you merged now, it would be a fast-forward merge.

### Finish the merge

1. Switch to main, the branch you will merge into: `git switch main`
1. Merge your changes in to main: `git merge rebase-me`

Resolving merge conflicts after a Git rebase
============================================

When you perform a `git rebase` operation, you're typically moving commits around. Because of this, you might get into a situation where a merge conflict is introduced. That means that two of your commits modified the same line in the same file, and Git doesn't know which change to apply.

After you reorder and manipulate commits using `git rebase`, should a merge conflict occur, Git will tell you so with the following message printed to the terminal:

```
error: could not apply fa39187... something to add to patch A

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
Could not apply fa39187f3c3dfd2ab5faa38ac01cf3de7ce2e841... Change fake file

```

Here, Git is telling you which commit is causing the conflict (`fa39187`). You're given three choices:

-   You can run `git rebase --abort` to completely undo the rebase. Git will return you to your branch's state as it was before `git rebase` was called.
-   You can run `git rebase --skip` to completely skip the commit. That means that none of the changes introduced by the problematic commit will be included. It is very rare that you would choose this option.
-   You can fix the conflict.

To fix the conflict, you can follow [the standard procedures for resolving merge conflicts from the command line](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line). When you're finished, you'll need to call `git rebase --continue` in order for Git to continue processing the rest of the rebase.
