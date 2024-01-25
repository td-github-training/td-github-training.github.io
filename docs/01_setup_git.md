## Setting up Git

Git is an open source version control application. You will need Git installed for this class.

You may already have Git installed so let's check! Open Terminal if you are on a Mac, or PowerShell if you are on a Windows machine, and type:

```sh
git version
```

You should see something like this:

```shell-session
$ git version
git version 2.33.1
```

In general, we recommend you stay within two minor versions of the [latest version](https://git-scm.com/downloads) of Git. The minor version is the second number in the series `x.x.x`.

We suggest having version [2.29.2](https://github.com/git-for-windows/git/releases/tag/v2.29.2.windows.2) or more recent if you're using Git for Windows or Git Bash.

### Installing Git

If you don't already have Git installed, you can download Git at www.git-scm.com.

#### Opening Your Shell

- If you are working on Windows, we recommend `Git Bash` which is installed with the Git package, so that you can follow along with the facilitator who will be using Bash
- If you are working on macOS or another Unix-like system, you can use the built-in Terminal application

#### Testing Your Install

Open your chosen shell, and type:

```sh
git clone https://github.com/githubschool/scratch.git
```

If the clone is successful you'll see:

```shell-session
$ git clone https://github.com/githubschool/scratch
Cloning into 'scratch'...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
```

If your clone is unsuccessful, read about [authenticating with GitHub from Git](https://docs.github.com/github/getting-started-with-github/set-up-git#next-steps-authenticating-with-github-from-git). Please note: many corporate networks restrict SSH traffic, so we highly recommend using HTTPS and verifying the clone works before class. Also, if you have two-factor authentication enabled and wish to use HTTPS, you will need to [set up a personal access token](https://docs.github.com/github/authenticating-to-github/accessing-github-using-two-factor-authentication#using-two-factor-authentication-with-the-command-line).

### Configuring Git

Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create. You can't create commits without these settings:

```sh
git config --global user.name "First-name Surname"
git config --global user.email "you@email.com"
```

Different systems handle line endings and line breaks differently. If you open a file created on another system and do not have this config option set, Git will think you made changes to the file based on the way your system handles this type of file.

```sh
//for Windows users
git config --global core.autocrlf true

//for Mac or Linux users
git config --global core.autocrlf input
```

> **Tip:** If you make a typo when setting one of your config properties, don't worry.  You can rerun the same `git config` command with different values between the double quotes to update the property to a new value.  If you typo a property name, you can delete the property with the following command:
>
> ```sh
> git config --global --unset <property_name>
> ```