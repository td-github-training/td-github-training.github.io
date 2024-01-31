<!-- ## Setting up GitHub

For this class, we will use a public account on GitHub.com

You can set up your free account by following these steps:

1. Access GitHub.com and click Sign up
1. Choose the free account
1. You will receive a verification email at the address provided
1. Click the link to complete the verification process

If you already have an account, verify that you can visit `github.com` within your organization's network.

---

## Setting up GitHub CLI

### Why?

### Installation

The GitHub CLI installation instructions can be found here: [cli/cli: GitHub’s official command line tool](https://github.com/cli/cli#installation) 

To install the CLI under Ubuntu, we type the following:

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
```

### Authentication

GitHub CLI can be used with both GitHub Enterprise Cloud and GitHub Enterprise Server.

To use `gh cli` with GHEC, we have to do the following:

```sh
gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: D042-4778
Press Enter to open github.com in your browser...
```

![](images/Pasted%20image%2020240123181402.png)

Click `Authorize`:

![](images/Pasted%20image%2020240123181450.png)

After authenticating, click `Authorize github`:

![](images/Pasted%20image%2020240123181542.png)

You should see the following:

![](images/Pasted%20image%2020240123181613.png)

And your terminal should show the following:

```sh
✓ Authentication complete.
- gh config set -h github.com git_protocol https
✓ Configured git protocol
! Authentication credentials saved in plain text
✓ Logged in as im-sampm
```

You're all set! -->