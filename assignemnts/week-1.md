# Week 1 Homework — Bash & Git in This Project

This homework is designed to help you practice the **real commands you would use when starting work in an existing repository**. You will use Bash to move around the project and inspect files, then use Git to understand the state and history of the repo.

## Learning goals

By the end of this homework, you should be able to:

- identify your current directory in the terminal
- list files in a project and recognize important hidden files
- read project files from the command line
- inspect the current state of a Git repository
- explain what basic Git output means in plain English

---

## Before you begin

Open a terminal and change into this repository's root folder. You should be in the folder that contains `README.md`, `.gitignore`, `intro-to-bash.md`, and `intro-to-git.md`.

```bash
cd /path/to/lumiere-cart-analysis
```

Use [`intro-to-bash.md`](../intro-to-bash.md) and [`intro-to-git.md`](../intro-to-git.md) as references while you work.

If a command opens a full-screen viewer such as `less`, press `q` to quit and return to the prompt.

---

## How to use this homework

Work through the commands **in order**. Do not skip ahead. The goal is to learn by seeing how each command helps you understand the project.

For each step:

- run the command exactly as shown
- read the explanation before or after running it
- look carefully at the output before moving on

You do **not** need to write anything down. The learning happens by following the sequence and comparing what each command reveals.

---

## Part A — Bash: navigate and inspect the project

Run each command from the repo root. These commands build on each other, so go in order.

### 1. Confirm where you are

```bash
pwd
```

Why this matters: `pwd` prints your current working directory, which is the folder your shell is currently using. Before you run project commands, you should always know where you are.

As you run it, notice that the output is a full path. This is the terminal's way of answering the question: "What folder am I in right now?"

### 2. List the files in the project

```bash
ls -la
```

Why this matters: `ls` lists files, `-l` shows details, and `-a` includes hidden files such as `.git` and `.gitignore`.

This is one of the first things developers do in an unfamiliar repo. It lets you quickly see what kind of project you are in and whether Git metadata is present.

### 3. Read the project title

```bash
cat README.md
```

Why this matters: `cat` prints a file directly to the terminal. This is useful for very short files.

In a real project, `README.md` is often the fastest place to learn what the repository is for. Here, `cat` works well because the file is short.

### 4. Open a longer file in a pager

```bash
less intro-to-bash.md
```

Why this matters: `less` is better than `cat` for longer files because it lets you scroll without dumping the whole file at once.

This is a common workflow: use `cat` for short files, but use `less` when a file is long enough that you want to inspect it gradually.

### 5. Preview only the beginning of a file

```bash
head -n 15 .gitignore
```

Why this matters: `head` shows only the first part of a file, which is useful when you want a quick preview.

This is helpful when you do not need the whole file. In this case, it gives you a fast look at how `.gitignore` is structured and what kinds of files the repo chooses not to track.

### 6. Count lines in multiple files

```bash
wc -l README.md intro-to-bash.md intro-to-git.md
```

Why this matters: `wc -l` counts lines. You can pass multiple files to compare them.

This gives you a quick sense of file size. Developers often use simple counts like this to decide whether a file is tiny, medium, or long before opening it.

---

## Part B — Git: inspect the repository

These commands are meant to help you understand the repo without changing its history. In real work, this is the first Git pass you would make before editing anything.

### 7. Check the current repo state

```bash
git status
```

Why this matters: `git status` is the most important everyday Git command. It tells you which branch you are on, whether files changed, and what Git thinks you should do next.

If you only remember one Git command from this week, remember this one. Developers run it constantly because it answers: "Where am I, and what is Git seeing right now?"

### 8. Look at recent commit history

```bash
git log --oneline -5
```

Why this matters: `git log` shows commit history. `--oneline` makes it compact, and `-5` limits the output to the five most recent commits.

This gives you a quick overview of what happened recently in the project. In practice, this is often the first history view people use when joining a repo.

### 9. Inspect the remote connection

```bash
git remote -v
```

Why this matters: a remote is a linked copy of the repository stored somewhere else, such as GitHub. `-v` shows the URLs Git uses.

This command gives context for where the project came from and where changes would be shared. Even if you are not pushing anything, it is useful to know the remote connection exists.

### 10. List branches

```bash
git branch -a
```

Why this matters: branches are parallel lines of work. `-a` shows local branches and remote-tracking branches.

This helps you see the difference between what exists on your machine and what Git knows about on the remote server.

---

## Optional challenge — Create a practice branch

Only do this if you are comfortable and your instructor allows local experimentation.

```bash
git switch -c homework/week1-practice
git status
git switch main
```

Why this matters: `git switch -c` creates a new branch and moves you onto it. Switching back to `main` returns you to the main line of work.

This is useful because it shows that branches are part of your workflow, not just abstract Git vocabulary. You can move between lines of work without changing tracked files just by changing branch context.

Do not push this branch unless your instructor specifically tells you to.

---

## Safety rules for this assignment

For this homework, do **not** use:

- `git reset --hard`
- `git clean`
- `git push --force`

Stay focused on **inspection, reading output, and understanding what the repo contains**.
