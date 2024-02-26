# What is a Pull Request?

A pull request is a proposal to merge a set of changes from one **branch** into another **branch** within a repository or a repository fork.   

<center>

![Merging Pull Requests](../../../img/merging-prs.png ':size=450px')

</center>

## Navigating a pull request

In a pull request, collaborators can review and discuss the proposed set of changes before they integrate the changes into the main codebase. Pull requests display the differences, or diffs, between the content in the source branch and the content in the target branch.

![octicon-comment-discussion] **Conversation**

Similar to the discussion thread on an Issue, a Pull Request contains a discussion about the changes being made to the repository. This discussion is found in the **Conversation** tab and also includes a record of all the commits made on the branch as well as assignments, labels and reviews that have been applied to the pull request.

![octicon-git-commit] **Commits**

The **Commits** tab contains more detailed information about who has made changes to the files. Clicking each commit ID will allow you to see the changes applied in that specific commit.

![octicon-diff] **Files changed**

The **Files changed** tab allows you to see cumulative effect of all the changes made on the branch. We call this the `diff`. Our diff isn't very interesting yet, but as we make changes your diff will become very colorful.

## Creating a pull request

> **Note:** A pull request is used to propose changes _between_ **branches**, so first create a branch and make some changes.

1. Click the *Pull Request* tab.
2. Click *New Pull Request*.
3. In the *base* dropdown, choose `main`
4. In the *compare* dropdown, choose the branch containing your changes.
5. Click *Create Pull Request*.
6. Enter a subject line and a concise description.
7. Select an assignee for the Pull Request.
8. Select a reviewer for the Pull Request.
9. Click on *Create pull request*.

## Reviewing a pull request

To provide feedback on proposed changes, GitHub offers three levels of commenting:

1. **General conversation**

  You can provide general comments on the Pull Request within the **Conversation** tab.

2. **Line comments**

  In the **Files changed** tab, you can hover over a line to see a blue ![`+`][octicon-diff-added] icon. Clicking this icon will allow you to enter a comment on a specific line. These line level comments are a great way to give additional context on recommended changes. They will also be displayed in the **Conversation** tab.

3. **Review**

  When you are making line comments, you can also choose to **Start a Review**. When you create a review, you can group many line comments together with a general message: Comments, Approve, or Request Changes. Reviews have special power in GitHub when used in conjunction with protected branches.


## Merging a pull request

When you merge a feature branch, you are taking the content and history from the feature branch and adding it to the content and history of the `main` branch.


1. Navigate to your Pull Request

   ?> **Hint:** Use the Author or Assignee drop-downs to find your pull request quickly

1. Click **Conversation**
1. Scroll to the bottom of the Pull Request and click the **Merge pull request** button
1. Click **Confirm merge**
1. Click **Delete branch**
1. Click **Issues** and confirm your original issue has been closed

GitHub offers three different merge strategies for pull requests:

- **Create a merge commit**

  This is the traditional option that will perform a standard recursive merge. A new commit will be added that shows the point when the two branches were merged together.

- **Squash and merge**

  This option will take all the commits on your branch and compress them into a single commit. The commit messages will be preserved in the extended commit message for the commit, but the individual commits will be lost.

- **Rebase and merge**

  This option will take all the commits and replay them as if they just happened. This allows GitHub to perform a fast-forward merge (and avoids the addition of the merge commit).