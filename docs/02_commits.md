## What is a Commit?

A Git commit is a core function in Git that captures a snapshot of the changes made to the files in a project at a specific point in time. This operation sends the latest changes of the source code to the local repository, making these changes part of the head revision of the repository.

### The two stage commit

When you work locally, your files exist in one of four states. They are either untracked, modified, staged, or committed.

![The Two Stage Commit - Part 1](./img/two-stage-commit-a.png ':size=50%')

An untracked file is a new file that has never been committed.

Git tracks these files, and keeps track of your history by organizing your files and changes in three working trees. They are Working, Staging (also called Index), and History. When we are actively making changes to files, this is happening in the working tree.

![The Two Stage Commit - Part 2](./img/two-stage-commit-b.png ':size=50%')

To add these files to version control, we use `git add`, which creates a collection of files that represent a discrete unit of work. We build this unit in the staging area.

![The Two Stage Commit - Part 3](./img/two-stage-commit-c.png ':size=50%')

When we are satisfied with the unit of work we have assembled, we create a commit using `git commit`, which will take a snapshot of everything in the staging area.

![The Two Stage Commit - Part 4](./img/two-stage-commit-d.png ':size=50%')

---

### Using Git log

When you clone a repository, you receive the history of all the commits made in that repository. The log command allows us to view that history on our local machine.

Let's take a look at some option switches you can use to customize your view of the project history. You can find these options, and many more, on [git-scm.com](https://git-scm.com/docs/git-log). _(Note: `--graph` is default on most Git Bash for Windows terminals.)_

```sh
git log
git log --oneline
git log --oneline --graph
git log --oneline --graph --decorate
git log --oneline --graph --decorate --all
git log --stat
git log --patch
```

> Use the up and down arrows or press enter to view additional log entries. Type `q` to quit viewing the log and return to the command prompt.
