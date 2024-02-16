# GitHub's Learning Pathway for Enterpries Administration: 
### [Essentials of administration and governance with GitHub Enterprise Cloud](https://resources.github.com/learn/pathways/administration-governance/essentials/administration-governance-github-enterprise-cloud/)



## Enterprise Account Management


**Enterprise Accounts and Organizations:**  
Enterprise accounts centralize policy and billing management for multiple GitHub.com organizations. Billing is managed at the enterprise level, with organization settings remaining read-only.

**Continuity and Access:**  
Ensure project accessibility by appointing multiple owners with appropriate permissions.

**Best Practices for Enterprise Owners:**  
Maintain lean organizational structures and appoint multiple owners for redundancy. Grant enterprise owners organization owner privileges for comprehensive control.

**Administrative Settings:**  
Explore specific organization-level administrative settings for enhanced management efficiency and policy adherence.

In summary, efficient enterprise organization management is vital for seamless development operations. Adherence to best practices and utilization of available tools ensure streamlined processes.

Understanding GitHub's Organizational Structure
---
![alt text](<img/Screenshot 2024-02-16 at 3.16.19 PM.png>)

GitHub organizations were designed to keep companies separate, ensuring data privacy. However, when companies deploy GitHub Enterprise, they often misunderstand "organization" as synonymous with internal departments. The goal should be to consolidate all entities within one or two GitHub organizations.

### Guidance on consolidating organizations
**Teams help create structure**
- Teams facilitate communication and repository permissions within organizations. Leveraging nested teams enables representation of internal departments, promoting collaboration while maintaining a robust permissions model.

**Challenges of Multiple Organizations**
- Communication barriers arise with multiple organizations, hindering team mentions and cross-team collaboration. 
- Access to repositories becomes fragmented, discouraging collaboration and InnerSource practices.
- Manual administration predominates in GitHub organizations, complicating policy management across multiple entities. Streamlining permissions and operational procedures becomes challenging, necessitating a more cohesive approach.
- Managing permissions and onboarding/offboarding processes becomes cumbersome with multiple organizations. Efficient licensing management and monitoring of pay-per-use products are simplified with consolidated organizational structures.

<!-- 
### Streamlining a Consolidation Process

Empowering users to handle repository transfers and leveraging automation scripts expedites consolidation efforts. Strategic scoping and effective communication ensure a smooth transition.

**Migrations: Planning and Execution**

Meticulous planning and collaboration with developers are essential for successful migrations. Attention to detail is crucial, particularly for projects with intricate CI/CD integrations.

**Conclusion**

Consolidating organizations on GitHub demands strategic planning, effective communication, and meticulous execution. By adhering to best practices and leveraging available tools, developers can navigate the consolidation process efficiently. -->

# Repo Admins:

### Rolling Back Commits

- Sometimes, it's necessary to undo changes made in commits. Git provides several methods for rolling back commits:

### Reverting Commits

- Use `git revert <commit>` to create a new commit that undoes the changes introduced by the specified commit.
- This method keeps a record of the undo operation, preserving the history.

### Resetting Commits

- Use `git reset <commit>` to move the current branch to the specified commit.
- Be cautious with this command as it can alter history. Use `--hard` to discard changes, `--soft` to keep changes staged, and `--mixed` to keep changes in the working directory.

## Using Filter-Branch

`git filter-branch` allows rewriting the repository history by applying custom filters. It's useful for tasks like removing sensitive data or reorganizing commits.

### Example Usage

- Remove a file from all commits: `git filter-branch --tree-filter 'rm -f <file>' HEAD`
- Change author email in all commits: `git filter-branch --commit-filter 'if [ "$GIT_AUTHOR_EMAIL" = "old@email.com" ]; then GIT_AUTHOR_EMAIL="new@email.com"; fi; git commit-tree "$@"' HEAD`

## Git Large File Storage (Git LFS)

Git LFS is an extension for Git that deals with large files by storing them outside the repository, while still keeping track of their versions.

### What is Git LFS (end-user)?

- Git LFS allows seamless handling of large files (>100 MB) within Git repositories.
- It replaces large files with tiny pointer files, reducing repository size and improving performance.
- End-users can work with large files as if they were normal Git-managed files.

### How to Setup Git LFS

1. Install Git LFS by downloading the installer from the [Git LFS website](https://git-lfs.github.com/).
2. Navigate to your Git repository and run `git lfs install` to initialize Git LFS.
3. Track large files using `git lfs track <pattern>` where `<pattern>` is a wildcard pattern matching the large files.
4. Commit and push changes as usual. Git LFS will handle large files transparently.

## Secret Management

Managing secrets, such as API keys or passwords, within a repository requires caution to prevent accidental exposure.

### Best Practices

- **Avoid storing secrets in code:** Instead, use environment variables or dedicated secret management tools.
- **Encrypt secrets:** If storing secrets in the repository is unavoidable, encrypt them before committing.
- **Restrict access:** Limit access to sensitive files using Git's access control features or repository hosting platform permissions.