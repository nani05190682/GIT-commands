

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

