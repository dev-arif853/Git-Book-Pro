# Git Command Cheat Sheet

A comprehensive reference guide for all essential Git commands.

---

## Table of Contents

- [Configuration](#configuration)
- [Repository Creation](#repository-creation)
- [Making Changes](#making-changes)
- [Committing](#committing)
- [Branching](#branching)
- [Merging](#merging)
- [Rebasing](#rebasing)
- [Undoing Changes](#undoing-changes)
- [Stashing](#stashing)
- [Remote Repositories](#remote-repositories)
- [Fetching and Pulling](#fetching-and-pulling)
- [Pushing](#pushing)
- [Tagging](#tagging)
- [Viewing History](#viewing-history)
- [Comparing](#comparing)
- [Finding](#finding)
- [Cherry-picking](#cherry-picking)
- [Submodules](#submodules)
- [Working with Patches](#working-with-patches)
- [Archive](#archive)
- [Maintenance](#maintenance)
- [Advanced](#advanced)
- [Useful Git Aliases](#useful-git-aliases)
- [Best Practices](#best-practices)

---

## Configuration

| Command | Description |
|---------|-------------|
| `git config --global user.name "[name]"` | Set the name you want attached to your commit transactions |
| `git config --global user.email "[email]"` | Set the email you want attached to your commit transactions |
| `git config --global color.ui auto` | Enable helpful colorization of command line output |
| `git config --list` | List all configuration settings |
| `git config --global --edit` | Open global config file in text editor |
| `git config --global alias.[alias] [command]` | Create a shortcut for a Git command |

---

## Repository Creation

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new Git repository in the current directory |
| `git init [directory]` | Create a new local repository in the specified directory |
| `git clone [url]` | Clone a repository from a remote source |
| `git clone [url] [directory]` | Clone a repository into a specific directory |
| `git clone --depth [depth] [url]` | Clone with limited commit history (shallow clone) |

---

## Making Changes

| Command | Description |
|---------|-------------|
| `git status` | Show the status of modified files in the working directory |
| `git status -s` | Show status in short format |
| `git diff` | Show unstaged changes between working directory and index |
| `git diff --staged` | Show staged changes between index and last commit |
| `git diff [commit1] [commit2]` | Show differences between two commits |
| `git add [file]` | Add a file to the staging area |
| `git add .` | Add all modified and new files to staging area |
| `git add -A` | Add all changes (including deletions) to staging area |
| `git add -p` | Interactively choose portions of files to add to staging |
| `git rm [file]` | Remove a file from working directory and staging area |
| `git rm --cached [file]` | Remove a file from staging area only, keep in working directory |
| `git mv [old-path] [new-path]` | Move or rename a file |

---

## Committing

| Command | Description |
|---------|-------------|
| `git commit -m "[message]"` | Commit staged changes with a descriptive message |
| `git commit -a -m "[message]"` | Commit all tracked file changes (skip staging) |
| `git commit --amend` | Modify the last commit (message or content) |
| `git commit --amend --no-edit` | Modify the last commit without changing the message |
| `git commit --allow-empty -m "[message]"` | Create a commit with no changes |
| `git commit -v` | Commit with verbose output showing diff in editor |

---

## Branching

| Command | Description |
|---------|-------------|
| `git branch` | List all local branches |
| `git branch -a` | List all local and remote branches |
| `git branch [branch-name]` | Create a new branch |
| `git branch -d [branch-name]` | Delete a branch (safe delete, prevents losing work) |
| `git branch -D [branch-name]` | Force delete a branch |
| `git branch -m [old-name] [new-name]` | Rename a branch |
| `git branch --merged` | List branches that have been merged into current branch |
| `git branch --no-merged` | List branches that have not been merged |
| `git checkout [branch-name]` | Switch to a different branch |
| `git checkout -b [branch-name]` | Create and switch to a new branch |
| `git checkout -b [branch] [remote]/[branch]` | Create and checkout a branch tracking a remote branch |
| `git switch [branch-name]` | Switch to a different branch (modern alternative to checkout) |
| `git switch -c [branch-name]` | Create and switch to a new branch |

---

## Merging

| Command | Description |
|---------|-------------|
| `git merge [branch]` | Merge specified branch into current branch |
| `git merge --no-ff [branch]` | Merge with a merge commit even if fast-forward is possible |
| `git merge --squash [branch]` | Merge and squash all commits into a single commit |
| `git merge --abort` | Abort the current merge and restore to pre-merge state |
| `git mergetool` | Open merge conflict resolution tool |

---

## Rebasing

| Command | Description |
|---------|-------------|
| `git rebase [branch]` | Reapply commits from current branch on top of another branch |
| `git rebase -i [commit]` | Interactive rebase to edit, squash, or reorder commits |
| `git rebase --continue` | Continue rebasing after resolving conflicts |
| `git rebase --abort` | Abort the rebase and restore to pre-rebase state |
| `git rebase --skip` | Skip the current commit during rebase |

---

## Undoing Changes

| Command | Description |
|---------|-------------|
| `git reset [file]` | Unstage a file while retaining changes in working directory |
| `git reset --soft [commit]` | Reset to commit, keep changes staged |
| `git reset --mixed [commit]` | Reset to commit, keep changes unstaged (default) |
| `git reset --hard [commit]` | Reset to commit, discard all changes |
| `git reset --hard HEAD` | Discard all local changes in working directory |
| `git revert [commit]` | Create a new commit that undoes changes from a previous commit |
| `git revert --no-commit [commit]` | Revert changes without automatically committing |
| `git checkout -- [file]` | Discard changes to a file in working directory |
| `git restore [file]` | Discard changes to a file (modern alternative) |
| `git restore --staged [file]` | Unstage a file |
| `git clean -fd` | Remove untracked files and directories |
| `git clean -n` | Show what would be removed by git clean (dry run) |

---

## Stashing

| Command | Description |
|---------|-------------|
| `git stash` | Save modified and staged changes for later |
| `git stash save "[message]"` | Save stash with a descriptive message |
| `git stash list` | List all stashed changesets |
| `git stash pop` | Apply most recent stash and remove it from stash list |
| `git stash apply` | Apply most recent stash but keep it in stash list |
| `git stash apply stash@{[n]}` | Apply a specific stash by index |
| `git stash drop` | Remove the most recent stash |
| `git stash drop stash@{[n]}` | Remove a specific stash |
| `git stash clear` | Remove all stashes |
| `git stash branch [branch-name]` | Create a new branch from a stash |

---

## Remote Repositories

| Command | Description |
|---------|-------------|
| `git remote` | List all remote repositories |
| `git remote -v` | List all remotes with URLs |
| `git remote add [name] [url]` | Add a new remote repository |
| `git remote remove [name]` | Remove a remote repository |
| `git remote rename [old-name] [new-name]` | Rename a remote repository |
| `git remote set-url [name] [url]` | Change the URL of a remote repository |
| `git remote show [name]` | Show information about a remote repository |
| `git remote prune [name]` | Delete stale remote-tracking branches |

---

## Fetching and Pulling

| Command | Description |
|---------|-------------|
| `git fetch` | Download objects and refs from remote repository |
| `git fetch [remote]` | Fetch from a specific remote |
| `git fetch --all` | Fetch from all remotes |
| `git fetch --prune` | Fetch and remove deleted remote branches |
| `git pull` | Fetch and merge changes from remote branch |
| `git pull [remote] [branch]` | Pull from a specific remote and branch |
| `git pull --rebase` | Fetch and rebase instead of merge |
| `git pull --ff-only` | Only pull if fast-forward is possible |

---

## Pushing

| Command | Description |
|---------|-------------|
| `git push` | Push commits to remote repository |
| `git push [remote] [branch]` | Push to a specific remote and branch |
| `git push -u [remote] [branch]` | Push and set upstream tracking branch |
| `git push --all` | Push all branches to remote |
| `git push --tags` | Push all tags to remote |
| `git push --force` | Force push (overwrites remote history) |
| `git push --force-with-lease` | Force push only if remote hasn't changed |
| `git push --delete [remote] [branch]` | Delete a remote branch |

---

## Tagging

| Command | Description |
|---------|-------------|
| `git tag` | List all tags |
| `git tag [tag-name]` | Create a lightweight tag |
| `git tag -a [tag-name] -m "[message]"` | Create an annotated tag |
| `git tag [tag-name] [commit]` | Tag a specific commit |
| `git tag -d [tag-name]` | Delete a local tag |
| `git push [remote] [tag-name]` | Push a specific tag to remote |
| `git push --tags` | Push all tags to remote |
| `git push --delete [remote] [tag-name]` | Delete a remote tag |
| `git show [tag-name]` | Show tag information and associated commit |

---

## Viewing History

| Command | Description |
|---------|-------------|
| `git log` | Show commit history for current branch |
| `git log --oneline` | Show commit history in condensed format |
| `git log --graph` | Show commit history with ASCII graph |
| `git log --all --graph --decorate` | Show full history with branches and tags |
| `git log -n [limit]` | Show only the last n commits |
| `git log --since="[date]"` | Show commits after a specific date |
| `git log --until="[date]"` | Show commits before a specific date |
| `git log --author="[name]"` | Show commits by a specific author |
| `git log --grep="[pattern]"` | Search commit messages for a pattern |
| `git log -S"[string]"` | Search for commits that add or remove a string |
| `git log --follow [file]` | Show history of a file, including renames |
| `git log [branch1]..[branch2]` | Show commits in branch2 not in branch1 |
| `git log --stat` | Show commit history with file change statistics |
| `git log -p` | Show commit history with full diff |
| `git blame [file]` | Show who modified each line of a file |
| `git show [commit]` | Show details and changes of a specific commit |
| `git show [commit]:[file]` | Show a file as it was in a specific commit |

---

## Comparing

| Command | Description |
|---------|-------------|
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git diff [commit1] [commit2]` | Compare two commits |
| `git diff [branch1]..[branch2]` | Compare two branches |
| `git diff --stat` | Show diff statistics instead of full diff |
| `git diff --name-only` | Show only names of changed files |
| `git diff --name-status` | Show names and status of changed files |

---

## Finding

| Command | Description |
|---------|-------------|
| `git grep "[pattern]"` | Search for a pattern in tracked files |
| `git grep -n "[pattern]"` | Search with line numbers |
| `git grep --count "[pattern]"` | Count matches per file |
| `git log -S"[string]"` | Find commits that added or removed a string |
| `git log --all --grep="[pattern]"` | Search commit messages across all branches |
| `git bisect start` | Start binary search for a bug-introducing commit |
| `git bisect bad` | Mark current commit as bad |
| `git bisect good [commit]` | Mark a commit as good |
| `git bisect reset` | End bisect session and return to original state |

---

## Cherry-picking

| Command | Description |
|---------|-------------|
| `git cherry-pick [commit]` | Apply changes from a specific commit to current branch |
| `git cherry-pick [commit1] [commit2]` | Apply multiple commits |
| `git cherry-pick --continue` | Continue cherry-pick after resolving conflicts |
| `git cherry-pick --abort` | Abort cherry-pick operation |
| `git cherry-pick --no-commit [commit]` | Cherry-pick without automatically committing |

---

## Submodules

| Command | Description |
|---------|-------------|
| `git submodule add [url] [path]` | Add a new submodule |
| `git submodule init` | Initialize submodules |
| `git submodule update` | Update submodules to match the parent repo |
| `git submodule update --remote` | Update submodules to latest remote commits |
| `git clone --recursive [url]` | Clone a repository including all submodules |
| `git submodule foreach [command]` | Execute a command in each submodule |

---

## Working with Patches

| Command | Description |
|---------|-------------|
| `git format-patch [commit]` | Create patch files for commits |
| `git format-patch -1 [commit]` | Create a patch for a single commit |
| `git am [patch-file]` | Apply a patch file |
| `git apply [patch-file]` | Apply changes from a patch without committing |
| `git apply --check [patch-file]` | Check if a patch can be applied cleanly |

---

## Archive

| Command | Description |
|---------|-------------|
| `git archive --format=zip HEAD > [file.zip]` | Create a zip archive of the repository |
| `git archive --format=tar HEAD \| gzip > [file.tar.gz]` | Create a compressed tar archive |
| `git archive [branch] [path] > [file]` | Archive a specific branch or path |

---

## Maintenance

| Command | Description |
|---------|-------------|
| `git gc` | Clean up unnecessary files and optimize repository |
| `git gc --aggressive` | More thorough optimization (takes longer) |
| `git prune` | Remove unreachable objects from database |
| `git fsck` | Check repository integrity |
| `git reflog` | Show reference logs (history of HEAD movements) |
| `git reflog expire --expire=now --all` | Expire all reflog entries immediately |
| `git count-objects -v` | Show repository size and object count |

---

## Advanced

| Command | Description |
|---------|-------------|
| `git worktree add [path] [branch]` | Create a new working tree for parallel work |
| `git worktree list` | List all working trees |
| `git worktree remove [path]` | Remove a working tree |
| `git filter-branch --tree-filter [command] HEAD` | Rewrite history by applying command to each commit |
| `git filter-repo` | Modern alternative to filter-branch for rewriting history |
| `git rev-parse HEAD` | Get the commit hash of HEAD |
| `git shortlog -sn` | Show commit count by author |
| `git describe --tags` | Describe current commit using most recent tag |

---

## Useful Git Aliases

| Command | Description |
|---------|-------------|
| `git config --global alias.co checkout` | Short alias for checkout |
| `git config --global alias.br branch` | Short alias for branch |
| `git config --global alias.ci commit` | Short alias for commit |
| `git config --global alias.st status` | Short alias for status |
| `git config --global alias.unstage 'reset HEAD --'` | Alias to unstage files |
| `git config --global alias.last 'log -1 HEAD'` | Show the last commit |
| `git config --global alias.lg 'log --oneline --graph --decorate'` | Pretty log format |
| `git config --global alias.visual '!gitk'` | Open gitk visualizer |

---

## Best Practices

- ✅ Commit often with meaningful messages
- ✅ Pull before you push to avoid conflicts
- ✅ Use branches for new features and experiments
- ✅ Never force push to shared branches
- ✅ Keep commits atomic and focused on single changes
- ✅ Write clear commit messages (present tense, imperative mood)
- ✅ Use .gitignore to exclude unnecessary files
- ✅ Review changes before committing (git diff)
- ✅ Test your code before committing
- ✅ Keep your main/master branch stable
- ✅ Use descriptive branch names
- ✅ Delete merged branches to keep repository clean

---

## License

This cheat sheet is released under [MIT License](https://opensource.org/licenses/MIT).

## Contributing

Feel free to submit issues or pull requests to improve this cheat sheet!

---

**Happy Git-ing! 🚀**
