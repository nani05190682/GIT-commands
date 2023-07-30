Add a new commit and reset back to one commit back
 $touch file1
 $git add .
 $git commit -m "file1 added"


Now Reset the HEAD to one level back
  $git reset --hard HEAD~1

Note: File2 will not be exists


The git reflog command is used to display a log of all the changes made to the local repository's references 
(e.g. branches, HEAD, tags) in reverse chronological order. 
It can be useful for recovering lost commits or branches that were accidentally deleted or overwritten.



git reflog
# git reset --hard <hash> - it will bring back the file


Lab Exercise:

Here's a lab exercise for practicing the use of `git reflog`:

## Objective
The objective of this lab exercise is to practice using the `git reflog` command to recover lost commits or branches in a local Git repository.

## Prerequisites
- Basic knowledge of Git commands (e.g. `git commit`, `git branch`, `git checkout`)
- A local Git repository with at least one commit and one branch

## Instructions
1. Create a new branch in your local Git repository using the command `git branch <branch-name>`. Make some changes to the new branch and commit them using the command `git commit -m "<commit-message>"`.

2. Switch back to the main branch using the command `git checkout main`. Make some changes to the main branch and commit them using the command `git commit -m "<commit-message>"`.

3. Delete the new branch using the command `git branch -D <branch-name>`.

4. Use the `git reflog` command to view a log of all the recent changes made to the repository's references. Find the commit hash of the last known location of the deleted branch.

5. Create a new branch at the commit hash using the command `git branch <new-branch-name> <commit-hash>`.

6. Switch to the new branch using the command `git checkout <new-branch-name>`.

7. Verify that your changes from step 1 are present in the new branch by using the command `git log`.



Merge Types:
	1. Fast-Forward
	2. Non Fast-Fast-Forward
	

##What is fast-forward merge?

A fast-forward merge in Git is a simple way to merge branches when the branch being merged into hasn't had any new commits since the branch being merged was created. 

Here's an example:

1. You have a branch called `main` and you create a new branch from it called `feature`.

2. You make some commits to `feature`, but there are no new commits on `main`.

In this case, a fast-forward merge is possible. Git will just move (or "fast forward") the `HEAD` pointer of the `main` branch to point to the latest commit of the `feature` branch. Essentially, Git just catches the `main` branch up with the `feature` branch, since the commits you made on the `feature` branch were based on the latest commit from `main` at the time the `feature` branch was created.

If there had been any new commits on `main` after you checked out the `feature` branch, a fast-forward merge wouldn't be possible. In that case, you'd either have to use a different kind of merge (creating a new merge commit that includes both the new `main` and `feature` commits), or rebase your changes on top of the updated `main` branch before you could do a fast-forward merge. 

You can force Git to use the fast-forward merge strategy when merging a branch with the `--ff-only` option, like so:

```bash
git merge --ff-only feature
```


If the branches can't be fast-forwarded, Git will abort the merge and let you know it couldn't be done.


## What is recursive merge?


A "recursive" merge is a strategy that Git uses to combine commits from two branches in cases where a "fast-forward" merge is not possible. This usually occurs when there have been changes on both branches since they diverged.

The name "recursive" comes from the fact that this strategy will recursively merge common ancestors of the two branches until it has created a common base that can be used to combine the changes.

**Here's an example:**

1. You have a `main` branch and you create a new branch from it called `feature`.
2. You make some commits to `feature`.
3. In the meantime, there are also new commits made on the `main` branch.

Now, if you want to merge `feature` back into `main`, you can't do a fast-forward merge because `main` has moved on since `feature` was branched off. The histories of the two branches have diverged. This is where a recursive merge comes in.

**The recursive merge strategy will:**

1. Identify the common ancestor of the two branches (the commit where `feature` was branched off).
2. Merge the changes made in `feature` with the changes made in `main`, using the common ancestor as the base.
3. If there are conflicts (i.e., the same part of the same file was changed in both `main` and `feature`), it will prompt you to resolve them.
4. Finally, it will create a new "merge commit" that brings together the changes from `main` and `feature`.

So, when you run `git merge feature` while `main` is checked out, and there are commits on both `main` and `feature`, Git will use the recursive merge strategy by default. The result is a history that shows how both lines of development were brought together.
