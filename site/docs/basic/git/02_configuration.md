# Configuring Git

Git allows you to set configuration options at three different levels.

- `--system` These are system-wide configurations. They apply to all users on this computer.
- `--global` These are the user level configurations. They only apply to your user account.
- `--local` These are the repository level configurations. They only apply to the specific repository where they are set.

> The default value for git config is `--local`.

If you would like to see which config settings have been added automatically, you can type 
```sh
git config --list
```

This will automatically read from each of the three config files and list the setting they contain.


You can also narrow the list to a specific configuration level by including it before the list option:

```sh
git config --global --list
```