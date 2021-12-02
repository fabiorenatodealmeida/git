# Workflow for public repositories with contributors

For the following sections, we are taking as an example a hypothetical public repository on GitHub named `project` and owned by the user `maintainer`, who is the project maintainer. We also consider a hypothetical contributor under the user account `contributor`.

First, we look at what a maintainer should do to prepare for collaboration. Then, we describe the workflow that contributors should follow. Finally, we will see the steps a maintainer must be aware of when a contributor makes a pull request.

## Maintainer

On the GitHub website, go to your user account and create a public repository for the project.

On your local machine, initialize your Git repository and push your first commit.

```
git init
git add .
git commit
git remote add origin git@github.com:maintainer/project.git
git push origin main
```

Now contributors can fork and work on their copy of the project.

## Contributor

Because the maintainer's repository is public, every GitHub user can access it: `https://github.com/maintainer/project`.

1. First, the contributor must fork the repository and clone his forked version to a local machine.

   ```
   git clone git@github.com:contributor/project.git
   ```

2. Before doing any work, you should consider going to the official GitHub website project `https://github.com/maintainer/project` and search for an issue to contribute or open one to discuss your idea.

3. When your issue is accepted, or you just want to try it yourself, create a branch to work on your copy of the project. Use a suggestive name related to the issue title and tracking number, like `doc-122-add-samples`, `bug-3-password-incorrect`, `feature-88-add-pdf-report`, `idea-12-hash-instead-of-btree`. But remember, **always create a branch** before starting your work.

   ```
   git branch <working-branch>
   ```

4. Then go to the branch you just created.

   ```
   git switch <working-branch>
   ```

5. Now you can work on the project (add files, edit content, make commits), and eventually, go back to the official GitHub website project to discuss the issue with the maintainer and other contributors. Stay on this step as long as you want to.

6. As soon as you are ready to share your work, send your commits to your remote server.

   ```
   git push origin <working-branch>
   ```

7. Access your GitHub remote copy of the project `https://github.com/contributor/project` and make a pull request on your working branch.

8. You can continue to work on your task or wait for the response of the maintainer. You can also start another parallel development line by working on other issues.

9. If your work has been accepted and merged into the `main` branch by the maintainer, then go to your GitHub website project and click on "Fetch upstream" to keep your copy up-to-date with the official repository. After that, synchronize your local repository and discard your temporary working branches.

   ```
   git fetch origin main
   git switch main
   git merge origin/main
   git push origin --delete <working-branch>
   git branch --delete <working-branch>
   ```

10. If for any reason you need the latest commits pushed by other contributors, fetch them first from the upstream repository as described in the previous step. After that, fetch from your remote copy of the project and merge it into your working branch.

```
git fetch origin main
git switch <working-branch>
git merge origin/main
```

## Pull Request

As a maintainer, you should take the following actions when a pull request is made by a contributor.

1. First, you have to add the contributor's repository as a remote one and fetch his working branch into your local repository.

   ```
   git remote add contributor git@github.com:contributor/project.git
   git fetch contributor <working-branch>
   git switch <working-branch>
   ```

2. After reviewing the contributor's work, the maintainer must decide whether it will be accepted or rejected.

3. By accepting the work, the branch on which the job was done must be merged into the `main` branch.

   ```
   git switch main
   git merge <working-branch>
   ```

   Now you push the `main` branch to the remote repository and delete the branch the contributor was working on from your local repository.

   ```
   git push origin main
   git branch --delete <working-branch>
   ```

   If necessary, tag the pushed version:

   ```
   git tag --annotate v1.0.0
   git push origin v1.0.0
   ```

4. In case the work must be rejected.

   You can abort the merge process if it is still in progress.

   ```
   git merge --abort
   ```

   Or you can just go back to the `main` branch and communicate with the contributor about the reasons.

   ```
   git switch main
   ```

## Final Thoughts

The maintainer could also work on an issue, but in this case, the forking of the official repository is not necessary because the maintainer, as the owner of the public project, has read and write access to the repository.

## References

- [Git - Book](https://git-scm.com/book/en/v2)
- [Patterns for Managing Source Code Branches](https://martinfowler.com/articles/branching-patterns.html)
- [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
