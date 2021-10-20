# Git Fundamentals

## What is Git ?

According to [https://git-scm.com/](), Git is a free and open source distributed version control system (DVCS) designed to handle everything from small to very large projects with speed and efficiency.

Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

## Configuration 

Set up the user name and email adress
```bash
git config --global user.name 'John Doe'
git config --global user.email 'john.doe@somewhere.com'
```

Set up default editor (can be emacs, nano, vim, notepad++, etc.)
```bash
git config --global core.editor nano
```

Set up auto-correct in case of mistyping a git command (the number corresponds to the delay after which the suggested command will be executed)
```bash
git config --global help.autocorrect 5
```

Set up color 
```bash
git config --global color.ui auto
```

Set up automatic conversion of `crlf` endlines to `LF` endlines to avoid line-ending issues (when working with both Windows and GNU/Linux for example).
```bash
git config --global core.autocrlf input
```

These user-level configurations are stored in `~/.gitconfig` or `C:\Users\<user_name>\.gitconfig`

By using `--system` argument instead of `--global`, the configuration will be stored in `/etc/gitconfig` or `C:\Program Files (x86)\Git\etc\gitconfig`. It corresponds to a system-level configuration while `--global` corresponds to a user-level configuration.

For repository-level configuration, the argument `--local` is used. THe configuration file is then stored in `.git/config` in each repository.

To obtain the configuration for the user-level for example:
```bash
git config --global --list
```

To unset parameters, for example `user.name`
```bash
git config --global --unset user.name
```

## Working locally

## Working remotely

## Branching, merging and rebasing