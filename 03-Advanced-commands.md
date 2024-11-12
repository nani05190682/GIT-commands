# GIT reflog


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



### step-by-step solution for the given exercise:
---

### Step 1: Create a New Branch
Create a new branch in your local Git repository.

```bash
git branch new-feature
```

### Step 2: Switch to the New Branch
Switch to the newly created branch.

```bash
git checkout new-feature
```

Alternatively, you can use:

```bash
git switch new-feature
```

### Step 3: Make Changes and Commit Them
Make some changes to a file (for example, `file.txt`), then add and commit those changes.

```bash
echo "Changes in new-feature branch" >> file.txt
git add file.txt
git commit -m "Added changes in new-feature branch"
```

### Step 4: Switch Back to the Main Branch
Switch back to the `main` branch.

```bash
git checkout main
```

Alternatively:

```bash
git switch main
```

### Step 5: Make Changes on the Main Branch and Commit Them
Make some changes on the `main` branch, then add and commit those changes.

```bash
echo "Changes in main branch" >> file.txt
git add file.txt
git commit -m "Added changes in main branch"
```

### Step 6: Delete the New Branch
Delete the `new-feature` branch.

```bash
git branch -D new-feature
```

### Step 7: Use `git reflog` to Find the Commit Hash
View the Git reference log to find the commit hash of the last known location of the deleted branch.

```bash
git reflog
```

Look for the entry that corresponds to the deleted `new-feature` branch commit. Note down the commit hash (let’s say it’s `abc1234`).

### Step 8: Create a New Branch at the Commit Hash
Create a new branch from the commit hash retrieved from the reflog.

```bash
git branch recovered-feature abc1234
```

### Step 9: Switch to the New Branch
Switch to the newly created branch.

```bash
git checkout recovered-feature
```

Alternatively:

```bash
git switch recovered-feature
```

### Step 10: Verify Your Changes
Verify that your changes from the original `new-feature` branch are present in the `recovered-feature` branch.

```bash
git log
```

You should see the commit you made in the `new-feature` branch.

### HISTORY
```bash
git branch new-feature
git checkout new-feature
echo "Changes in new-feature branch" >> file.txt
git add file.txt
git commit -m "Added changes in new-feature branch"
git checkout main
echo "Changes in main branch" >> file.txt
git add file.txt
git commit -m "Added changes in main branch"
git branch -D new-feature
git reflog
git branch recovered-feature <commit-hash>
git checkout recovered-feature
git log
```


Merge Types:
	1. Fast-Forward

Let's dive into the types of Git merges: **Fast-Forward** 

---

### 1. Fast-Forward Merge

A **Fast-Forward** merge happens when the branch you are merging into (e.g., `main`) has not diverged from the branch you are merging (`feature`). In this case, Git simply moves the `main` branch pointer forward to point to the latest commit on the `feature` branch.

#### Example of Fast-Forward Merge

**Step 1: Initialize a Git repository and create a file**

```bash
git init
echo "Initial commit" > file.txt
git add file.txt
git commit -m "Initial commit on main"
```

**Step 2: Create and switch to a new branch**

```bash
git checkout -b feature
```

**Step 3: Make changes in the `feature` branch**

```bash
echo "Feature work" >> file.txt
git add file.txt
git commit -m "Added feature work"
```

**Step 4: Switch back to the `main` branch**

```bash
git checkout main
```

**Step 5: Merge the `feature` branch into `main`**

```bash
git merge feature
```

**Outcome:**  
- The `main` branch pointer is simply moved forward to point to the latest commit of the `feature` branch.
- No new merge commit is created.
- The history remains linear.

**Git Log Output:**

```
* Added feature work (feature)
* Initial commit on main
```

---






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



Sure, here's a lab exercise for performing a non-fast forward merge in Git:

1. Start by creating a new branch called `feature` and checking it out:

   ```
   git checkout -b feature
   ```

2. Make some changes to a file in the `feature` branch and commit them:

   ```
   # Make some changes to a file
   git add .
   git commit -m "Made some changes in the feature branch"
   ```

3. Switch back to the `main` branch:

   ```
   git checkout main
   ```

4. Make some changes to the same file in the `main` branch and commit them:

   ```
   # Make some changes to the same file
   git add .
   git commit -m "Made some changes in the main branch"
   ```

5. Merge the `feature` branch into `main` using the `--no-ff` flag to force a non-fast forward merge:

   ```
   git merge --no-ff feature
   ```

6. Git will open your default text editor to allow you to enter a commit message for the merge commit. Enter a meaningful message and save it.

7. Finally, push your changes to the remote repository:

   ```
   git push origin main
   ```

Congratulations! You have successfully performed a non-fast forward merge in Git.

# GIT rebase
Git rebase is a command that allows you to move the changes made in one branch to another branch. It is used to integrate changes from one branch into another branch in a more linear manner than merging.

Here's an example:

Let's say you have two branches, `master` and `feature`. You are currently on the `feature` branch and have made some changes. Meanwhile, changes have also been made on the `master` branch. To integrate these changes into your `feature` branch, you can use the following command:

```
git rebase master
```

This will move your changes on top of the changes made on the `master` branch, resulting in a more linear history.

It's important to note that using `git rebase` can change the commit history, so it should be used with caution.
