# What is a Tag?

A tag is a reference that point to specific points in Git history. Tags are typically used to capture a point in history that is used for a marked version release (i.e., v1.0.0).

## Tags vs Branches

Tags and branches serve different purposes in version control:

- **Branches** are for ongoing development, such as adding new features or fixing bugs. They allow separate lines of development without impacting the main codebase. After completing work on a branch, changes can be merged back into the main codebase.

- **Tags** mark specific points in the repository's history, indicating important milestones like releases. Unlike branches, tags are not intended for ongoing development but rather to reference specific points in the development timeline.

### When to use branches

- **Scenario:** Want to add a new feature or experiment without affecting the main codebase.
- **Use:** Create a Git branch to isolate development work from the main codebase. Merge back into the main branch after completing and testing the feature.

### When to use tags

- **Scenario:** Ready to release a new software version to users.
- **Use:** Apply a Git tag to mark the current state of the codebase as a new version release. Tag with a version number and brief description of changes for easy reference and rollback if needed.

## Creating tags

To create a new tag, you can use the `git tag` command followed by the tag name:

```bash
git tag v1.0.0
```

This command creates a lightweight tag. Lightweight tags are simply pointers to specific commits.

## Creating annotated tags

If you want to include more information – such as the tagger name, email, and date – you can create an annotated tag. To do this, use the `-a` option:

```bash
git tag -a v1.0.0 -m "my version 1.0.0"
```

The `-m` option allows you to add a tagging message.

## Listing tags

To see all the tags in your repository, you can use the `git tag` command with no options:

```bash
git tag
```

**Output:**

```bash
v1.0.0
v1.0.1
v1.0.2
```

## Checking out tags

To checkout a specific tag, you can use the `git checkout` command followed by the tag name:

```bash
git checkout v1.0.0
```

This will put your repository in "detached HEAD" state, which means you're not on any branch.

Deleting a Tag
If you want to delete a tag, you can use the `-d` option followed by the tag name:

```bash
git tag -d v1.0.0
```

**Output:**

```bash
Deleted tag 'v1.0.0' (was f7d6a4f)
```

## Pushing tags

By default, when you push to a remote repository, tags are not included. To push tags to the remote repository, you can use the `--tags` option:

```bash
git push origin --tags
```

This will push all your tags to the remote repository.
