## What is a Repository?

A repository is the most basic element of GitHub. It is easiest to imagine as a project's folder. However, unlike an ordinary folder on your laptop, a GitHub repository offers simple yet powerful tools for collaborating with others.

### Repository Tabs

- **Code**
    - The **Code** tab is where you will find the files included in the repository. These files may contain the project code, documentation, and other important files. We also call this tab the root of the project. Any changes to these files will be tracked via Git version control.
- **Issues**
    - Issues are used to track bugs and feature requests. Issues can be assigned to specific team members and are designed to encourage discussion and collaboration.

#### Pull requests

A Pull Request represents a change, such as adding, modifying, or deleting files, which the author would like to make to the repository. Pull Requests help you write better software by facilitating code review and showing the status of any automated tests.

#### Projects

Projects allow you to visualize your work with Kanban style boards. Projects can be created at the repository or organization level.

#### Wiki

Wikis in GitHub can be used to communicate project details, display user documentation, or almost anything your heart desires. And of course, GitHub helps you keep track of the edits to your Wiki!

### Repository Best Practices

#### README.md

The README.md is a special file that we recommend all repositories contain. GitHub looks for this file and helpfully displays it below the repository. The README should explain the project and point readers to helpful information within the project.

#### CONTRIBUTING.md

The CONTRIBUTING.md is another special file that is used to describe the process for collaborating on the repository. The link to the CONTRIBUTING.md file is shown when a user attempts to create a new issue or pull request.

#### ISSUE_TEMPLATE.md

The ISSUE_TEMPLATE.md (and its twin the pull request template) are used to generate templated starter text for your project issues. Any time someone opens an issue, the content in the template will be pre-populated in the issue body.

---

## Configure Git to ignore files

While working within your repository, you might notice system or configuration files created by your operating system or text editor. These files are typically things that you don't want git to track or include in the history of your project. Although you can manually ignore those files by never committing them to the history of the project, there is an easier way for you to ignore those files. Git enables you to ignore specific files, files types, and folders through the use of a text file you can add to your repository titled `.gitignore`. This file instructs Git to stop tracking changes of certain files, which means that these files will not be pushed to GitHub from your local machine.

**Example files that you might want Git to ignore:**

1. Secrets, e.g. `*.pem`, `*.key`
1. Binary files, e.g. `*.pdf`, `*.docx`
1. Log files, e.g. `*.log`
1. Build files, e.g. `Build/*`

### Readily available `.gitignore` templates

#### github/gitignore

The [github/gitignore repository](https://github.com/github/gitignore) is a collection of `.gitignore` templates based on popular programming languages.

For example, the following snippet shows some suggested files you should start ignoring in a Python project.

![python-gitignore](img/python-gitignore.png ':size=60%')

These templates are also available when you create a new repository:

![create-gitignore-repo](img/gitignore-create-repo.png ':size=60%')

#### gitignore.io

[This website](https://www.toptal.com/developers/gitignore) is another resource for you to find appropriate `.gitignore` templates when your project contains multiple programming languages.

### Activity: Creating a `.gitignore` file

#### Ignore files for a single repository

1. In your Terminal or Git Bash, `cd` to a repository of interest and create a `.gitignore` file:

   ```sh
   touch .gitignore
   ```

   For Windows users who are not using a bash-based terminal:

   ```sh
   echo >> .gitignore
   ```

1. Go to `github/gitignore` and choose a template of your choice and paste it in the file.

1. To share the gitignore rules with other users who clone the repository, commit the `.gitignore` file to your repository.

   ```sh
   git add .gitignore
   git commit -m "add gitignore file"
   ```

#### Ignore files for all repositories on your local machine

1. You can also create a global `.gitignore` file to define a list of rules for ignoring files in every local Git repository.

   To do this, you should be in your root directory:

   ```sh
   touch .gitignore_global
   ```

1. Let's grab [an example `.gitignore` template](https://gist.github.com/octocat/9257657) and paste it in the file:

   ```md
   # Compiled source #
   ###################
   *.com
   *.class
   *.dll
   *.exe
   *.o
   *.so

   # Packages #
   ############
   # it's better to unpack these files and commit the raw source
   # git has its own built in compression methods
   *.7z
   *.dmg
   *.gz
   *.iso
   *.jar
   *.rar
   *.tar
   *.zip

   # Logs and databases #
   ######################
   *.log
   *.sql
   *.sqlite

   # OS generated files #
   ######################
   .DS_Store
   .DS_Store?
   ._*
   .Spotlight-V100
   .Trashes
   ehthumbs.db
   Thumbs.db
   ```

1. Configure `git` to use this file:

   For Mac Users:

   ```sh
   git config --global core.excludesfile ~/.gitignore_global
   ```

   For Windows Users:

   ```sh
   git config --global core.excludesfile %USERPROFILE%\.gitignore_global
   ```


---

### Creating Repositories

#### GitHub Web

- New Repository
	- Initialize repo using GitHub.com UI
	- Follow instructions on GitHub.com to create new repo and push
- Existing source code via GitHub.com UI
	- Initialize repo locally
	- Create repo using GitHub.com UI
	- Follow instructions on GitHub.com to push existing repo

#### GitHub CLI

- Existing source code via GitHub CLI
	- Initialize repo locally
	- Use `gh repo` to create repo and push code from current directory
- Existing repo on GitHub.com
	- `git clone` to local directory
