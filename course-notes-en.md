# 📚 Version Control: Git and GitHub Course Lecture Notes
**Instructor:** Atil Samancioglu  

---

## 💻 1. Basic Terminal and System Commands

The terminal (command line) is the essential tool for working efficiently in the software development process.

* **`cmd`:** Opens the Command Prompt window on the Windows operating system.
* **`Windows + R`:** Opens the Run dialog box to quickly trigger a program or command.
* **`ipconfig`:** Lists the local network IP addresses and network configuration details of the computer.
* **`pwd` (Print Working Directory):** Prints the full file path of the currently active folder to the terminal screen.
* **`ls`:** Lists the names of the files and subfolders inside the active folder.
* **`ls -la`:** Lists all files in the active folder, including hidden files (such as `.git` starting with a dot) and detailed permission information.
* **`cd <folder_name>` (Change Directory):** Allows entry into the specified subfolder.
* **`cd ..`:** Moves back to the previous folder (up one level) in the file directory.
* **`Tab Key`:** Automatically completes the typed commands or file names in the terminal.
* **`mkdir <folder_name>` (Make Directory):** Creates a brand new folder from scratch in the active directory.
* **`touch <file_name>.<extension>`:** Creates an empty file with the specified name and extension.
* **`rm <file_name>.<extension>` (Remove):** Permanently deletes the specified file.
* **`rm -rf <folder_name>`:** Forcefully and permanently deletes the specified folder and all its subfiles.
* **`clear`:** Clears the old command history on the terminal screen, opening a clean line.

---

## 🛠️ 2. Initial Git Setup and Identity Configurations

After Git is installed, global identity settings are configured only once so that the history records who made the entries.

* **`git --version`:** Shows the current version of the Git software installed on the computer.
* **`git` / `git --help`:** Lists the core Git commands available and the help documentation.
* **`git config --global user.name "<first_last_name>"`:** Defines the global username to be stamped as the author name on all commits to be made.
* **`git config user.name`:** Used to verify the currently defined username in the system on the screen.
* **`git config --global user.email "<email>"`:** Defines the global email address to be stamped as the author signature on all commits to be made.
* **`git config user.email`:** Used to verify the currently defined email address in the system on the screen.

---

## 🎯 3. Core Git Concepts and Workflow

The Git architecture consists of three core areas: Working Directory, Staging Area, and Local Repository.

* **Local Repository:** The hidden database (`.git` folder) where Git stores all history, branches, commits, and version records on your computer.
* **Index / Staging Area:** The waiting room between the changes made in your project and the commit process that saves these changes permanently.
* **Commit:** The process of permanently sealing the current state (Snapshot) of the changes made in the project into the local database and leaving a mark in history.
* **`git init` (Initialize):** Converts an ordinary folder into a local Git repository that Git can track. This is the first and most fundamental command. A `git status` check must be performed before running `git init` anywhere.
* **`git status`:** Summarizes the current Git status of the project; it shows which files have been modified and which ones are awaiting approval in the staging area.
* **`git add <file_name>`:** Moves the changes made in the specified file to the preparation area (Staging Area).
* **`git add .`:** Transfers all new additions, deletions, and modifications made in the working directory to the staging area in a single move.
* **`git commit -m "<commit_message>"`:** Seals all files in the staging area, creating a permanent point in history. It is preferred that messages be short, concise, and usually written in English.
* **`git log`:** Lists all commits made in the project chronologically, with the newest at the top. When the log list gets long, the `END` warning appears at the bottom of the terminal line. To exit this screen and return to the normal terminal line, the **`q` (quit)** key on the keyboard must be pressed.

---

## 🙈 4. Ignoring Files and Configuration (`.gitignore`)

Private data, passwords, or log folders that should not be shared with everyone in projects should never be taken to the staging area and sent to GitHub.

