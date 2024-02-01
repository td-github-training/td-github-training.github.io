## Setting up GitHub

For this class, we will use a public account on GitHub.com

You can set up your free account by following these steps:

1. Access GitHub.com and click Sign up
1. Choose the free account
1. You will receive a verification email at the address provided
1. Click the link to complete the verification process

If you already have an account, verify that you can visit `github.com` within your organization's network.

---

## Setting up GitHub CLI
##### [**gh cli installation instructions**](https://github.com/cli/cli#installation) 

##### [**gh cli manual**](https://cli.github.com/manual/)
### Adding the GitHub CLI to your workflow can help you
* View, create, clone, and fork repositories
* Create, close, edit, and view issues and pull requests
* Review, diff, and merge pull requests
* Run, view, and list workflows
* Create, list, view, and delete releases
* Create, edit, list, view, and delete gists
* List, create, delete, and connect to a codespace
* Retrieve information from the GitHub API





<!-- To install the CLI under Ubuntu, we type the following: -->
<!-- 
```sh
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y

...

After this operation, 43.7 MB of additional disk space will be used.
Get:1 https://cli.github.com/packages stable/main amd64 gh amd64 2.42.1 [11.3 MB]
Fetched 11.3 MB in 1s (8181 kB/s)
Selecting previously unselected package gh.
(Reading database ... 61835 files and directories currently installed.)
Preparing to unpack .../archives/gh_2.42.1_amd64.deb ...
Unpacking gh (2.42.1) ...
Setting up gh (2.42.1) ...
Processing triggers for man-db (2.10.2-1) ...
``` -->

### Authenticate with a GitHub host

**Start interactive setup:**

```
gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: D042-4778
Press Enter to open github.com in your browser...
```

**You should see the following:**

![Alt text](docs/img/image-5.png)
![Alt text](docs/img/image-6.png)