# Pull Requests

PRs are used to propose changes to the git commit history. A pull request introduces an action that could address an Issue or other change. A Pull Request is considered a work in progress until it is merged into the target branch.

## Creating a PR

TBD

## PR templates

To enhance the **clarity** of pull requests, it's essential to provide a comprehensive checklist of relevant information regarding the proposed code changes. Instead of relying solely on a single-line summary, consider including details such as:

-   **Bug Fix Description:** Explain how the bug was addressed and provide a description of the solution.

-   **New Feature Summary:** Offer a summary or description of any new features being introduced.

-   **Unit Test Coverage:** Outline the unit test cases covered to ensure code reliability.

-   **Impact on Existing Functionalities:** Indicate whether the code changes have any impact on existing functionalities.

-   **Testing Details:** Provide information about the testing procedures conducted.

-   **Cross-Device and Browser Testing:** Specify whether the code was tested across different devices and browsers.

These checklists can be automatically populated in the description field every time a new pull request is made through **PR Templates**!

If your project repository is on GitHub, the name of the template and where it's located in your repository matters a lot. The template created as a Markdown file should be named `PULL_REQUEST_TEMPLATE.md` by default and placed in either the project's root folder, the `PULL_REQUEST_TEMPLATE` folder if you are saving multiple templates or the `.github` directory.

Create a Markdown file, name it `PULL_REQUEST_TEMPLATE.md`, and place it in the project's root folder.

![alt text](../../../img/image-20.png)

*NOTE: Make sure to place the Markdown file within one of the previously mentioned locations and save and merge it with the same name.*

Now, when you create a new pull request, you will see the template content automatically loaded into the description field as shown in the following image.

![alt text](../../../img/image-19.png)

### Creating an Issue
**1.** Navigate to the Issues tab

**2.** Click on New Issue

**3.** Get started with the Error Issue Template which will have prompts

**4.** Copy the below formatting:
> <img width="1253" alt="Screenshot 2024-01-26 at 1 35 22 PM" src="img/image-14.png">

**5.** Assign Yourself to the issue

**6.** Label issue as a bug

**7.** Submit the issue

## Working on the Issue on GitHub
**1.** On your new issue under "Development", click `create a branch`

**2.** Click on the README.md file on your new branch

**3.** Click on the pencil in the top right to open the editor

**4.** Change the filename to README.**md**

**5.** Commit directly to your branch


## Creating a Pull Request
Now that you have started to change your file, you will open a pull request to discuss the file with your team mates. Follow these steps to create a Pull Request in the class repository:

**1.** Click the *Pull Request* tab.

**2.** Click *New Pull Request*.

**3.** In the *base* dropdown, choose `main`

**4.** In the *compare* dropdown, choose the branch you just committed.

**5.** Type a subject line and enter a concise description.

**6.** Enter the description as `fixes #1` to tag it to the issue

**6.** Click *Preview* to see how your Pull Request will look.

**7.** Assign the Pull Request to yourself.

**8.** Select the instructor as a reviewer on the PR.

**9.** Click on *Create pull request*.

> When you navigate to the class repository, you should see a banner at the top of the page indicating you have recently pushed branches, along with a button that reads *Compare & pull request*. This helpful button will automatically create a pull request between your branch and `main` as well.

If everything looks good we will start to merge!

## Merging Your Pull Request

When you merge your branch, you are taking the content and history from your feature branch and adding it to the content and history of the `main` branch.

![image](../../../img/image-15.png)

Many project teams have established rules about who should merge a pull request.

- Some say it should be the person who created the pull request since they will be the ones to deal with any issues resulting from the merge.
- Others say it should be a single person within the project team to ensure consistency.
- Still others say it can be anyone other than the person who created the pull request to ensure at least one review has taken place.

> GitHub offers three different merge strategies for Pull Requests:

- **Create a merge commit:** This is the traditional option that will perform a standard recursive merge. A new commit will be added that shows the point when the two branches were merged together.
- **Squash and merge:** This option will take all of the commits on your branch and compress them into a single commit. The commit messages will be preserved in the extended commit message for the commit, but the individual commits will be lost.
- **Rebase and merge:** This option will take all of the commits and replay them as if they just happened. This allows GitHub to perform a fast forward merge (and avoids the addition of the merge commit).

### Let's take a look at how you can merge the pull request.

