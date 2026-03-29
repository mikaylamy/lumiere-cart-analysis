# Intro to Bash

**Bash** (Bourne Again Shell) is a command-line interpreter: you type commands as text, and the shell runs programs and manages files on your computer. On macOS and most Linux systems, the default login shell is often Bash or a Bash-compatible shell (such as zsh). The ideas below apply to both.

---

## Terminal, shell, and prompt

- **Terminal** (or “console”) is the app window where you type.
- **Shell** is the program that reads what you type and runs commands.
- The **prompt** usually shows where you are and ends with `$` (normal user) or `#` (superuser). You type after the prompt and press **Enter** to run a line.

If you are unsure which shell you use:

```bash
echo $SHELL
```

---

## Where you are: `pwd` and `cd`

| Command | What it does |
|--------|----------------|
| `pwd` | **P**rint **w**orking **d**irectory — shows your current folder path. |
| `cd` | **C**hange **d**irectory. |
| `cd ..` | Go up one folder (parent). |
| `cd ~` or `cd` | Go to your **home** directory (`~` is shorthand for home). |
| `cd -` | Go back to the previous directory. |

Paths can be **absolute** (start from the root, e.g. `/Users/you/project`) or **relative** (from where you are now, e.g. `../data`).

---

## Listing and inspecting files

| Command | What it does |
|--------|----------------|
| `ls` | List files in the current directory. |
| `ls -la` | Long listing, including hidden files (names starting with `.`). |
| `ls path/to/dir` | List that directory without changing into it. |

**Hidden files** start with a dot (e.g. `.gitignore`). They are easy to miss with plain `ls`.

---

## Creating, copying, moving, removing

| Command | What it does |
|--------|----------------|
| `mkdir dirname` | Create a directory. |
| `mkdir -p a/b/c` | Create nested directories as needed. |
| `touch file.txt` | Create an empty file or update its timestamp. |
| `cp source dest` | Copy a file. |
| `cp -r dir dest` | Copy a directory recursively. |
| `mv old new` | Move or rename a file or folder. |
| `rm file` | **Permanently** delete a file (no Trash). |
| `rm -r dir` | Delete a directory and its contents — **dangerous** if the path is wrong. |

**Safety tips:** Prefer `rm -i` for interactive confirmation when learning. Double-check paths before `rm -r`. There is no undo.

---

## Reading file contents

| Command | What it does |
|--------|----------------|
| `cat file` | Print the whole file to the terminal. |
| `less file` | Page through a file (press `q` to quit). |
| `head -n 20 file` | First 20 lines. |
| `tail -n 20 file` | Last 20 lines. |

---

## Wildcards (globs)

- `*` matches any characters in one file name (e.g. `*.txt`).
- `?` matches a single character.
- `[abc]` matches one character from the set.

The shell expands globs **before** running the command, so `ls *.md` becomes `ls` with a list of matching files.

---

## Redirection and pipes

- `command > file` — write **stdout** to `file` (overwrite).
- `command >> file` — **append** stdout to `file`.
- `command < file` — read stdin from `file`.
- `command1 \| command2` — send stdout of `command1` into stdin of `command2`.

Example: count lines in all Markdown files in the current directory:

```bash
cat *.md | wc -l
```

---

## Environment variables

- **Assignment:** `NAME=value` (no spaces around `=`).
- **Export** so child processes see it: `export NAME=value`.
- **Print:** `echo $NAME`.

Common examples: `PATH` (where the shell looks for programs), `HOME` (your home directory).

---

## Quoting

- **Single quotes `'...'`** — almost everything is literal; variables are **not** expanded.
- **Double quotes `"..."`** — variables **are** expanded (`echo "Hi $USER"`).
- **Backticks** `` `command` `` or **`$(command)`** — run a command and substitute its output. Prefer `$(...)` for nesting and readability.

---

## Running scripts

A small Bash script is a text file with a **shebang** on the first line:

```bash
#!/usr/bin/env bash
echo "Hello, $USER"
```

Make it executable, then run it:

```bash
chmod +x myscript.sh
./myscript.sh
```

`./` means “in the current directory” — the shell does not run programs from `.` unless you say so (for security).

---

## Getting help

- `man command` — manual page (press `q` to quit).
- Many programs accept `--help` or `-h`.

---

## Quick reference (copy-friendly)

```bash
pwd                    # current directory
ls -la                 # list all, details
cd path                # change directory
mkdir -p dir           # make directory
cp -r src dst          # copy
mv old new             # move / rename
rm -i file             # delete with prompt
cat file               # print file
less file              # page through file
command > out.txt      # redirect output
a | b                  # pipe output
export VAR=value       # set env for children
./script.sh            # run script in current dir
```

---

## Further reading

- Bash manual: `man bash`
- GNU Bash manual (online): [https://www.gnu.org/software/bash/manual/](https://www.gnu.org/software/bash/manual/)
