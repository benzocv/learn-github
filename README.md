# Github Command Cheat Sheet

A quick reference guide for common and advanced Git commands with examples and detailed explanations.

---

## Configuration

| Command                                              | Description                                 | Example                                               |
| ---------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------- |
| `git config --global user.name "foo"`              | Sets the global username.                   | `git config --global user.name "John Doe"`          |
| `git config --global user.email "foo@example.com"` | Sets the global email.                      | `git config --global user.email "john@example.com"` |
| `git config --list`                                | Displays the list of global configurations. | `git config --list`                                 |

---

## Branches

| Command                        | Description                                                                            |
| ------------------------------ | -------------------------------------------------------------------------------------- |
| `git branch foo`             | Create a new branch named `foo`. Example: `git branch feature-login`               |
| `git branch -d foo`          | Deletes a branch named `foo`. Example: `git branch -d feature-login`               |
| `git switch foo`             | Switch to the branch `foo`. Example: `git switch main`                             |
| `git switch -c\|--create foo` | Create and switch to a new branch `foo`. Example: `git switch -c feature-search`   |
| `git restore foo.js`         | Undo all changes to the file `foo.js` in the working directory.                      |
| `git checkout foo.js`        | Undo all changes to the file `foo.js` (legacy command; use `git restore` instead). |
| `git checkout foo`           | Switch to branch `foo` (legacy command; use `git switch` instead).                 |
| `git checkout -b foo`        | Create and switch to branch `foo` (legacy command; use `git switch -c` instead).   |
| `git merge foo`              | Merge branch `foo` into the current branch. Example: `git merge feature-update`    |

---

## Pulling

| Command                       | Description                                                                                                                  |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `git pull --rebase --prune` | Pull the latest changes from the remote repository, rebase local changes, and remove branches that no longer exist remotely. |

---

## Staged Changes

| Command                         | Description                                                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `git add file.txt`            | Stage a file named `file.txt` for commit. Example: `git add index.html`                                               |
| `git add -p\|--patch file.txt` | Stage parts of the changes in a file interactively. Example:`git add -p app.js`                                         |
| `git mv file1.txt file2.txt`  | Rename or move a file. Example:`git mv old-name.txt new-name.txt`                                                       |
| `git rm --cached file.txt`    | Remove a file from the staging area without deleting it from the working directory. Example:`git rm --cached debug.log` |
| `git rm --force file.txt`     | Unstage and delete a file from the working directory. Example:`git rm --force unused.js`                                |
| `git reset HEAD`              | Unstage all changes but keep them in the working directory.                                                               |
| `git reset --hard HEAD`       | Unstage and delete all changes in the working directory.**Use with caution** as it cannot be undone.                |
| `git clean -f\|--force -d`     | Recursively remove untracked files and directories. Example:`git clean -fd`                                             |
| `git clean -f\|--force -d -x`  | Recursively remove untracked and ignored files. Example:`git clean -fdx`                                                |

---

## Changing Commits

| Command                                    | Description                                                                                                            |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| `git reset 5720fdf`                      | Reset the current branch to a specific commit without modifying the working directory.                                 |
| `git reset HEAD~1`                       | Reset the current branch to the previous commit while keeping changes in the working directory.                        |
| `git reset --hard 5720fdf`               | Reset the current branch and working directory to a specific commit.**This will erase all uncommitted changes.** |
| `git commit --amend -m "New message"`    | Modify the last commit message. Example:`git commit --amend -m "Fix typo in documentation"`                          |
| `git commit --fixup 5720fdf`             | Create a commit to fix or amend the specified commit.                                                                  |
| `git revert 5720fdf`                     | Create a new commit to undo changes introduced by a specific commit.                                                   |
| `git rebase --interactive [origin/main]` | Rebase the current branch interactively on top of the main branch. Example:`git rebase --interactive origin/main`    |
| `git rebase --interactive 5720fdf`       | Rebase to a specific commit interactively.                                                                             |
| `git rebase --continue`                  | Continue the rebase process after resolving conflicts.                                                                 |
| `git rebase --abort`                     | Abort an ongoing rebase operation.                                                                                     |
| `git cherry-pick 5720fdf`                | Copy a specific commit to the current branch.                                                                          |

---

## Compare

| Command                  | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| `git diff`             | Show changes between the working directory and the index. |
| `git diff HEAD HEAD~2` | Compare the current commit with two commits back.         |
| `git diff main other`  | Show changes between two branches.                        |

---

## View

| Command                                  | Description                                                                |
| ---------------------------------------- | -------------------------------------------------------------------------- |
| `git log`                              | View the commit history. Example:`git log --oneline` for a concise view. |
| `git log --patch`                      | View commits along with their changes.                                     |
| `git log --decorate --graph --oneline` | Visualize the commit history as a graph.                                   |
| `git show HEAD`                        | Display details of the current commit.                                     |
| `git blame file.txt`                   | See who made each change to a file.                                        |

---

## Stash

| Command                           | Description                                              |
| --------------------------------- | -------------------------------------------------------- |
| `git stash push -m "Message"`   | Save uncommitted changes to the stash with a message.    |
| `git stash --include-untracked` | Stash all uncommitted and untracked files.               |
| `git stash list`                | View all stashed changes.                                |
| `git stash apply`               | Apply the last stashed changes to the working directory. |
| `git stash clear`               | Delete all stashes.                                      |

---

## Tags

| Command                                                | Description                                                               |
| ------------------------------------------------------ | ------------------------------------------------------------------------- |
| `git tag`                                            | List all tags.                                                            |
| `git tag -a\|--annotate 0.0.1 -m\|--message "Message"` | Create an annotated tag. Example:`git tag -a v1.0 -m "Initial release"` |
| `git push --tags`                                    | Push tags to a remote repository.                                         |

---

## Remote

| Command                           | Description                                                |
| --------------------------------- | ---------------------------------------------------------- |
| `git remote -v`                 | View the URLs of remote repositories.                      |
| `git remote add upstream <url>` | Add a new remote repository named `upstream`.            |
| `git push --force-with-lease`   | Push changes while ensuring no conflicting remote updates. |
| `git push --tags`               | Push all tags to the remote repository.                    |

---

## Submodules

| Command                  | Description                         |
| ------------------------ | ----------------------------------- |
| `git submodule status` | Check the status of all submodules. |

**Submodule Workflow**:

1. Sync: `git submodule sync`
2. Initialize: `git submodule init`
3. Update: `git submodule update`

---

## Notes

- Always commit and push frequently to avoid losing progress.
- Use `git rebase` cautiously to avoid rewriting shared commit history.
- Use `git stash` for temporary work, but do not rely on it as a long-term backup.
