Here's a practical exercise to help your students get hands-on experience with Git merging. This will allow them to practice both fast-forward and three-way merges, including resolving merge conflicts.

---

## **Git Merge Practice Exercise**

### **Objective**:
- Understand the difference between fast-forward and three-way merges.
- Learn how to resolve merge conflicts.

---

### **Step 1: Setting Up a Test Repository**

1. **Create a new directory and initialize a Git repository**:
    ```bash
    mkdir git-merge-practice
    cd git-merge-practice
    git init
    ```

2. **Create a `main` branch with an initial commit**:
    ```bash
    echo "This is the main branch." > file.txt
    git add file.txt
    git commit -m "Initial commit on main branch"
    ```

---

### **Scenario 1: Fast-Forward Merge**

3. **Create a new branch (`feature-1`) and make changes**:
    ```bash
    git checkout -b feature-1
    echo "Adding a feature in feature-1 branch." >> file.txt
    git add file.txt
    git commit -m "Add feature in feature-1 branch"
    ```

4. **Switch back to `main` and perform a fast-forward merge**:
    ```bash
    git checkout main
    git merge feature-1
    ```

5. **Verify the merge result**:
    ```bash
    cat file.txt
    git log --oneline
    ```

- **Expected Outcome**: The changes from `feature-1` are directly merged into `main` without creating a new merge commit.

---

### **Scenario 2: Three-Way Merge with Merge Conflicts**

6. **Create two new branches from `main`**:
    ```bash
    git checkout main
    git checkout -b feature-2
    git checkout -b feature-3
    ```

7. **Make different changes in both branches**:

    - On `feature-2`:
      ```bash
      git checkout feature-2
      echo "Update from feature-2 branch." >> file.txt
      git add file.txt
      git commit -m "Update file.txt in feature-2 branch"
      ```

    - On `feature-3`:
      ```bash
      git checkout feature-3
      echo "Conflicting update from feature-3 branch." >> file.txt
      git add file.txt
      git commit -m "Update file.txt in feature-3 branch"
      ```

8. **Switch back to `main` and merge `feature-2` (no conflicts expected)**:
    ```bash
    git checkout main
    git merge feature-2
    ```

9. **Now, try to merge `feature-3` into `main`**:
    ```bash
    git merge feature-3
    ```

- **Expected Outcome**: A merge conflict occurs because both `feature-2` and `feature-3` updated the same lines in `file.txt`.

10. **Identify and resolve the conflict**:
    ```bash
    git status
    ```

    - Open `file.txt` in a text editor and manually resolve the conflict.
    - After resolving, mark the file as resolved:
      ```bash
      git add file.txt
      git commit -m "Resolved merge conflict between feature-2 and feature-3"
      ```

11. **If you want to abort the merge** (instead of resolving it):
    ```bash
    git merge --abort
    ```

---

### **Review and Clean Up (Optional)**

12. **Review the commit history**:
    ```bash
    git log --graph --oneline
    ```

13. **Delete the branches (if no longer needed)**:
    ```bash
    git branch -d feature-1
    git branch -d feature-2
    git branch -d feature-3
    ```

---

