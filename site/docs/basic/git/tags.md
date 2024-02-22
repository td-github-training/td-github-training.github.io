# What is a Tag?

## Tags vs Branches

Tags and branches serve different purposes in version control:

- **Branches** are for ongoing development, such as adding new features or fixing bugs. They allow separate lines of development without impacting the main codebase. After completing work on a branch, changes can be merged back into the main codebase.

- **Tags** mark specific points in the repository's history, indicating important milestones like releases. Unlike branches, tags are not intended for ongoing development but rather to reference specific points in the development timeline.

## When to use branches

- **Scenario:** Want to add a new feature or experiment without affecting the main codebase.
- **Use:** Create a Git branch to isolate development work from the main codebase. Merge back into the main branch after completing and testing the feature.

## When to use tags

- **Scenario:** Ready to release a new software version to users.
- **Use:** Apply a Git tag to mark the current state of the codebase as a new version release. Tag with a version number and brief description of changes for easy reference and rollback if needed.

> Additionally, using tags and branches in **CI/CD Pipelines** help to keep development organized and efficient for streamlined collaboration, automated testing, CI/CD integration, documentation, and visibility.