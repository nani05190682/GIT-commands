

Current Directory and Staging Area in GIT

In Git, the current directory refers to the directory that you are currently working in. It is the directory that contains the files and directories that you want to track with Git.

The staging area, also known as the index, is a place where you can prepare changes for a commit. When you make changes to files in your working directory, those changes are not automatically added to the next commit. Instead, you must explicitly add them to the staging area using the `git add` command. Once the changes are in the staging area, you can review them and make any necessary modifications before committing them to the repository using `git commit`.

Think of the staging area as a place where you can review and organize your changes before committing them to your repository. It allows you to selectively choose which changes you want to include in your next commit, and gives you an opportunity to review your changes before making them permanent.


How to create a initial commit in GIT ?

To create an initial commit in Git, you can follow these steps:

1. First, initialize a new Git repository in your project directory by running the command `git init`.
2. Add the files you want to track to the staging area using the command `git add <filename>` or `git add .` to add all files.
3. Commit the changes using the command `git commit -m "Initial commit"`.


 Lab exercise for creating an initial commit in Git:

1. Create a new directory for your project and navigate to it using the command line.

   ```
   mkdir myproject
   cd myproject
   ```

2. Initialize a new Git repository in the directory using the command `git init`.

   ```
   git init
   ```

3. Create a new file in the directory and add some content to it.

   ```
   touch README.md
   echo "Hello, world!" > README.md
   ```

4. Add the file to the staging area using the command `git add`.

   ```
   git add README.md
   ```

5. Commit the changes with a message using the command `git commit`.

   ```
   git commit -m "Initial commit"
   ```

