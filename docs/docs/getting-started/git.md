# Setting up Git

**Git** is an open source version control application. You will need git installed for this class.


## Installing git

### Windows

1. Download the latest Git for Windows installer from the [Git official website](https://git-scm.com/download/win).

2. When you've successfully started the installer, you should see the Git Setup wizard screen. Follow the Next and Finish prompts to complete the installation. The default options are pretty sensible for most users.

3. Open a Command Prompt (or Git Bash if during installation you elected not to use Git from the Windows Command Prompt).

4. Confirm that Git was properly installed by typing `git --version` into the command prompt.

```bash
git --version
```

### Mac

1. If you are on a Mac, you can download Git from Git official website or install it via Homebrew with the following command:

```bash
brew install git
```

2. Verify the installation was successful by typing git --version:

```bash
git --version
```

### Linux

#### Ubuntu / Debian

1. If you're on a Debian-based distribution like Ubuntu, try apt-get:

```bash
sudo apt-get update
sudo apt-get install git
```
#### Fedora

1. For Fedora systems, use dnf:

```bash
sudo dnf install git
```

## Testing your install

1. Confirm that Git was properly installed by typing `git --version`:

```bash
git --version
```

2. Next, try cloning a repository to make sure you can access GitHub:

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

> **Note:** If your clone is unsuccessful, read about [authenticating with GitHub from Git](https://docs.github.com/github/getting-started-with-github/set-up-git#next-steps-authenticating-with-github-from-git). 


## Configuring git

Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create. You can't create commits without these settings:

### Global configuration

If you are using a personal computer, apply the `--global` flag so you only have to set these settings once.

```sh
git config --global user.name "First-name Surname"
git config --global user.email "you@email.com"
```

### Local configuration

If you are using a computer without a private, personal account, don't apply the `--global` flag. This way, the settings will only be stored in your current repository. 

However, if you work in another repository on this same computer, you will need to set these configuration options again.

```sh
git config user.name "First-name Surname"
git config user.email "you@email.com"
```

> **Tip:** If you make a typo a when entering a property, you can delete the property with the following command:
>
> ```sh
> git config --global --unset <property_name>
> ```

### Handling Line Endings

Different systems handle line endings and line breaks differently. If you open a file created on another system and do not have this config option set, Git will think you made changes to the file based on the way your system handles this type of file.

- **Windows users:** `git config --global core.autocrlf true`
- **Mac users:** `git config --global core.autocrlf input`
