# Setting up Git

**Git** is an open source version control application. You'll need git installed for this class.


## Installing git

### Windows

1. Download the latest Git for Windows installer from the [Git official website](https://git-scm.com/download/win).

2. When you've successfully started the installer, you should see the Git Setup wizard screen. Follow the Next and Finish prompts to complete the installation. The default options are pretty sensible for most users.

### Mac

1. If you are on a Mac, you can download Git from Git official website or install it via Homebrew with the following command:

```bash
brew install git
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

1. Open a Command Prompt (or Git Bash if during installation you elected not to use Git from the Windows Command Prompt).

2. Confirm that Git was properly installed by typing `git --version` into the command prompt.

```bash
git --version
```

3. Next, try cloning a repository to make sure you can access GitHub:

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

### Local vs Global configuration

#### Global configuration

If you are using a personal computer, apply the `--global` flag so you only have to set these settings once.

```sh
git config --global user.name "First-name Surname"
git config --global user.email "you@email.com"
```

#### Local configuration

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

### Setting the default branch name

```bash
git config --global init.defaultBranch main
```

### Automatically setting up remotes

The `push.autosetupremote` is a Git configuration option that controls the behavior of `git push` when a new branch is created.

When you create a new branch with `git branch` or `git checkout -b`, Git can automatically set up a branch in your remote repository to track your new local branch. This behavior is controlled by the `push.autosetupremote` configuration option.

The `push.autosetupremote` option can have three possible values:

- `always`: Whenever you create a new branch, Git will automatically set up a branch in your remote repository to track your new local branch. This is the same as using the `--track` option with `git branch` or `git checkout -b`.

- `matching`: Git will only set up tracking for branches with the same name in the remote repository. This is the default behavior.

- `nothing`: Git will not automatically set up tracking for new branches.

You can set this option with the `git config` command. For example, to set it to `always`, you would use:

```bash
git config --global push.autosetupremote always
```

This command sets the `push.autosetupremote` option to `always` for all repositories on your system. If you want to set it for a single repository, you can omit the `--global` option. 


### Setting a default editor

The `core.editor` configuration option in Git specifies the text editor that Git will use for commit messages, interactive rebase, and other operations that require user input.

By default, Git uses the system's default editor, which is usually Vim or Nano on Unix-based systems, and Notepad on Windows.

If you want to change the default editor to something else, you can use the `git config` command with the `core.editor` option. For example, to set the editor to VS Code, you can use:

```bash
git config --global core.editor "code --wait"
```

In this command, `--global` means that the configuration will apply to all repositories on your system. If you want to set the editor for a single repository, you can omit the `--global` option.

The `"code --wait"` argument tells Git to use VS Code as the editor, and to wait until the files are closed before continuing.

You can replace `"code --wait"` with the command for your preferred text editor. 

### Better diff syntax

The `merge.conflictstyle` configuration option in Git specifies the format of conflict markers when a merge conflict occurs.

By default, Git uses the `merge` style, which shows a `<<<<<<<`, a `=======`, and a `>>>>>>>` to mark the beginning of the conflicting changes from the current branch, the separation between the conflicting changes, and the end of the conflicting changes from the other branch, respectively.

If you set `merge.conflictstyle` to `diff3`, Git will use a slightly different format that includes the common ancestors of the conflicting changes. This can give you more context and make it easier to resolve the conflict.

Here's how you can set `merge.conflictstyle` to `diff3`:

```bash
git config --global merge.conflictstyle diff3
```

With `diff3` style, conflict markers look like this:

```bash
<<<<<<< HEAD
This is some content from the current branch.
||||||| merged common ancestors
This is some content from the common ancestor.
=======
This is some content from the other branch.
>>>>>>> other-branch
```

The `||||||| merged common ancestors` marker and the content below it show what the conflicting section looked like in the common ancestor of the two branches.

### Pushing tags

The `push.followTags` configuration option in Git specifies whether tags will be pushed along with your commits when you use `git push`.

By default, Git does not push tags when you use `git push`. You have to use `git push --tags` to push tags to the remote repository.

If you set `push.followTags` to `true`, Git will automatically push tags when you push commits, as long as the tags are reachable by the commits. This can be convenient if you frequently create tags and want them to be pushed automatically.

Here's how you can set `push.followTags` to `true`:

```bash
git config --global push.followTags true
```

### Rebase on pull

The `branch.autosetuprebase` configuration option in Git specifies whether new branches should be set up to automatically rebase when pulled.

By default, when you pull a branch, Git performs a merge, which can lead to a non-linear history. If you prefer a linear history, you can use `git pull --rebase` to rebase instead of merging.

If you set `branch.autosetuprebase` to `always`, Git will automatically set up new branches to rebase when pulled. This means that you don't have to use `--rebase` with `git pull`; Git will rebase by default.

Here's how you can set `branch.autosetuprebase` to `always`:

```bash
git config --global branch.autosetuprebase always
```

The `branch.autosetuprebase` option can have three possible values:

- `never`: The default behavior. Git will merge when you pull.
- `always`: Git will rebase when you pull.
- `remote`: Git will rebase when you pull a branch that was checked out from a remote tracking branch.

### Setting merge tool

The `merge.tool` configuration option in Git specifies the merge tool that Git will use when conflicts occur.

Git can use a variety of merge tools, such as `vimdiff`, `meld`, `kdiff3`, `opendiff`, and others. The merge tool you choose should be installed on your system and available in your `PATH`.

Here's how you can set `merge.tool` to use `vimdiff`:

```bash
git config --global merge.tool vimdiff
```

When a merge conflict occurs, you can use the `git mergetool` command to start the merge tool and resolve the conflict:

```bash
git mergetool
```

This command will start the merge tool specified by `merge.tool` and show the conflicting changes. You can then resolve the conflict in the merge tool.

### Handling line endings

Different systems handle line endings and line breaks differently. If you open a file created on another system and do not have this config option set, Git will think you made changes to the file based on the way your system handles this type of file.

- **Windows users:** `git config --global core.autocrlf true`
- **Mac users:** `git config --global core.autocrlf input`
