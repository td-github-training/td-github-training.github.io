## What is a Repository?

A Git repository is a centralized location that stores a collection of files along with their revision history. It is a crucial component of the Git version control system, which enables collaborative development and allows multiple developers to work on a project simultaneously. Each developer maintains a local copy of the entire repository, including all files and their complete history, enabling seamless offline work and efficient merging of changes at a later stage. 

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