6. Verify that the commit was created by running the command `git log`.

   ```
   git log




GIT Logs:

To read the logs in Git, you can use the `git log` command. This command displays a list of all the commits in your repository, along with some information about each commit, such as the commit hash, author, date, and commit message.

Here's an example lab exercise for reading the logs in Git:

1. Create a new directory for your project and navigate to it using the command line.

   ```
   mkdir myproject
   cd myproject
   ```

2. Initialize a new Git repository in the directory using the command `git init`.

   ```
   git init
   ```

3. Create a new file in the directory and add some content to it.

   ```
   touch README.md
   echo "Hello, world!" > README.md
   ```

4. Add the file to the staging area using the command `git add`.

   ```
   git add README.md
   ```

5. Commit the changes with a message using the command `git commit`.

   ```
   git commit -m "Initial commit"
   ```

6. Make some changes to the file and commit them.

   ```
   echo "This is a new line." >> README.md
   git add README.md
   git commit -m "Added a new line to README.md"
   ```

7. View the logs using the `git log` command.

   ```
   git log
   ```



Branches in GIT

In Git, a branch is a lightweight movable pointer to a commit. It is essentially a way to create a separate line of development that is independent from the main line of development. Each branch represents a different version of the codebase, and changes made in one branch do not affect the code in other branches until they are merged together.

The main branch in Git is usually called "master", but you can create as many branches as you need for your project. Branches are useful for working on new features, fixing bugs, or experimenting with new ideas without affecting the main codebase. Once you are satisfied with the changes in a branch, you can merge it back into the main branch to incorporate the changes into the main codebase.

Using branches in Git allows multiple developers to work on different parts of a project simultaneously without interfering with each other's work. It also provides a way to experiment with new features or ideas without affecting the stability of the main codebase.

Use Cases of GIT Branches:


There are many use cases for Git branches, including:

1. Feature development: You can create a new branch for each new feature you are working on, allowing you to develop and test the feature without affecting the main codebase.

2. Bug fixing: If you discover a bug in the code, you can create a new branch to fix the bug without affecting the main codebase.

3. Experimentation: You can create a branch to experiment with new ideas or technologies without affecting the stability of the main codebase.

4. Code reviews: You can create a branch to review changes made by another developer before merging them into the main codebase.

5. Release management: You can create a branch for each release of your software, allowing you to maintain different versions of the codebase with different features and bug fixes.

6. Hotfixes: If you need to make an urgent fix to the code, you can create a branch to fix the issue and merge it into the main codebase as soon as possible.




How to create a branch :


To create a new branch in Git, you can use the `git branch` command. Here are the steps to create a new branch:

1. Make sure you are in the main branch by running `git branch` command. The current branch will be highlighted with an asterisk.

   ```
   git branch
   * master
   ```

2. Create a new branch by running the `git branch <branch-name>` command, where `<branch-name>` is the name of the new branch you want to create.

   ```
   git branch feature-branch
   ```

3. Switch to the new branch by running the `git checkout <branch-name>` command.

   ```
   git checkout feature-branch
   ```

Alternatively, you can combine steps 2 and 3 into a single command by running `git checkout -b <branch-name>`, which creates a new branch and switches to it in one step.

   ```
   git checkout -b feature-branch
   ```

























Lab 02:

 Lab exercise for creating a branch in Git:
1. Create a new directory for your project and navigate to it using the command line.

   ```
   mkdir myproject
   cd myproject
   ```

2. Initialize a new Git repository in the directory using the command `git init`.

   ```
   git init
   ```

3. Create a new file in the directory and add some content to it.

   ```
   touch README.md
   echo "Hello, world!" > README.md
   ```

4. Add the file to the staging area using the command `git add`.

   ```
   git add README.md
   ```

5. Commit the changes with a message using the command `git commit`.

   ```
   git commit -m "Initial commit"
   ```

6. Create a new branch using the `git branch` command.

   ```
   git branch feature-branch
   ```

7. Switch to the new branch using the `git checkout` command.

   ```
   git checkout feature-branch
   ```

8. Make some changes to the file and commit them.

   ```
   echo "This is a new feature." >> README.md
   git add README.md
   git commit -m "Added a new feature to README.md"
   ```

9. Switch back to the main branch using the `git checkout` command.

   ```
   git checkout master
   ```

10. Verify that the changes made in the feature branch did not affect the main branch.

    ```
    cat README.md
    ```

    You should only see the original content of the file, "Hello, world!".




GIT Merge:

In Git, merging is the process of combining changes from one branch into another. When you merge a branch, Git takes the changes made in the source branch and applies them to the target branch, creating a new commit that incorporates the changes.

Merging is typically used to incorporate changes made in a feature branch back into the main branch, or to incorporate bug fixes made in a bugfix branch back into the main branch. It allows multiple developers to work on different parts of a project simultaneously without interfering with each other's work.

When you merge a branch, Git will automatically try to merge the changes in the two branches. If there are any conflicts between the changes, Git will prompt you to resolve them manually before completing the merge.

Merging is an important part of Git workflow and allows teams to collaborate on a codebase effectively.


Lab Exercise:

Sure, here's an example of how to merge two branches in Git:

1. Create a new directory for your project and navigate to it using the command line.

   ```
   mkdir myproject
   cd myproject
   ```

2. Initialize a new Git repository in the directory using the command `git init`.

   ```
   git init
   ```

3. Create a new file in the directory and add some content to it.

   ```
   touch README.md
   echo "Hello, world!" > README.md
   ```

4. Add the file to the staging area using the command `git add`.

   ```
   git add README.md
   ```

5. Commit the changes with a message using the command `git commit`.

   ```
   git commit -m "Initial commit"
   ```

6. Create a new branch called `feature-branch` using the `git branch` command.

   ```
   git branch feature-branch
   ```

7. Switch to the new branch using the `git checkout` command.

   ```
   git checkout feature-branch
   ```

8. Make some changes to the file and commit them.

   ```
   echo "This is a new feature." >> README.md
   git add README.md
   git commit -m "Added a new feature to README.md"
   ```

9. Switch back to the main branch using the `git checkout` command.

   ```
   git checkout master
   ```

10. Create a new branch called `bugfix-branch` using the `git branch` command.

    ```
    git branch bugfix-branch
    ```

11. Switch to the new branch using the `git checkout` command.

    ```
    git checkout bugfix-branch
    ```

12. Make some changes to the file to fix a bug and commit them.

    ```
    sed -i '' 's/world/universe/g' README.md
    git add README.md
    git commit -m "Fixed a bug in README.md"
    ```

13. Switch back to the main branch using the `git checkout` command.

    ```
    git checkout master
    ```

14. Merge the changes from `feature-branch` into `master` using the `git merge` command.

    ```
    git merge feature-branch
    ```

15. Merge the changes from `bugfix-branch` into `master` using the `git merge` command.

    ```
    git merge bugfix-branch
    ```

Congratulations, you have successfully merged two branches in Git! Now both the new feature and bug fix are incorporated into the main codebase.




Deleting Data: 

Working Directory Files 

Unstaged Changes 

Staged Changes 

Latest Commits  

Branches 

 

 

 

Working Directory files: 

 

To delete a file and commit the changes in Git, you can use the following commands: 

  

1. To delete the file: `git rm filename` 

  

   This will remove the file from your local repository. 

  

2. To commit the changes: `git commit -m "Delete filename"` 

  

   This will commit the changes to your local repository along with a message describing the changes made. 

  

  

For example, if you want to delete a file named "example.txt" and commit the changes, you can use the following commands: 

  

``` 