* **`.gitignore`:** A special configuration file where you specify the names of files and folders that you do not want Git to track, save, or send to a remote server.
* *Open Source Templates:* Every software language (Python, Node, Java, etc.) has its own list of unnecessary files that should be kept away. When starting a project at world standards, ready-made language templates can be included in the project via the [GitHub Gitignore Repository](https://github.com).

---

## 🌿 5. Branch Management and Merging

Branches are secure workspaces created to develop features, fix bugs, or run experiments independently without risking the main code line (usually called `main` or `master`).

* **Head:** The active pointer in Git architecture showing exactly where, on which branch, or on which commit we currently stand.
* **`git branch`:** Lists all branches present in the current repository and highlights the active branch.
* **`git branch <new_branch_name>`:** Creates a new independent working branch separate from the main branch.
* **`git switch <branch_name>`:** Switches into the specified branch, moving the `HEAD` pointer there.
* **`git merge <branch_name>`:** A command used to merge changes made in different branches into a single branch. Whichever branch you want to pull code into, you must first switch to that branch.
* **Fast-Forwarding:** A type of fast and seamless merging performed by directly moving the tip of the target branch to the very front of the main branch without changing history, since there is no conflicting history between the two branches.
* **Merge Conflict:** The error where Git cannot automatically decide which change to accept in the same line of the same file when you want to merge two different branches, thereby halting the merge.

---

## 📥 6. Uncommitted Changes Leak and Stash Mechanism

In Git, branches only track committed history. The working directory and the staging area do not belong to a branch yet; they are a shared area. When you make changes in a branch and do not commit them, if you switch to another branch, Git tries to preserve these uncommitted changes and carries them over to the branch you switched to.

### Solution Pathways:
1. **Committing:** Permanently saving changes to the current branch before switching branches.
2. **Discarding Changes (`git restore`):** Completely giving up on the changes made.
   * **`git restore <file_name>`:** Used to restore (reload) files in the working directory or staging area to their old/desired state.
3. **Stashing (`git stash`):** Temporarily moving code under development to a side area (your stash) without committing it, thereby cleaning the workspace.
   * **`git stash`:** Allows you to temporarily shelve changes you are working on but have not yet committed, without losing them, keeping the working directory perfectly clean.
   * **`git stash list`:** Displays all change packages stashed away in a chronological list.
   * **`git stash pop`:** Restores the latest change package placed in the temporary memory (stash) onto the current code and permanently deletes that package from the stash.
   * **`git stash apply stash@{<index>}`:** Takes the specific package at a certain index in your stash list (e.g., `stash@{0}`) and applies it to your current branch but does not delete that package from the stash list.
   * **`git stash clear`:** Permanently deletes (resets) all change packages accumulated in your stash in a single move.

---

## 🕰️ 7. Navigating Git History and HEAD States

Returning to old commits is a critical process for inspecting a stable moment of the project in the past.

* **`git checkout <commit_ID>`:** Used to switch between branches and go to an old commit to inspect the history.
* **Detached HEAD:** A state in Git where the `HEAD` pointer you are currently working on points directly to a specific commit (a point in time) rather than a branch.
* **Reattached HEAD:** The name given to the process of escaping the "Detached HEAD" state and reconnecting the `HEAD` pointer back to a normal and secure branch.

### Ways to Recover from a Detached HEAD State:

* **Scenario A (If No Changes Were Made):** If you just looked at the history and made no modifications, you can safely return to your main branch and reattach HEAD without any additional steps:
  ```bash
  git switch master  # or git switch main
  ```

* **Scenario B (If Changes Were Made and Need to Be Saved):** If you ran experiments while on the past commit and want to preserve this code, you must follow these steps in order:
  ```bash
  git branch <new_branch_name>   # Generates a new branch on the past commit
  git switch <new_branch_name>   # Switches to the new branch and attaches the HEAD pointer
  git add .                      # Takes changes to the staging area
  git commit -m "Your Message"   # Makes the changes permanent in the new branch
  ```

---

## 🕰️ 8. Advanced History Management (Reset & Revert)

Git includes commands suitable for different scenarios to undo erroneous operations or edit history.

* **`git reset <commit_ID>`:** Cancels all commits thrown after the selected commit moment. The most important feature of this command is that even if the commits are deleted, the code changes you wrote inside those commits are not deleted from your computer (the codes remain in the working directory).
* **`git reset --hard <commit_ID>`:** One of the sharpest and most irreversible commands in Git architecture. It aligns the history of the project, the staging area, and the working directory on your computer exactly back to the specified commit moment. When this command is run, all commits made after the selected commit, files added to the stage, and all unrecorded code changes are completely deleted.
* **`git revert <commit_ID>`:** A secure undo command that creates a **new counter-commit** that reverses the changes made by a specific commit in the past without touching the current history line of your project. It is the safest undo method used in team collaborations since it does not wipe old commits from history.

---

## 🔍 9. Code Comparison (Git Diff)

Used to inspect code differences between different stages or time periods of the project line by line.

* **`git diff`:** Shows the code differences between the current state of files in the working directory and the last commit. It lists only the changes that have not yet been taken to the stage (`git add`).
* **`git diff HEAD`:** Compares all current code changes made in the working directory on your computer, regardless of their status (both those added to the stage and those not added), against the last commit.
* **`git diff <commit_ID_1> <commit_ID_2>`:** Compares all code differences line by line between two specific separate commits (time frames) in Git history. When writing the command, a space can be left between commit IDs, or a double dot (`..`) sign can be placed.
* **`git diff <branch_name_1> <branch_name_2>`:** Lists the code and structure differences between two specified separate branches. A space can be left between branch names, or a double dot (`..`) sign can be inserted.

---

## 🛤️ 10. Linearizing History (Rebase)

* **`git rebase <target_branch_name>`:** The process of moving the starting point (root) of the active branch under development to the latest commit of the target branch, thereby rewriting history linearly (in a straight line). The main purpose of this process is to purify the project history from complex branching and unnecessary merge commits, making everything look clean as if all codes were written one after another on a single line.

---

## ☁️ 11. Remote Repository Management (GitHub Integration)

Platform tools that enable the processes conducted with Git on the local computer to be stored on the cloud and opened to teamwork.

* **GitHub:** A cloud-based software development and collaboration platform that uses the Git architecture, allowing software developers to store, manage, share, and provide version control for their code.
* **`git remote add origin https://github.com<username>/<repository_name>.git`:** The fundamental command that establishes a digital connection bridge between the local Git repository on the computer and the remote repository opened on GitHub.
* **`origin`:** The short alias of this long internet address inside Git. According to world standards, the main server address is always named `origin`. This way, instead of typing that long internet address one by one every time you push, just typing `origin` is sufficient.
* **`git push -u origin <branch_name>`:** The command that sets up a permanent tracking bridge between the local branch and the branch on the remote server when uploading codes to GitHub for the first time (e.g., `git push -u origin main or master`).
* **`git push`:** The fundamental command that uploads all code changes written, staged (`git add`), and approved (`git commit`) on the computer to the remote server on GitHub.
* **`git push origin <feature_branch_name>`:** Used to upload other side branches (e.g., the `feat` branch) independently to the GitHub server outside of the main branch.
* **Pull Request (PR):** The process where a developer requests permission, review, and approval from other team members and project managers to add code from their own branch into the main branch (`main`/`master`) of the project.
* **`git branch -r`:** The inspection command used to list all remote branches on the GitHub side recorded on the local computer.
* **`git fetch origin`:** A secure preview command that checks and downloads all new changes, history, and branches from GitHub to the computer but does not touch your current live code.
* **`git fetch origin master`:** A special command that targets and downloads only the new commits (updates) in the specified branch (e.g., `master` or `main`) without touching any other branch on GitHub.
* **`git pull origin <branch_name>`:** An synchronization command used to download the most up-to-date codes and changes from GitHub and automatically merge them with your local codes (e.g., `git pull origin master`).
* **`git pull = git fetch + git merge`:** The golden formula showing that the `git pull` command is a combination of two commands that first downloads data (`fetch`) and then merges it with local code (`merge`) in the background.
* **`git clone <address>`:** The fundamental command used to download all history, files, and branches of an existing project standing on GitHub to your computer for the first time. The HTTPS or SSH address copied by pressing the green "Code" button on the project page is used.
* **Fork:** The process of making an exact copy of a project standing on someone else's or a company's GitHub account onto your own GitHub account.
* **Collaborators:** Other software developers whom the repository owner explicitly authorizes to directly intervene in, write code for, and update (`push`) a private or public repository on GitHub.
