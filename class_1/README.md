# Git and GitHub Commands

A simple command guide for using Git on your computer and GitHub online. All names such as `USERNAME`, `REPOSITORY`, and `BRANCH_NAME` are placeholders; replace them with your own details.

## Git and GitHub

- **Git** tracks changes to files on your computer.
- **GitHub** hosts Git repositories online and supports collaboration.
- A **repository** (or repo) contains project files and their change history.
- A **commit** is a saved checkpoint of your changes.
- A **branch** lets you work on changes separately from the main branch.

## 1. Configure Git

Set your name and email once on each computer:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check the settings:

```bash
git config --global --list
```

## 2. Get a repository

To download a repository from GitHub, replace the placeholders with its owner and name:

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
```

To start a new local repository instead:

```bash
mkdir REPOSITORY
cd REPOSITORY
git init
```

You can also create an empty repository on GitHub using the website, then follow the instructions GitHub gives to connect it to your local folder.

## 3. Check changes

```bash
git status
git diff
git diff --staged
git log --oneline -5
git branch
git remote -v
```

These show the current state, unstaged edits, staged edits, recent commits, local branches, and connected remote repositories.

## 4. Save and upload changes

After editing files:

```bash
git status
git add FILENAME
git commit -m "Describe your change"
git push
```

Replace `FILENAME` with a changed file. To stage all changed files, use `git add .` instead.

For the first push of a new branch, set its upstream at the same time:

```bash
git push -u origin BRANCH_NAME
```

## 5. Get the latest changes

To download and merge updates from the remote branch:

```bash
git pull origin main
```

Replace `main` if the repository uses a different branch name. `git fetch` downloads updates without merging them; `git pull` downloads and merges.

## 6. Create a branch and open a pull request

Create and switch to a new branch:

```bash
git switch -c BRANCH_NAME
```

Make your changes, then stage, commit, and push the branch:

```bash
git add FILENAME
git commit -m "Describe your change"
git push -u origin BRANCH_NAME
```

On GitHub, open the repository and choose **Compare & pull request** (or **New pull request**). Review the source and destination branches, describe your changes, and submit the pull request.

## 7. Fork workflow (optional)

A fork is your own GitHub copy of another person's repository. On GitHub, open the repository and select **Fork**. Then clone your fork and add the original repository as `upstream`:

```bash
git clone https://github.com/YOUR_USERNAME/REPOSITORY.git
cd REPOSITORY
git remote add upstream https://github.com/ORIGINAL_OWNER/REPOSITORY.git
git remote -v
```

To bring the original repository's latest `main` branch into your fork:

```bash
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

Here, `origin` is your fork and `upstream` is the original repository.

## 8. Undo or set aside changes

Unstage a file but keep its edits:

```bash
git restore --staged FILENAME
```

Discard uncommitted edits to a file:

```bash
git restore FILENAME
```

This permanently discards those uncommitted edits. To temporarily set changes aside and restore them later:

```bash
git stash
git stash pop
```

## 9. Optional: GitHub CLI

The GitHub CLI (`gh`) lets you use some GitHub features from a terminal. After installing it, sign in:

```bash
gh auth login
```

View the current repository on GitHub:

```bash
gh repo view --web
```

Create a pull request from your current branch:

```bash
gh pr create --base main --fill
```

## Helpful reminders

- Run `git status` before committing, switching branches, or merging.
- Commit your changes before pulling or merging updates.
- A push uploads commits to GitHub. A pull request asks others to review and merge your changes.
- Never commit passwords, access tokens, or other secrets.