git rm example.txt 

git commit -m "Delete example.txt" 

git push 

```  

  

Note that these commands assume you are currently in the Git repository directory and have the necessary permissions to make changes. 

 

 

How to restore a file: 

 

The `git restore` command is used to restore files in a Git repository. It can be used to restore files to a previous commit or to discard local changes made to a file. Here are some examples: 

  

- To restore a file to its state in the last commit: `git restore filename` 

  

  This will replace the contents of the file with the version in the last commit. 

  

- To restore a file to its state in a specific commit: `git restore --source=commit_hash filename` 

  

  This will replace the contents of the file with the version in the specified commit. 

 

  

For example, if you want to restore a file named "example.txt" to its state in the last commit, you can use the following command: 

  

``` 

git restore example.txt 

``` 

  

If you want to discard local changes made to the file and restore it to its state in the last commit, you can use the following command: 

  

``` 

git restore --staged example.txt 

``` 

  

Note that these commands assume you are currently in the Git repository directory and have the necessary permissions to make changes. 

 

 

 

The `git checkout <file_name>` command is used to discard changes made to a specific file in the working directory and replace it with the version from the most recent commit. This can be useful if you have made changes to a file and want to discard those changes and start over with the version from the last commit. 

  

Here's an example:  

  

Suppose you have made changes to a file named "example.txt" and want to discard those changes and restore the file to its state in the last commit. You can use the following command: 

  

``` 

git checkout example.txt 

``` 

  

This will replace the contents of "example.txt" with the version from the most recent commit, effectively discarding any local changes made to the file. 

  

Note that if you have already staged changes to the file using `git add`, you will need to unstage those changes first using `git reset` before using `git checkout` to discard the changes in the working directory. 

 

 

 

GIT Restore: 

 

Here's an example of how to use the `git restore` command and some of its use cases: 

  

Suppose you have made changes to a file named "example.txt" and want to restore it to its state in the last commit. You can use the following command: 

  

``` 

git restore example.txt 

``` 

  

This will replace the contents of "example.txt" with the version from the most recent commit, effectively discarding any local changes made to the file. 

  

Use cases for `git restore` include: 

  

1. Discarding local changes: If you have made changes to a file and want to discard those changes and start over with the version from the last commit, you can use `git restore` to restore the file to its previous state. 

  

2. Unstaging changes: If you have staged changes to a file using `git add` and want to unstage those changes, you can use `git restore --staged` followed by the filename to unstage the changes. 

  

3. Reverting to a previous commit: If you want to revert a file to its state in a previous commit, you can use `git restore --source=<commit>` followed by the filename to restore the file to its state in the specified commit. 

  

4. Restoring deleted files: If you have accidentally deleted a file and want to restore it, you can use `git restore` followed by the filename to restore the file to its previous state. 

  

Note that the `git restore` command was introduced in Git 2.23 and replaces the older `git checkout -- <file>` command for restoring files. 

 

 

Undo the staged Changes: 

 

 

This will unstage all changes that you have added to the staging area. If you want to unstage a specific file, you can specify the file name after the HEAD parameter: 

  

  

``` 

git reset HEAD <file> 

git checkout <file> 

``` 

  

The first command `git reset HEAD <file>` will unstage the changes for the specified file. The second command `git checkout <file>` will discard the changes made to the file and restore it to the last committed state. 

  

Note that if you have made changes to multiple files, you can use `git reset` to unstage all changes and then use `git checkout` to restore all files to the last committed state: 

  

``` 

git reset HEAD 

git checkout . 

``` 

  

This will unstage all changes and restore all files to the last committed state. 

 

 

 

 

 

 

 

 

 

 

 
