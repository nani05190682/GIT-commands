# GIT-rebase

# Lab Exercise: Git Rebase 

In this lab exercise, we will simulate a scenario of collaborating on a project with multiple contributors and branches. The objective is to understand how to use `git rebase` to ensure your feature branch is up-to-date with the changes in the main branch.

**Scenario**

We have a main branch (`main`) and a feature branch (`feature_branch`). Another contributor has just merged a new feature into `main`, and you need to incorporate those changes into your `feature_branch`.

**Instructions:**

1. Clone the project into your local system.
   
    ```bash
    git clone https://github.com/Your-Repo/Your-Project.git
    ```
   
2. Navigate into the project's directory.
   
    ```bash
    cd Your-Project
    ```
   
3. Check out the `feature_branch`.

    ```bash
    git checkout feature_branch
    ```
   
4. Add a new file called `sample.txt` with some text content and commit the change.

    ```bash
    echo "Hello, World!" > sample.txt
    git add sample.txt
    git commit -m "Added sample.txt"
    ```
   
5. Now switch back to the `main` branch and simulate a scenario where a new feature has been merged.

    ```bash
    git checkout main
    echo "New feature" > feature.txt
    git add feature.txt
    git commit -m "Added new feature"
    ```
   
6. Now, we will rebase `feature_branch` onto the `main` branch. This operation moves or combines a sequence of commits to a new base commit. This is a way to integrate changes from one branch into another.

    ```bash
    git checkout feature_branch
    git rebase main
    ```
   
7. At this point, if there are any conflicts, you will have to resolve them manually.

8. Once the conflicts are resolved, continue the rebase operation.

    ```bash
    git rebase --continue
    ```
   
9. Finally, verify the changes in your `feature_branch`.

    ```bash
    git log
    ```
   
   You should see your commits in `feature_branch` on top of the commits in `main` branch, meaning your feature branch is now updated with the new changes in the main branch.
   
**Note:** Rebase is a powerful command. You should refrain from rebasing public branches that others are working on because it rewrites commit history. It is best used for cleaning up local commit history before merging into a public branch.

This exercise aims to make you familiar with the `git rebase` command, which is a common operation while working on feature branches in a collaborative project.