**1.** Navigate to your Pull Request (HINT: Use the Author or Assignee drop downs to find your Pull Request quickly)

**2.** Click *Conversation*

**3.** Scroll to the bottom of the Pull Request and click the *Merge pull request* button

**4.** Click *Confirm merge*

**5.** Click *Delete branch*
> Your issue will be closed through the link created with the `fixes` keyword.


## Updating Your Local Git Repository

When you merged your Pull Request, you deleted the branch on GitHub, but this will not automatically update your local copy of the repository. Let's go back to our command line application and get everything in sync.

First, we need to get the changes we made on GitHub into our local copy of the repository:

**1.** Start by switching back to your default branch: `git switch main`

**2.** Retrieve all of the changes from GitHub: `git pull`

> `git pull` is a combination command that retrieves all of the changes from GitHub and then updates the branch you are currently on to include the changes from the remote. The two separate commands being run are `git fetch` and `git merge`. `git fetch` is a primary command used to download contents from a remote repository, and `git merge` joins two or more development histories together.


## Cleaning Up the Unneeded Branches

If you type `git branch --all` you will probably see that even though you deleted your branch on the remote, it is still listed in your local copy of the repository, both as a local branch and as a read-only remote tracking branch. 

**Let's get rid of those extra branches.**

**1.** Take a look at your local branches: `git branch --all`

**2.** Let's see which branches are safe to delete: `git branch --merged`

**3.** Delete the local branch: `git branch -d <branch-name>`

**4.** Take another look at the list: `git branch --all`

**5.** Your local branch is gone but the remote tracking branch is still there. Delete the remote tracking branch: `git pull --prune`


> Adding the `--merged` option to the `git branch` command allows you to see which branches **do not contain unique work** when compared to the checked out branch. In this case, since we are checked out to main, we will use this command to ensure all of the changes on our feature branch have been merged to production before we delete the branch.

If you would like pruning of the remote tracking branches to be set as your default behavior when you pull, you can use the following configuration option: `git config --global fetch.prune true`. 


[include](07a_activity_create_pull_request.md ':include')

## Exploring a pull request

Now that we have created a Pull Request, let's explore a few of the features that make Pull Requests the center of collaboration:

### ![octicon-comment-discussion] Conversation tab

Similar to the discussion thread on an Issue, a Pull Request contains a discussion about the changes being made to the repository. This discussion is found in the **Conversation** tab and also includes a record of all the commits made on the branch as well as assignments, labels and reviews that have been applied to the pull request.

### ![octicon-git-commit] Commits tab

The **Commits** tab contains more detailed information about who has made changes to the files. Clicking each commit ID will allow you to see the changes applied in that specific commit.

### ![octicon-diff] Files changed tab

The **Files changed** tab allows you to see cumulative effect of all the changes made on the branch. We call this the `diff`. Our diff isn't very interesting yet, but as we make changes your diff will become very colorful.

## Code review in pull requests

To provide feedback on proposed changes, GitHub offers three levels of commenting:

### General conversation

You can provide general comments on the Pull Request within the **Conversation** tab.

### Line comments

In the **Files changed** tab, you can hover over a line to see a blue ![`+`][octicon-diff-added] icon. Clicking this icon will allow you to enter a comment on a specific line. These line level comments are a great way to give additional context on recommended changes. They will also be displayed in the **Conversation** tab.

### Review

When you are making line comments, you can also choose to **Start a Review**. When you create a review, you can group many line comments together with a general message: Comments, Approve, or Request Changes. Reviews have special power in GitHub when used in conjunction with protected branches.

## Activity: Code review

One of the best ways to ensure code quality is to make peer reviews a part of every Pull Request. Let's review your partner's code now:

1. Click the **Pull Request** tab.
1. Use the **Author** drop down to locate your partner's pull request.
1. Click the **Files Changed** tab.
1. Hover over a single line in the file to see the blue +. Click the + to add a line comment.
1. Comment on the line and click **Start a review**.
1. Add additional line comments to the pull request.
1. Click **Review changes** in the top right corner.
1. Choose whether to **Approve** or **Request changes**
1. Enter a general comment for the review.
1. Click **Submit review**
1. Click the **Conversation** tab to check out your completed review.

[octicon-comment-discussion]:https://unpkg.com/octicons/build/svg/comment-discussion.svg

