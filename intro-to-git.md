# Intro to Git

**Git** tracks changes to files over time. A **repository** (repo) is a folder with history; you work in a **working tree**, stage snapshots, and record them as **commits**. **Remote** repos (e.g. on GitHub) let you share and back up that history.

---

## Start or copy a project

| Command | What it does |
|--------|----------------|
| `git clone <url>` | Download a remote repo and create a local copy with remotes already set. |
| `git init` | Turn the current folder into a new repo (creates a `.git` directory). |

---

## Daily workflow

| Command | What it does |
|--------|----------------|
| `git status` | Show changed files, what is staged, and which branch you are on. |
| `git add <file>` | Stage a file for the next commit. |
| `git add -A` or `git add .` | Stage all changes in the repo (learn the difference between them as you go). |
| `git commit -m "message"` | Save a snapshot of everything currently staged. |
| `git diff` | Show unstaged changes. |
| `git diff --staged` | Show what will go into the next commit. |

---

## History and branches

| Command | What it does |
|--------|----------------|
| `git log` | List commits (newest first). `git log --oneline` is a compact view. |
| `git branch` | List local branches; the current one is marked. |
| `git branch <name>` | Create a branch (does not switch to it). |
| `git switch <name>` | Move your working tree to another branch (modern name for “checkout branch”). |
| `git switch -c <name>` | Create and switch to a new branch. |
| `git merge <branch>` | Bring another branch’s commits into the branch you are on. |

---

## Remotes (GitHub, GitLab, etc.)

| Command | What it does |
|--------|----------------|
| `git remote -v` | List configured remotes and their URLs. |
| `git pull` | Fetch from the default remote and merge into your current branch. |
| `git push` | Send your local commits to the remote (usually `origin`). |

---

## Useful extras

- **`.gitignore`**: A text file listing paths and patterns Git should not track (build outputs, secrets, editor files).
- **`git restore <file>`**: Discard unstaged changes in that file (careful: you lose uncommitted edits).
- **`git restore --staged <file>`**: Unstage a file without changing its contents on disk.

When in doubt, run `git status` and read what Git suggests next.
