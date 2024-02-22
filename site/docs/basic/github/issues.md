# What is an Issue?

In GitHub, you will use issues to record and discuss ideas, enhancements, tasks, and bugs. Issues make collaboration easier by:

- Replacing email for project discussions, ensuring everyone on the team has the complete story, both now and in the future.
- Allowing you to cross-link to related issues and pull requests.
- Creating a single, comprehensive record of how and why you made certain decisions.
- Allowing you to easily pull the right people into a conversation with @ mentions and team mentions.

<!-- [include](02a_activity_create_github_issue.md ':include') -->
<p align="center">
  <img src="img/issue-tasks-progress-reduced-motion-d920d5bbc273.png" alt="code" width="440"/>
</p>

[GitHub Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/quickstart-for-projects) and Issues
---
<p align="center">
  <img src="img/ezgif-5-f7a61cf113.jpg" alt="code" width="600"/>
</p>

GitHub Projects allow teams to organize their work into boards, where issues represent tasks, bugs, features, or enhancements. Each card on the board typically corresponds to an issue, providing a visual representation of the project's progress.


#### Features of GitHub Projects with Issues:
- Tailor your project's table/board layout, and include statuses of tasks that are then automatically tracked on GitHub through Todo-InProgress-Done status 

- Save different tabs to navigate to specific project aspects of interest, facilitating seamless workflow management.
   
- Open draft issues directly from your project table or board to integrate new tasks seamlessly.

## How to write effective GitHub Issues


### Avoid Duplication

The first step in writing a GitHub issue is to utilize the search feature to ensure that a similar issue doesn't already exist. In instances of duplicate issues, one should be closed, and this is typically the less detailed issue. 
    
- Ensure that the closing comment contains a link to the remaining open issue (e.g., "Duplicate of #123") and that any relevant details from the closed issue are consolidated into the open one.

### One Issue per Issue

It's essential to avoid combining multiple topics into a single issue. Each bug or feature request should be documented in its own issue.

- **Bad:** "The form needs a subject field. Also, the submit button is broken."
  (Separate these into two issues.)
- **Good:** "Add a subject field to form"
- **Good:** "Submit button causes 405 error"

While some issues may be complex, particularly with significant feature requests, it's beneficial to separate them into multiple issues whenever possible.

**Keep issue titles concise**, descriptive, and compelling.

**Markdown** is a simple way to style text on GitHub, making well-formatted issues easier to read and understand.

#### Writing and Formatting Markdown

Markdown is a lightweight and easy-to-use syntax for styling all forms of writing on the GitHub platform. [Learn more about Markdown](https://guides.github.com/features/mastering-markdown/).

- **Links:** Include links to specific application views being described.
- **Screenshots:** Utilize screenshots to clarify the observed issue.
- **@ Mention:** If specific users within your organization need to be alerted, mention them in the issue.

### Objectivity

A well-defined issue avoids speculation and opinion. When reporting bugs, provide thorough descriptions and refrain from assuming the cause. For feature requests, focus on describing the problem rather than prescribing a solution.

- **Bad:** "Make the button red."
- **Good:** "Users don't understand that deletion is irreversible."

Avoid hypothetical scenarios unless backed by a genuine need, reinforcing the use of user stories.

### Reproduction Steps

When logging a bug, provide **clear** instructions to reproduce it. Simplify the steps and verify their reliability.

Be precise in instructions; for example, instead of "enter text in the search input," specify the exact text causing the error.


> Many GitHub projects also offer [issue templates!](https://github.com/stevemao/github-issue-templates)
