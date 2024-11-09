

## **Creating and Managing Git Branches**

### **1. Creating a Branch**
Branches in Git allow you to create separate lines of development within the same repository. This is especially useful when working on new features, fixing bugs, or experimenting without affecting the main codebase.

- **Command**:
  ```bash
  git branch <branch-name>
  ```
- **Example**:
  ```bash
  git branch feature/login
  ```
  This command creates a new branch called `feature/login` but does not switch to it. The new branch is created from your current HEAD (the latest commit in your current branch).

- **Note**: Use branches to isolate work, so your changes don’t interfere with the main codebase.

### **2. Switching Branches**
After creating a branch, you'll often want to switch to it so you can start working on that branch.

#### **Using `git checkout` (Legacy)**
- **Command**:
  ```bash
  git checkout <branch-name>
  ```
- **Example**:
  ```bash
  git checkout feature/login
  ```
  This command switches your working directory to the `feature/login` branch.

#### **Using `git switch` (Recommended)**
- **Command**:
  ```bash
  git switch <branch-name>
  ```
- **Example**:
  ```bash
  git switch feature/login
  ```
  The `git switch` command is a newer and more intuitive way to change branches, introduced in Git 2.23. It’s preferred over `git checkout` for switching branches because it avoids confusion with checking out files.

- **Why use `git switch`?**
  - **Clarity**: Explicitly designed for branch switching, making it more user-friendly.
  - **Safety**: Reduces the risk of accidentally checking out files.

### **3. Listing Branches**
You can view all branches in your Git repository to see which branches exist and which one you are currently on.

- **Command**:
  ```bash
  git branch
  ```
- **Example Output**:
  ```
  main
  * feature/login
  hotfix-123
  ```
  - The `*` next to `feature/login` indicates that it’s the currently active branch.

- **Additional Options**:
  - `git branch -a`: Lists all local and remote branches.
  - `git branch -r`: Lists only remote branches.

### **4. Renaming Branches**
If you want to rename an existing branch, Git provides a straightforward command.

- **Command**:
  ```bash
  git branch -m <new-branch-name>
  ```
- **Example**:
  ```bash
  git branch -m feature/authentication
  ```
  This renames the current branch to `feature/authentication`.

- **Renaming a Different Branch**:
  ```bash
  git branch -m old-branch-name new-branch-name
  ```

### **5. Deleting Branches**
Branches that are no longer needed can be safely deleted to keep your repository clean.

#### **Deleting a Local Branch**
- **Command**:
  ```bash
  git branch -d <branch-name>
  ```
- **Example**:
  ```bash
  git branch -d feature/login
  ```
  This deletes the `feature/login` branch, but only if it has been fully merged. If the branch contains unmerged changes, Git will warn you.

- **Force Deletion**:
  ```bash
  git branch -D <branch-name>
  ```
  Use `-D` (uppercase) to forcefully delete a branch even if it has unmerged changes.

#### **Deleting a Remote Branch**
To delete a branch from a remote repository (like GitHub), use the following command:

- **Command**:
  ```bash
  git push origin --delete <branch-name>
  ```
- **Example**:
  ```bash
  git push origin --delete feature/login
  ```
  This command removes the `feature/login` branch from the remote repository. Note that it does not delete the local branch.

- **Alternative Method**:
  ```bash
  git push origin :<branch-name>
  ```

---

### **Summary Table**

| **Action**                  | **Command**                             | **Description**                                       |
|----------------------------|----------------------------------------|-------------------------------------------------------|
| Create a branch           | `git branch <branch-name>`             | Creates a new branch.                                 |
| Switch branches (legacy)  | `git checkout <branch-name>`           | Switches to the specified branch. (Legacy)            |
| Switch branches (recommended) | `git switch <branch-name>`           | Switches to the specified branch.                     |
| List branches             | `git branch`                           | Lists all local branches.                             |
| Rename branch             | `git branch -m <new-branch-name>`      | Renames the current branch.                           |
| Delete local branch       | `git branch -d <branch-name>`          | Deletes a local branch (only if merged).              |
| Force delete local branch | `git branch -D <branch-name>`          | Force deletes a local branch (even if not merged).    |
| Delete remote branch      | `git push origin --delete <branch-name>`| Deletes a branch from the remote repository.          |

