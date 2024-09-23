# Git-ting in Groups Using Rebase

## Setting up
- TEAM Lead Software Engineer creates each repository (one for front end, one for back end).
- Next, TEAM Lead adds every team member to the repos as collaborators (find in Settings on each repo).
- Each team member will have to accept the invitation through their email.

## Merging feature branches using Rebase
- Create a feature branch: `git checkout -b feature-branch`
- On your `feature-branch` you can write your changes to the code
- Then on the `feature-branch`, stage and commit your changes: `git add .`, `git commit -m "adding changes"`
- Now that our feature-branch has been committed, we will switch back to the `main` branch in order to pull down any changes made after we began working on our `feature-branch`.
- On the `main` branch, run `git pull` to bring down the changes to the remote version of the repo.
- Then switch back to `feature-branch`: `git switch feature-branch` or `git checkout feature-branch`

### Time to Rebase
- First we'll rebase our `feature-branch`: `git rebase main`.
Here we are merging our feature-branch code with our main branch code, here in our feature-branch.
If there are no merge conflicts then everything should be up to date on this branch. This branch now has the latest version of the codebase. Now we can run the rebase command on our main branch to merge changes there.
- Switch back to your `main` branch and run the rebase command to merge in the `feature-branch`: `git rebase feature-branch`
- Now you can add, commit, and push.

#### AFTER REBASING YOUR BRANCH INTO `main`, THE `feature-branch` SHOULD BE `DELETED`. YOU CAN CREATE A NEW BRANCH OFF OF `main/dev` 


## Handling merge conflicts
Merge conflicts can be scary when you don't know which commands to use and you see an error message.
When we have a merge conflict, it means that two separate codebases have different code that were are trying to merge into one.
Git wants you to resolve each conflict one by one. It will show you in VSCode the `current changes` versus the `incoming changes` and ask you to choose which changes to keep. You can choose one or both of the changes. 

#### YOU MAY NEED TO FIX YOUR CODE SINCE SOME LINES MAY OVERWRITE OTHER LINES THAT WERE ALSO USED.

That is why we rebased on the `feature-branch` first. If there are any conflicts, we'll resolve them here during our rebase and then we'll be good to go to rebase into our `main`.

1. On the `feature-branch` run: `git rebase main`
1. Uh Oh! Merge conflict.
1. Now resolve each conflicting file (there may be more than one code block where you need to resolve) by choosing one or both of the changes, then stage (git add .), then commit (git commit -m "message")
1. After resolving the changes in this file, staging and committing, move onto the next conflict by using `git rebase --continue`
1. Follow steps 3 and 4 until there are no more conflicts. Once you are finished you can stage and commit one last time.
1. Now switch to the main branch and run `git rebase feature-branch` and everything is good to go. Stage, commit, push to Github.
