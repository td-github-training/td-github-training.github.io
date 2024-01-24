## Using Commits

A git commit is a core function in Git that captures a snapshot of the changes made to the files in a project at a specific point in time. This operation sends the latest changes of the source code to the local repository, making these changes part of the head revision of the repository.

### The two stage commit

When you work locally, your files exist in one of four states. They are either untracked, modified, staged, or committed.

![The Two Stage Commit - Part 1](./img/two-stage-commit-a.png ':size=50%')

An untracked file is a new file that has never been committed.

Git tracks these files, and keeps track of your history by organizing your files and changes in three working trees. They are Working, Staging (also called Index), and History. When we are actively making changes to files, this is happening in the working tree.

![The Two Stage Commit - Part 2](./img/two-stage-commit-b.png ':size=50%')

To add these files to version control, you will create a collection of files that represent a discrete unit of work. We build this unit in the staging area.

![The Two Stage Commit - Part 3](./img/two-stage-commit-c.png ':size=50%')

When we are satisfied with the unit of work we have assembled, we will take a snapshot of everything in the staging area. This is called a commit.

![The Two Stage Commit - Part 4](./img/two-stage-commit-d.png ':size=50%')

In order to make a file part of the version controlled directory we will first do a `git add`, and then we will do a `git commit`. Let's do it now.

1. First, let's check the status of our working tree: `git status`
1. Move the file from the working tree to the staging area: `git add my-file.md`
1. Let's see what happened: `git status`
1. Now let's take our first snapshot: `git commit`
1. Git will open your default text editor to request a commit message. Simply type your message on the top line of the file. Any line without a # will be included in the commit message.
1. Save and close the commit message
1. Let's take another look at our repository status: `git status`
