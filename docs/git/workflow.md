# Workflow

Workflow is just the recommended way of using the version control.

Version Control is a system that records changes to a file or set of files over time so that you can recall specific versions later. There are a lot of types of version controlled system, to manage this project we use git, a Distributed Version Control System.

Git is flexible in how a user manage changes, which leads to different types of workflows. This project uses what you call is a __Forking Git Workflow__. 

### Forking a repo
Fork the organization repo to your github account. A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project.

- To fork a repo, just go to the site of the repo you want to fork, and click the `Fork` button on the page.
- Select an owner for the forked repo
- Choose whether to copy only the default [branch](/git/branches.md) or all branches to the new fork.
- Click Create fork.

### Cloning your forked repo
Now, you have a personal remote copy of the repo. You need to bring this copy to your local machine so that you will be able to make changes. We do this by cloning the repo.

- To clone a fork, go to GitHub.com, navigate to your fork.
- Above the list of files, click on __Code__ and then choose SSH option, copy the SSH URL for the repo.
- Now, open terminal and cd to where you want the cloned repo.
- Type `git clone`, and then paste the URL you copied earlier. It will look something like 
  ```shell
  git clone git@github.com:YOUR_USERNAME/YOUR_FORK.git
  ```
  Press __Enter__. Your local clone will be created. 
- Run `git remote -v`. You will see current configured remote repository for your fork.
    ```shell
    $ git remote -v
    > origin  git@github.com:YOUR_USERNAME/YOUR_FORK.git (fetch)
    > origin  git@github.com:YOUR_USERNAME/YOUR_FORK.git (push)
    ```  
 `origin` is auto-generated and points at your fork of the repo(parent repo). When you make new changes to the code base, `origin` is where you will push them. 

### Keeping your fork updated
Eventually, the original repo will have changes made to it, so you need a way to pull these updates. In order to do so, you need to add a remote that points to it. Traditionally, we call this `upstream`.

- On GitHub.com, navigate to the original repo.
- Above the list of files, click on __Code__ and then choose SSH option, copy the SSH URL for the repo.
- Open your clone of the fork in Terminal.
- Type `git remote add upstream` and then paste the URL and press __Enter__. It will look like
  ```shell
  $ git remote add upstream git@github.com:ORIGINAL_OWNER/REPO_NAME.git
  ```
- To verify run `git remote -v`. 
  ```shell
  $ git remote -v
  > origin    git@github.com:YOUR_USERNAME/YOUR_FORK.git (fetch)
  > origin    git@github.com:YOUR_USERNAME/YOUR_FORK.git (push)
  > upstream  git@github.com:ORIGINAL_OWNER/REPO_NAME.git (fetch)
  > upstream  git@github.com:ORIGINAL_OWNER/REPO_NAME.git (push)
  ```

### Making Changes
Before you make any changes, you should make a branch. Remember to __never commit to main__. The command `git status` will tell you what branch you are on.
It is important that you never commit to main because main will be the branch that you will pull upstream changes from.

1. __Update main__ - Before you make any changes, first checkout main.
   ```shell
   git checkout main
   ```
    and pull in the latest changes
    ```shell
    git pull
    ```
    This will make it so that your changes are against the very latest main, which will reduce the likelihood of merge conflicts due to your changes conflicting with changes made by someone else.
1. __Create a branch__ - You should make a branch name that is short, descriptive, and unique, as people will use this to reference your changes if they want to pull them down on their own computer to test them.   
    - To create a branch, run `git checkout -b branch-name`. This will create a new branch and check it out. You can verify this with `git status`.
1. __Make your changes and commit them__ - Once you have created your branch, make your changes and commit them. Remember to keep your commits atomic, that is, each commit should represent a single unit of change. Also, remember to write helpful commit messages, so that someone can understand what the commit does just from the reading the message without having to read the [diff](https://git-scm.com/docs/git-diff).
   For example, at the command line, this might look like
   ```shell
   git add filename [filename ...]
   git commit 
   ```
   This will open an editor where you can write your commit message.
1. __Push up your changes__ - Push your changes to your fork. Do this, by running 
  ```shell
  git push origin feature-branch
  ```
2. __Make a pull request__ - Once you see your branch appear in GitHub, be sure to compare your branch with the original repo's main branch. This is where you can check for any merge conflicts that need to be resolved. After resolving, if it all looks good, make your pull request of the branch you want. Give your pull request a proper title and description(optional).
3. __Pushing additional changes__ - Once you have created a pull request, it will likely be reviewed and some additional fixes will be necessary. __Do not create a pull request__. Rather, simply make more commits to your branch and push them. They will be added to the pull request automatically.

Once the pull request has been reviewed successfully, someone with push access to the main repo will merge it in. At this point you are done. You can checkout main and pull as described in Step 1 and your changes should be there.

!!!note "Important points"
    - You only need to clone and fork once per repo.
    - Use `git status` often to check what branch you are on and see if you have any uncommitted changes.
    - Be descriptive in your branch names, commit messages, and pull request title and descriptions.
    - It is good idea to make a comment on the pull request whenever you commit more changes so people get notified that it is ready to be reviewed again, as many people have notifications off for commits on pull requests.

### References
- [More on Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
- [Some Distributed Git Workflows](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Workflow recommended by GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Contributing to a project in Distributed Git](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)