# Workflow for private repositories with contributors

For the following sections, we are taking as an example a hypothetical private repository on GitHub named `project-1` and owned by the organization `user-org`, which is supposed to be under the account of the project maintainer. First, we consider what the maintainer should do to prepare for collaboration. Then, we describe the workflow that a contributor should follow. Finally, we will see the steps the maintainer must be aware of when a contributor has finished a task.

## Maintainer

The best way to work with a private repository is to attach it to an organization instead of directly to your GitHub user account.

On the GitHub website:

- Create an organization under your GitHub user account if you don't have one yet.
- Go to your organization and create a private repository for the project.
- Add one or more contributors to the repository (Project Settings :arrow_right: Manage access). Contributors must at least be allowed to push and manage issues in the repository.

On your local machine, initialize your git repository and push your first commit.

```
git init
git add .
git commit
git remote add origin git@github.com:user-org/project-1.git
git push origin main
```

Now contributors can clone and work on the project.

## Contributor

Even though it is private, an authorized contributor can access the repository: `https://github.com/user-org/project-1`.

1. First, the contributor must clone the remote repository to his local machine.

   ```
   git clone git@github.com:user-org/project-1.git
   ```

2. Before doing any work, you should consider going to the GitHub website project `https://github.com/user-org/project-1` and open an issue to discuss your idea.

3. When your issue is accepted, or you just want to try it yourself, create a branch to work on the project. Use a suggestive name or a name related to an open issue, like `crazy-idea` or `issue-1`. But remember, **always create a branch** before starting your work.

   ```
   git branch issue-1
   ```

4. Then go to the branch you just created.

   ```
   git switch issue-1
   ```

5. Now you can work on the project (add files, edit content, make commits), and eventually, go back to the GitHub website to discuss the issue with the maintainer and other contributors. Stay on this step as long as you want to.

6. As soon as you are ready to share your work, send your commits to the remote server.

   ```
   git push origin issue-1
   ```

7. You can continue to work on your task or wait for the response of the maintainer. You can also start another parallel development line by working on other issues.

8. If your work has been accepted and merged into the `main` branch by the maintainer, then you must synchronize your local `main` branch with the remote repository and finally discard your temporary working branch.

   ```
   git fetch origin main
   git switch main
   git merge origin/main
   git branch --delete issue-1
   ```

9. If for any reason you need the latest commits pushed by other contributors, you can fetch and merge them into your working branch.

   ```
   git fetch origin main
   git switch issue-1
   git merge origin/main
   ```

## Merge

Although any contributor with write access to the repository can do this operation, we are delegating it here only to the project maintainer.

1. First, you have to fetch the branch the contributor was working on into your local repository.

   ```
   git fetch origin issue-1
   git switch issue-1
   ```

2. After reviewing the contributor's work, the maintainer must decide whether it will be accepted or rejected.

3. By accepting the work, the branch on which the job was done must be merged into the `main` branch.

   ```
   git switch main
   git merge issue-1
   ```

   Now you push the `main` branch to the remote repository and delete the branch the contributor was working on from both the remote and your local repository.

   ```
   git push origin main
   git push origin --delete issue-1
   git branch --delete issue-1
   ```

   If necessary, tag the pushed version:

   ```
   git tag --annotate v1.0.0-rc1
   git push origin v1.0.0-rc1
   ```

4. In case the work must be rejected.

   You can abort the merge process if it is already started.

   ```
   git merge --abort
   ```

   Or you can just go back to the `main` branch and communicate with the contributor about the reasons.

   ```
   git switch main
   ```

## Final Thoughts

The maintainer could also work on an issue, but in this case, the maintainer should assume the role of a contributor and go through the same steps a regular contributor would go. The only difference is that the acceptance of the work will be done by himself.

## References

- [Git - Book](https://git-scm.com/book/en/v2)
- [Patterns for Managing Source Code Branches](https://martinfowler.com/articles/branching-patterns.html)
- [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
