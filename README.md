# git - the stupid content tracker

*"As you go through it, you will discover it is not really stupid."*

This repository contains basic information for those who want to use GitHub as a contributor or maintainer of a project. We consider two cases here:

1. A maintainer with a private repository within an organization and some contributors. These contributors are the members of the organization or outside collaborators with read/write access to the repository. Read the [Workflow-for-private.md](Workflow-for-private.md) file to learn the basics of interaction in a private domain.

2. A maintainer with a public repository and some contributors. Here, only the maintainer will have read/write access to the repository. Contributors contribute to the project by forking the repository, working on their copy, and making a pull request to share the work. Read the [Workflow-for-public.md](Workflow-for-public.md) file to learn the basics of interaction in a public domain.

In either case, you must check the [Markdown.md](Markdown.md) file to learn how to use the Markdown language to write issues or participate in discussions using the GitHub platform.

The [Git.md](Git.md) file contains some git commands you will need when working on a project. Some of these commands run over an SSH connection, so the maintainer and contributors must have their own SSH private/public key pair. To generate such a pair of keys, type:

```
ssh-keygen -t ed25519 -C "GitHub-User-e-mail"
```

We recommend you first set up your GitHub account with your public key before trying any Git command. Then you will be able to run over an SSH connection without even having to type your user name and password each time you go to the remote server. Read [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) for more information.