[octicon-diff]:https://unpkg.com/octicons/build/svg/diff.svg

[octicon-diff-added]: https://unpkg.com/octicons/build/svg/diff-added.svg

[octicon-git-commit]:https://unpkg.com/octicons/build/svg/git-commit.svg

---

# Merging pull requests

Now that you have made the requested changes, your pull request should be ready to merge.

## Merge explained

When you merge your branch, you are taking the content and history from your feature branch and adding it to the content and history of the `main` branch.

![Merging Pull Requests](../../../img/merging-prs.png)

Many project teams have established rules about who should merge a pull request.

- Some say it should be the person who created the pull request since they will be the ones to deal with any issues resulting from the merge.
- Others say it should be a single person within the project team to ensure consistency.
- Still others say it can be anyone other than the person who created the pull request to ensure at least one review has taken place.

This is a discussion you should have with the other members of your team.

## Merging your pull request

Let's take a look at how you can merge the pull request:

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

### Working on a PR means that:
1. A developer works on their contribution in a fork (clone) of the central repository.
2. Once finished, they create a PR to notify the appropriate teams of changes.
3. Code review passes along with status checks before merging.
4. Merge the PR

**A few Considerations**
- *PRs encourage wider code review adoption*.
- *Continuous refinement through iteration is crucial and we do so with a Pull Request*.
- *PRs are not the only means for code reviews, but are central to GitHub's review process*.

**Benefits of Pull Requests:**

- **Streamlined Collaboration:** PRs facilitate seamless collaboration where contributors can propose changes on their own branch, ensuring a clean and working history.

- **Clear Communication:** Pull requests provide a structured platform for discussing proposed changes. Through comments and discussions within the pull request thread while the contributor can still push commits into the PR.

- **Code Review:** PRs on GitHub are a helpful utility for code reviews. Before merging changes into the main repository, contributors submit their pull requests for review by codeowners for open-ended quality assurance.

- **Automated Testing and CI/CD Integration:** GitHub integrates seamlessly with various continuous integration (CI) and continuous deployment (CD) tools, integrating with GitHub Actions for processes to run like linting, and status checks for test cases on the code that is pushed into a PR.

- **Documentation and Visibility:** Pull requests serve as a valuable documentation tool, capturing the rationale behind code changes, discussions, and decisions made during the development process.

Downsides of this workflow might be:
- Pull requests introduce an additional step in the integration process.
- Code review process can sometimes lead to delays.
- Continuous integration may face challenges when PRs become a bottleneck.

## PR Best Practices (PRBP's)

**Why Context on A Pull Request Matters**

Context is the guiding light that allows developers to swiftly navigate pull requests. When it comes to enhancing both the speed and quality of pull-request reviews, there is a golden best practice: **provide as much upfront context as possible to the reviewer.**

Consider these proven strategies for boosting pickup time:

- **Estimated Review Time:** Labeling pull requests with an estimated review time (ETR) is a game-changer. Whether it's 5 minutes or 60, providing this insight empowers developers to work lean.
  
- **Risk Identification:** Differentiating between low-risk changes (e.g., Documentation or Test changes only) and high-risk changes (e.g., Core services, API Database, or Security) offers invaluable clarity.
  
- **Integration Links:** Including ticket or issue links alongside pull requests streamlines understanding and collaboration.
  
- **Test-Coverage Impact:** Highlighting test-coverage impact helps reviewers gauge the impact of proposed changes.

So, what's the magic of adding an ETR to pull requests? It's simple: when developers know how long a review might take – whether it's a short 5 minutes or a more involved 60 – they're more likely to pick up the request promptly and complete their reviews efficiently.

**The Psychology Behind Swift Reviews**

Developers aren't just code machines; they're knowledge workers. By incorporating estimated review times, we cater to their cognitive biases. Here's why it works:

- **Optimal Scheduling:** Knowing the expected review time allows reviewers to schedule their reviews strategically, minimizing interruptions and maximizing focus.
  
- **Avoiding Cognitive Reload:** Starting a review and then getting interrupted can lead to cognitive reload, forcing reviewers to start from scratch therefore prolonging the review process.
  
- **Maintaining Quality:** Rushing through a review due to time constraints can *compromise quality*. By providing clear expectations upfront, we mitigate the risk of rushed reviews and ensure thorough evaluations.
