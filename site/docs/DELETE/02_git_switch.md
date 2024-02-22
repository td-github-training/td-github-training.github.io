git switch
--

**The "switch" command allows you to switch your current HEAD branch. It's relatively new (added in Git v2.23) and provides a simpler alternative to the classic "checkout" command.**

The "switch" command provides a simple alternative to "checkout". It has a very clear and limited purpose: *switching and creating branches*!

Important Options
-----------------

### `<branch-name>`

**The name of a local or remote branch that you want to switch to.** If you specify the name of an existing *local* branch, you will switch to this branch and make it the current "HEAD" branch.\
But you can also specify a *remote* branch: in that case, Git will create a new local branch based on that remote branch and set up a [tracking relationship](https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch).

### `-c <new-name>`

**The name of a new local branch you want to create.** Using the "-c" flag, you can specify a name for a *new* branch that should be created. You can also specify a starting point (either another branch or a concrete revision); if you don't provide any specific starting point, the new branch will be based on the current HEAD branch.

## `<branch-name> --discard-changes`

**Switch to the specified branch and discard any local changes to obtain a clean working copy.** As a general rule, your working copy does NOT have to be clean before you can use "switch". However, if you have local modifications that would conflict with the switched-to branch, Git would abort the switch. Using the "--discard-changes" flag will discard any of your current local changes and then switch to the specified branch.

Usage Examples
--------------

The most common scenario is to simply specify the local branch you want to switch to:

```
$ git switch other-branch
```

This will make the given branch the new HEAD branch. If, in one go, you also want to create a new local branch, you can use the "-c" parameter:

```
$ git switch -c new-branch
```

If you want to check out a remote branch (that doesn't yet exist as a local branch in your local repository), you can simply provide the remote branch's name. When Git cannot find the specified name as a local branch, it will assume you want to check out the respective remote branch of that name:

```
$ git switch remote-branch
```

This will not only create a local branch, but also set up a "tracking relationship" between the two branches, making sure that pulling and pushing will be as easy as "git pull" and "git push".
