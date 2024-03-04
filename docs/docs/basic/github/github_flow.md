# What are Branching Strategies?

A branching strategy is a set of guidelines and practices that software development teams adopt to manage and structure their code changes using branches in Git.

Branching strategies are crucial for coordinating work among team members, enabling parallel development, and ensuring a smooth integration and deployment process. They help in organizing the codebase, minimizing conflicts during merges, and maintaining the stability of the main codebase while new features, fixes, or experiments are being developed.

## GitHub Flow

The GitHub flow is a lightweight workflow that allows developers to experiment with new ideas safely, without fear of compromising a project.

![GitHub Workflow](../../../img/github-workflow.png)

GitHub Flow emphasizes continuous delivery and consists of the following steps:

1. Anything in the main branch is deployable.
1. To work on something new, create a descriptively named branch off of the main branch.
1. Commit to that branch locally and regularly push your work to the same named branch on the server.
1. When you need feedback or help, or you think the branch is ready for merging, open a pull request.
1. After someone else has reviewed and signed off on the feature, you can merge it into the main branch.
1. Once merged, you can deploy the changes from the main branch immediately.

GitHub Flow is ideal for teams prioritizing a fast and continuous deployment cycle. It's simpler and more flexible but requires a disciplined approach to testing and deployment to ensure stability

### Branch Structure

The GitHub-flow approach is more linear and requires `main` to be deployable **at any point in time**.

Hotfixes, features, and bugs all go back to mainline, and bugs are communicated to consumers at the time of the changelog landing in mainline:

```mermaid
    gitGraph
       commit tag:"v1.0.0"
       branch hotfix-1
       checkout hotfix-1
       commit id: "Fixed checkout"
       checkout main
       merge hotfix-1 tag:"v1.0.1"
       branch feature-1
       commit id: "Added another button"
       commit id: "Bigger button"
       commit id: "Make button green"
       checkout main
       merge feature-1 tag:"v2.0.0"
```


Only one `main` branch acts as a safe reference, and everything else happens inside pull requests ("merge requests" in **GitLab**).

In GitHub-flow, the project moves with the merged patches, without any "going back" (except for reverts).

### Considerations

#### 1. Deployment

With GitHub-flow, one of the implications is that a patch should go live when we merge it. This means that deployment procedures will be stressed more, especially with humans involved.

It is endorsed to mitigate this via automation, but for that to happen reliably, the entire deployment should be automated, rather than just parts of it.

Switching to a previous stable release (rollback) in case of a failed deployment **must** also be automatic to avoid affecting production uptime in case of defects. If rollbacks are not viable, then some mitigation procedure (change reverting + re-deploy) is needed.

#### 2. Development

Because changes land directly in `main` in GitHub-Flow, the main advantage is that changes go live quicker: this allows developers to get faster feedback.

Instead of looking for the reason for a defect inside a release with a large `git diff`, we get a more precise idea of which changes broke some behavior.

#### 3. Release Naming

Because GitHub-flow encourages rolling releases, introducing a process that assigns artificial names to such releases is not necessary: the current git HEAD SHA1 usually suffices to pinpoint a release.

Past releases lose relevance too, as "what is currently live" becomes more important (as it should).

In order to satisfy the requirement for release management from stakeholders, it is possible to:

1.  Generate a report: GitHub **and** GitLab have such functionality, coupled with pull- and merge-requests
2.  Generate a release report in the issue tracker: could be as easy as a live query that shows which features landed and in which timeframe

## Choosing a Workflow

Now is a good time to discuss workflows - what works for you and your team, what might work, and what you've been doing in the past. Here are some topics you will want to discuss with your team as you establish your ideal process.  Have a conversation either synchronously or in issues in the class repository about different workflows.

1. Which branching strategy will we use?
1. Which branch will serve as our "main" or deployed code?
1. How will you protect your code?
1. Will we use naming conventions for our branches?
1. How will we use labels and assignees?
1. Will we use milestones?
1. Will we have required elements of Issues or Pull Requests (e.g. shipping checklists)?
1. Who is expected to review your work? Do you plan to involve other teams?
1. How will we indicate sign-off on Pull Requests?
1. Who will merge pull requests?
1. How will you teach your workflow to your team? If it already exists, how is it taught to new hires?
1. What integrations will be used in different stages of development? Will all teams be using the same tools?
1. If users have questions about Git, GitHub, or their workflows, who do they ask? How do they know who to ask?
