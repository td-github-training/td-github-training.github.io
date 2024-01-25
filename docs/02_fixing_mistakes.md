## Exercise: Fixing Mistakes

### Soft reset

Using the practice repository we created earlier, let's try a `reset --soft`.

1. View the history of our project: `git log --oneline --decorate`
1. Identify the current location of `HEAD`.
1. Go back two commits in history: `git reset --soft HEAD~2`
1. See the tip of our branch (and `HEAD`) is now sitting two commits earlier than it was before: `git log --oneline --decorate`
1. The changes we made in the last two commits should be in the staging area: `git status`
1. All the files still exist locally: `ls`
1. Let's remove the extra file we created earlier: `git rm --cached file7.md`
1. Now, we'll re-commit these changes without the extra file: `git commit -m "re-add file 5 and 6"`

> In this example, the tilde tells git we want to reset to two commits before the current location of `HEAD`. You can also use the first few characters of the commit ID to pinpoint the location where you would like to reset.

### Mixed reset

Next we will try the default mode of reset, `reset --mixed`:

1. Once again, we will start by viewing the history of our project: `git log --oneline`
1. Go back one commit in history: `git reset HEAD~`
1. See where the tip of the branch is pointing: `git log --oneline --decorate`
1. The changes we made in the last commit have been moved back to the working directory: `git status`
1. All the files still exist locally: `ls`
1. Move the files to the staging area before we can commit them: `git add file5.md file6.md`
1. Re-commit the files: `git commit -m "re-add file 5 and 6"`

> Notice that although we have essentially made the exact same commit (adding file 5 and 6 together with the same HEAD and commit message) we still get a new commit ID. This can help us see why the reset command should never be used on commits that have been pushed to the remote.

### Hard reset

Last but not least, let's try a hard reset.

1. Start by viewing the history of our project with: `git log --oneline`
1. Reset to the point in time when the only file that existed was the README.md: `git reset --hard <SHA>`
1. See that all the commits are gone: `git log --oneline`
1. Notice your working directory is clean: `git status`
1. See that the only files in your repository are the README.md and file7.md: `ls`

> **Warning:** Remember, `git reset --hard` overwrites your working directory, staging area, and history. This means that uncommitted changes you have made to your files will be completely lost. Don't use it unless you really want to discard your changes. Any files that are untracked will remain and be unchanged.