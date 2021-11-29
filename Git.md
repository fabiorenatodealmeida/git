# Git

This document is not a learning resource for someone new to Git. It is only a collection of usual tasks and how to do them. If you are new to Git technology, we suggest the following book: [Pro Git](https://git-scm.com/book/en/v2).

In the following sections, when a commit appears in command as a parameter (`<commit>`), you generally use the 40-character hash code associated with it. However, most of the time, you can use a tag or even a branch name, in which case you are effectively referencing the most recent commit on that branch.

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Basics](#basics)
4. [Log](#log)
5. [Differences](#differences)
6. [Restore](#restore)
7. [Tags](#tags)
8. [Show](#show)
9. [Branches](#branches)
10. [Merge](#merge)
11. [Remotes](#remotes)
12. [Push](#push)
13. [Fetch](#fetch)
14. [References](#references)

## Installation

Git download: [https://www.git-scm.com](https://www.git-scm.com/)

Make sure to install at least version 2.28. On Linux, type:

```
sudo apt install git[-all]
```

## Configuration

Settings for:

1. All users and all repositories (`/etc/gitconfig`).

   ```
   git config --system <key> <value>
   ```

2. All repositories of the current user (`~/.gitconfig`).

   ```
   git config --global <key> <value>
   ```

3. A specific project only (`PROJECT/.git/config`).

   ```
   git config [--local] <key> <value>
   ```

For instance, to configure Git for all repositories of the current user `johndoe`, you should do the following. Note that in this case, the text editor of choice is `vi` and the default branch for all new local repositories will be `main`.

```
git config --global user.name "John Doe"
git config --global user.email johndoe@hotmail.com
git config --global core.editor vi
git config --global init.defaultBranch main
```

To check the settings:

```
git config [--show-scope] [--show-origin] { --list | <key> }
```

## Basics

For help, type:

```
git VERB { --help | -h }
```

To initialize an empty local repository, go to the project directory and type:

```
git init
```

To stage content for the next commit, use:

```
git add *.c
git add <directory>
git add --all
```

It is better to set up a file named `.gitignore` in your project to tell Git what files or directories should not be part of a commit. For instance, you could have a `.gitignore` file like this:

```
*.log
directory/
filename
```

Type `man gitignore` for help on that.

You should also create a file named `.gitattributes` to explicitly tell Git what kind of binary files you have in your repository. It is crucial because Git will automatically convert `CR` + `LF` line endings to `LF` during check-in and check-out of text files to circumvent problems when contributors use different operating systems.

```
* text=auto eol=lf
*.{png,jpg,jpeg,gif} binary
```

To stop tracking a file, use the following command. The file will also be deleted from the working tree. Use `--cached` to only remove the file from the index.

```
git rm [--cached] <file>
```

Check the status of your working tree and, if everything is correct, make a commit.

```
git status
git commit [--verbose] [--amend]
```

Your text editor of choice will open and allow you to enter information about the commit. Type a short description for the title of the commit (less than 50 characters), followed by a blank line and more detailed information about the work you have done. Only the title is required. If you need to repair a previous commit because you forgot to add a file or wrote a wrong commit message, use the option `--amend`. However, never use the `--amend` option if you already have made the history public.

## Log

To see the history of changes, use:

```
git log [--patch] [--stat] [--author="..."] [--grep="commit-message word"]
        [--after="YYYY-MM-DD hh:mm:ss"] [--before="YYYY-MM-DD hh:mm:ss"]
        [--graph] [--oneline] [--all]
        [ <branch> | <file> ]
```

To see the log between two points in time, use the range notation. This will report entries after `<commit-1>` and up to `<commit-2>`:

```
git log <commit-1>..<commit-2>
```

For instance, if tag `v1.0.0` points to the project current stable version, you can see all patches after this version by typing:

```
git log --patch v1.0.0..
```

## Differences

You can compare your working tree with what is in your staging area with:

```
git diff [<file-or-directory>]
```

You can compare your working tree with a specific point in time with:

```
git diff <commit> [<file-or-directory>]
```

If you want to compare what is in your staging area with your last commit, use:

```
git diff --staged [<file-or-directory>]
```

You can also compare between to points in time:

```
git diff <commit-before> <commit-after> [<file-or-directory>]
```

Show differences between two branches:

```
git diff <branch-1>...<branch-2>
```

## Restore

Restore content from a specific point in time with:

```
git restore --source=<commit> <file-or-directory>
```

## Tags

List tags:

```
git tag [--list ["v0.1.*"]]
```

Create a tag for the most recent commit on the branch or a specific `<commit>` in history.

```
git tag --annotate <tag> [<commit>]
```

Delete a tag:

```
git tag --delete <tag>
```

## Show

To see the details of a commit or tag, or even the version of a file at some point in time, type:

```
git show { <commit> | <tag> }[:<file>]
```

## Branches

List branches:

```
git branch [--all]
```

Create a new movable pointer `<branch>` referencing the same commit you are currently on or over an older `<commit>`:

```
git branch <branch> [<commit>]
```

Go to the specified branch:

```
git switch <branch>
```

Go to the past (detached HEAD):

```
git switch --detach <commit>
```

Delete a branch that already has been merged:

```
git branch --delete <branch>
```

Delete a branch that you want to discard the work:

```
git branch -D <branch>
```

## Merge

To merge the changes made in branch `issue-1` into the branch `main`, type:

```
git switch main
git merge issue-1
```

If there are conflicts, resolve them and finish the merge process with a commit:

```
git diff
git add .
git commit
```

Alternatively, you can abort the merge to return to the previous state:

```
git merge --abort
```

## Remotes

Add a new remote repository named `origin`. This is normally the repository you have read/write access to.

```
git remote add origin git@github.com:user/project.git
```

List remote repositories:

```
git remote [--verbose]
```

Show details about the remote repository:

```
git remote show origin
```

## Push

To send your commits in a branch to the remote repository:

```
git push origin <branch>
```

Delete a branch from the remote repository:

```
git push origin --delete <branch>
```

Tags need to be pushed to the remote repository with:

```
git push origin <tag>
```

Use this to push all local tags with only one command:

```
git push origin --tags
```

To remove a tag from the remote repository, type:

```
git push origin --delete <tag>
```

## Fetch

To get the most recent commits in a branch from the remote repository:

```
git fetch origin <branch>
```

## References

- [Git - Book](https://git-scm.com/book/en/v2)
- [Git - Reference](https://git-scm.com/docs)
- [The Official GitHub Training Manual](https://githubtraining.github.io/training-manual/#/)