---

### **Practical Exercises**
1. **Create a branch** named `feature/cart`, switch to it, and make a commit.
2. **Rename the branch** to `feature/shopping-cart`.
3. **Delete the branch locally and remotely**.





**Branch Navigation and Management** 

---

## **Branch Navigation and Management**

### **1. Checking Branch History**
Understanding the commit history is crucial when working with multiple branches. Git provides powerful commands to visualize the history, making it easier to navigate between branches and understand changes.

#### **Command**: Viewing a Simplified Commit History
```bash
git log --oneline --graph --all
```

- **Breakdown of Options**:
  - `--oneline`: Displays each commit in a single line for a cleaner view.
  - `--graph`: Shows a text-based graphical representation of the branch structure.
  - `--all`: Displays the commit history of all branches, not just the current one.

- **Example Output**:
  ```
  * a1b2c3d (HEAD -> feature/cart) Add shopping cart functionality
  | * 4f5e6g7 (origin/main, main) Fix bug in user authentication
  |/
  * 8h9i0j1 Update README with setup instructions
  * 2k3l4m5 Initial project setup
  ```
  - The `*` symbols represent commits, with branch names shown in parentheses.
  - This view helps you quickly understand the branching and merging history.

#### **Use Case**:
- Great for getting a quick overview of your project's branch structure.
- Useful when you need to see how your feature branch diverges from the main branch.

### **2. Viewing Changes Between Branches**
When collaborating on a project, it's essential to review differences between branches before merging. Git allows you to see what has changed between two branches.

#### **Command**: Comparing Branches
```bash
git diff <branch1>..<branch2>
```

- **How It Works**:
  - Shows the differences between the tip of `<branch2>` and the tip of `<branch1>`.
  - Useful for reviewing changes before merging branches.

- **Example**:
  ```bash
  git diff main..feature/cart
  ```
  This command compares the `feature/cart` branch against the `main` branch. It highlights what changes exist in `feature/cart` that are not in `main`.

- **Output**:
  ```
  diff --git a/index.html b/index.html
  index 123abc4..567def8 100644
  --- a/index.html
  +++ b/index.html
  @@ -12,7 +12,7 @@
  - <h1>Welcome to My Website</h1>
  + <h1>Welcome to Our E-commerce Store</h1>
  ```
  - Lines prefixed with `+` are additions.
  - Lines prefixed with `-` are deletions.

#### **Other Useful Options**:
- **View changes for specific files**:
  ```bash
  git diff <branch1>..<branch2> -- <filename>
  ```
- **Compare commits with merge base**:
  ```bash
  git diff <branch1>...<branch2>
  ```
  Using three dots (`...`) compares `<branch2>` against the common ancestor with `<branch1>`, which is helpful for reviewing merge requests.

### **3. Practical Examples**

#### **Example 1: Visualizing All Branches**
1. Run the following command to see the history of all branches:
   ```bash
   git log --oneline --graph --all
   ```
2. Observe the commit graph to identify branching points and merges.

#### **Example 2: Checking Differences Before a Merge**
1. Let's say you want to check what changes are in the `feature/login` branch that are not in the `main` branch:
   ```bash
   git diff main..feature/login
   ```
2. Review the output to ensure no unintended changes are introduced.

---

### **Summary Table**

| **Action**                            | **Command**                                   | **Description**                                         |
|---------------------------------------|----------------------------------------------|---------------------------------------------------------|
| View commit history for all branches  | `git log --oneline --graph --all`            | Displays a simplified history with branch structure.    |
| Compare two branches                  | `git diff <branch1>..<branch2>`              | Shows changes between the two branches.                 |
| Compare commits with merge base       | `git diff <branch1>...<branch2>`             | Shows changes from the common ancestor of two branches. |

---

### **Hands-on Lab**
1. **Lab Setup**:
   - Create two branches: `feature/header` and `feature/footer`.
   - Make a few commits on each branch.

2. **Exercise 1**: 
   - Use `git log --oneline --graph --all` to view the commit history.
   
3. **Exercise 2**: 
   - Use `git diff feature/header..feature/footer` to compare changes between the two branches.
