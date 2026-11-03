# 2. GitHub

GitHub is where all hackathon code lives. We use the **`hackathon-1`** repository for:

- **Code commits** — every change goes through a branch and pull request
- **CI** — automated checks run on your pull requests
- **Project tickets** — issues track bugs, features, and tasks

## Create an account

1. Go to <https://github.com/signup>
2. Use a real email you can access (you will need to verify it)
3. Pick a professional username — it will appear on your commits
4. Enable two-factor authentication when prompted

## Install Git and the GitHub CLI

You need **`git`** for version control and we recommend **`gh`** (GitHub's CLI) for signing in, opening pull requests, and creating issues. `gh` uses `git` under the hood, so install both.

### macOS

Use Homebrew. It installs current versions without downloading all of Xcode (which is several GB):

```bash
brew install git gh
```

If you do not have Homebrew yet, install it first from <https://brew.sh>:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> Homebrew itself needs the Apple Command Line Tools, but only the small developer toolkit — not the full Xcode app. The installer will offer to fetch them if they are missing.
>
> Already have the Xcode command line tools (or full Xcode)? `git` may already work. Check with `git --version` before installing anything.

### Windows

```powershell
winget install --id Git.Git -e
winget install --id GitHub.cli -e
```

Or download Git from <https://git-scm.com/download/win>. Keep the default options during install.

Open a **new** PowerShell window afterwards so the new commands are on your `PATH`.

### Verify

```bash
git --version
gh --version
```

## Set your identity

Use the same email as your GitHub account:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## Get access to the repo

1. Send your **GitHub username** to an organiser in Discord
2. Accept the email invitation (or the notification on GitHub)
3. Confirm you can open <https://github.com/emdad-i/hackathon-1>

## Sign in and clone the repo

1. Sign in once with the GitHub CLI:

   ```bash
   gh auth login
   ```

   Choose **GitHub.com** → **HTTPS** → **Login with a web browser**, then enter the code it shows you.

2. Clone the repo:

   ```bash
   gh repo clone emdad-i/hackathon-1
   cd hackathon-1
   ```

`git clone https://github.com/emdad-i/hackathon-1.git` works too — `gh` just already has your credentials.

## Daily workflow

```bash
git switch main
git pull
git switch -c feat/my-feature

# make changes
git add -A
git commit -m "feat: add my feature"
git push -u origin HEAD
```

Then open a pull request:

```bash
gh pr create --fill
```

Wait for CI to pass and ask a teammate to review before merging.

## Rules

- Never commit secrets, `.env` files, or API keys.
- Do not push directly to `main`.
- Keep pull requests small and review them quickly.
- Use issues for tasks so we can see who is working on what.

## Ticket example

Create an issue on GitHub, or from the terminal:

```bash
gh issue create --title "Add login form" --label feature
```

Include:

- **Title:** `Add login form`
- **Description:** what "done" looks like
- **Assignee:** yourself
- **Label:** `feature`

Reference it in your PR with `Closes #12` so it closes automatically on merge.
