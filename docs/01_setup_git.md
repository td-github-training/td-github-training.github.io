### Setting up Git

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

#### Downloading and installing Git

If you don't already have Git installed, you can download Git at www.git-scm.com.

If you need additional assistance installing Git, you can find more information in [the ProGit chapter on installing Git](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### Where is your shell?

Now is a good time to create a shortcut to the command-line application you will want to use with Git:

- If you are working on Windows, we recommend `Git Bash` which is installed with the Git package, so that you can follow along with the facilitator who will be using Bash
- If you are working on macOS or another Unix-like system, you can use the built-in Terminal application

### Step 3: Try cloning with HTTPS

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

#### Proxy configuration

If your organization uses a proxy, you will need to configure the proxy settings in Git. Open Git Bash (on Windows) or Terminal (on Mac or \*nix) and complete the appropriate steps below:

**If your proxy does not require authentication:**

```sh
git config --global http.proxy https://YOUR.PROXY.SERVER:8080
```

Replace `YOUR.PROXY.SERVER` with your proxy's URL.

**If your proxy does require authentication:**

```sh
git config --global http.proxy https://YOUR_PROXY_USERNAME:YOUR_PROXY_PASSWORD@YOUR.PROXY.SERVER:8080
```

Replace `YOUR_PROXY_USERNAME` with the username used to authenticate into your proxy, `YOUR_PROXY_PASSWORD` with the password used to authenticate into your proxy, and `YOUR.PROXY.SERVER` with your proxy's URL.

### Step 4: Local Git configuration

In this section, we will prepare your local environment to work with Git.

#### Checking your Git version

First, let's confirm your [Git Installation](https://git-scm.com/downloads):

```sh
git version
```

If Git is installed, it will return your version: `git version 2.33.1`.

If you do not see a Git version listed or this command returns an error, you may need to install Git.

> To get the latest version of Git, visit [www.git-scm.com](https://www.git-scm.com).

#### Git configuration levels

Git allows you to set configuration options at three different levels.

##### --system

These are system-wide configurations. They apply to all users on this computer.

##### --global

These are the user level configurations. They only apply to your user account.

##### --local

These are the repository level configurations. They only apply to the specific repository where they are set.

> The default value for git config is `--local`.

#### Viewing your configurations

If you would like to see which config settings have been added automatically, you can type `git config --list`. This will automatically read from each of the three config files and list the setting they contain.

```sh
git config --list
```

You can also narrow the list to a specific configuration level by including it before the list option.

```sh
git config --global --list
```

#### Configuring your name and email address

Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create. You can't create commits without these settings:

```sh
git config --global user.name "First-name Surname"
git config --global user.email "you@email.com"
```

**Example:**

```sh
git config --global user.name "Mona Octocat"
git config --global user.email "mona@github.com"
```

> **Tip:** If you make a typo when setting one of your config properties, don't worry.  You can rerun the same `git config` command with different values between the double quotes to update the property to a new value.  If you typo a property name, you can delete the property with the following command:
>
> ```sh
> git config --global --unset <property_name>
> ```

##### Git config and your privacy

The instructions for this exercise use the `--global` flag when identifying your `user.name` and `user.email` configuration settings. If you are currently using a computer without a private, personal account, don't apply the `--global` flag. This way, the settings will only be stored in our assignment repository. If you work in another repository on this same computer, you will need to set these configuration options again.

> For example:
>
> ```sh
> git config user.email "you@email.com"
>```

Your name and email address will automatically be stored in the commits you make with Git. If you would like your email to remain private, GitHub allows you to generate a no-reply email address for your account. Click the **Keep my email address private** in the [Settings > Emails section](https://github.com/settings/emails). After enabling this feature, you just need to enter the automatically generated `ID+username@users.noreply.github.com` when configuring your email.

> For example:
>
> ```sh
> git config --global user.email 18249274+githubteacher@users.noreply.github.com
> ```

#### Configuring autocrlf

```sh
//for Windows users
git config --global core.autocrlf true

//for Mac or Linux users
git config --global core.autocrlf input
```

Different systems handle line endings and line breaks differently. If you open a file created on another system and do not have this config option set, Git will think you made changes to the file based on the way your system handles this type of file.

> Memory Tip: `autocrlf` stands for auto carriage return line feed.

### Step 5: Set up your text editor

For this class, we will use a basic text editor to interact with our code. Let's make sure you have one installed and ready to work from the command-line.

#### Pick your editor

You can use almost any text editor, but we have the best success with the following:

- [Visual Studio Code](https://code.visualstudio.com)
- Notepad
- Vi or Vim
- Sublime
- Notepad++
- GitPad

If you do not already have a text editor installed, go ahead and download and install one of the above editors now! You can also configure Visual Studio Code as your default text editor for Git commands using the [instructions at docs.github.com](https://docs.github.com/github/using-git/associating-text-editors-with-git).

#### Your editor on the command-line

After you have installed an editor, confirm you can open it from the command-line.

If installed properly, the following command will open the Visual Studio Code editor:

```sh
code .
```


```mermaid
graph LR
    A --- B
    B-->C[fa:fa-ban forbidden]
    B-->D(fa:fa-spinner);
```