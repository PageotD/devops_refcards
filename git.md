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

To initialize a local repository with git, from within the repository
```bash
git init
```

To add files
```bash
git add <file_name>
```
The `-u` after `git add` allows to add only updated files which are already tracked.

To view the state of the git repository ((un)tracked files, modified files, etc.)
```bash
git status
```

To commit
```bash
git commit -m "Some commit message"
```

To view the differences between the current version and the previous commited version

```bash
git diff
git diff HEAD~1..HEAD
```
The second command will return the differences between the current and the previous commits.

To delete a file from project and stage the removal for commit
```bash
git rm <file_name>
```

To change an existing file path and stage the move
```bash
git mv <source> <destination>
```
To show all commit logs with indication of any paths that moved
```bash
git log --stat -M
git log --oneline --graph
git shortlog
git log origin/main
```

To clear staging area, rewrite working tree from specified commit
```bash
git reset --hard <commit>
```
Using `HEAD~1` will reset the repository to the previous commit status and will erase the current commit status.

To remove untracked files from the worktree
```bash
git clean
```
`-n` option allows to dry-run.

To automatically ignore files, a `.gitignore` files can be created
```bash
# .gitignore
*.txt # will ignore all files with the .txt extension
img/* # will ignore all files in the img folder
```

## Working remotely

To retrieve an entire repository from a hosted location via URL
```bash
git clone <repository_url>
```

To show the history of the commits
```bash
git show
git show <commit>
```

To see the list of remote repositories
```bash
git remote -v
```

To add a Git url as an alias
```bash
git remote add <alias> <git_url>
```

To see the branches
```bash
git branch [-r/-v]
```
`-r` otion gives the remote repositories, `-v` gives a list of all the branches.

To fetch and merge any commits from the tracking remote branch
```bash
git pull
```

To transmit local branch commits to the remote repository branch
```bash
git push
```

To tag a commit
```bash
git tag # list the tags
git tag -a v1.4 -m "my version 1.4" #Add a tag with a message
git tag -s v1.4_signed # Allows to signed the tag for verification
```

By default, Git does not push tags. To push the tags
```bash
git push --tags
```

## Branching, merging and rebasing

