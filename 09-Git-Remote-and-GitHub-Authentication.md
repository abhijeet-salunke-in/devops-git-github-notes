# 09. Git Remote and GitHub Authentication

> 📘 Module: Git Remote & GitHub Authentication
>
> 🎯 Difficulty: Intermediate
>
> ⏱ Estimated Reading Time: 30 Minutes
>
> 💻 Prerequisites:
>
> - Git Workflow
> - Commits
> - Branching
> - GitHub Repository

---

# 📖 Introduction

Until now, all our work has been inside our local computer.

To collaborate with other developers, backup our code, and trigger CI/CD pipelines, we need a **Remote Repository**.

Git uses **Remote Repositories** to synchronize code between local machines and platforms like GitHub.

This chapter explains everything related to Remote Repositories and authentication methods used in modern DevOps.

---

# 📚 Table of Contents

## Part 1

1. What is a Remote Repository?
2. Why Remote Repositories are Needed?
3. Local vs Remote Repository
4. Git Remote
5. git remote
6. git remote -v
7. git remote add
8. git remote rename
9. git remote remove
10. Origin
11. Upstream
12. Push
13. Push Upstream (-u)

## Part 2

14. Git Fetch
15. Git Pull
16. Fetch vs Pull
17. Push Branch
18. HTTPS Authentication
19. Personal Access Token (PAT)
20. SSH Authentication
21. Generate SSH Key
22. Add SSH Key to GitHub
23. DevOps Scenario
24. Best Practices
25. Interview Questions
26. Summary

---

# 1. What is a Remote Repository?

A Remote Repository is a Git repository stored on another system.

Usually

```
GitHub

GitLab

Bitbucket

Azure DevOps
```

Instead of

your own computer.

---

## Diagram

```
Your Computer

(Local Repository)

        │

git push

        │

        ▼

GitHub

(Remote Repository)
```

---

# Why Remote Repository?

Without Remote Repository

```
Developer A

↓

USB Drive

↓

Developer B
```

Not practical.

With GitHub

```
Developer A

↓

Push

↓

GitHub

↓

Pull

↓

Developer B
```

Much easier.

---

# Benefits

✔ Backup

✔ Team Collaboration

✔ Code Sharing

✔ CI/CD Integration

✔ Disaster Recovery

✔ Version History

---

# 2. Local vs Remote Repository

| Local Repository | Remote Repository |
|------------------|-------------------|
| Stored on Computer | Stored on GitHub |
| Offline | Internet Required |
| Personal Work | Team Collaboration |
| Fast | Shared Repository |

---

# 3. Git Remote

Git remembers

which GitHub repository

belongs to your local project.

This information is called

```
Remote
```

---

# View Remote

Command

```bash
git remote
```

Example Output

```
origin
```

---

# View Detailed Remote

```bash
git remote -v
```

Output

```
origin

https://github.com/abhijeet/devops-git-github-notes.git (fetch)

origin

https://github.com/abhijeet/devops-git-github-notes.git (push)
```

---

# 4. git remote add

Used to connect

Local Repository

with

GitHub Repository.

Syntax

```bash
git remote add origin Repository_URL
```

Example

```bash
git remote add origin https://github.com/abhijeet-salunke-in/devops-git-github-notes.git
```

---

## Command Breakdown

```
git
```

Git program

```
remote
```

Manage remote repositories

```
add
```

Create new remote

```
origin
```

Remote name

```
Repository URL
```

GitHub Repository

---

# Why "origin"?

Origin is just the default name.

You can name it anything.

Example

```bash
git remote add github URL
```

But

every company uses

```
origin
```

as the standard.

---

# 5. git remote rename

Rename remote.

```bash
git remote rename origin github
```

---

# Verify

```bash
git remote
```

Output

```
github
```

---

# 6. git remote remove

Remove remote connection.

```bash
git remote remove origin
```

Local repository remains safe.

Only remote link disappears.

---

# 7. Origin

Origin refers to

your default remote repository.

Example

```
Local Repository

↓

Origin

↓

GitHub Repository
```

Almost every Git project contains

```
origin
```

---

# 8. Upstream

Suppose

You fork Kubernetes.

```
Kubernetes

↓

Fork

↓

Your Repository
```

Your Repository

↓

origin

Original Kubernetes Repository

↓

upstream

---

Why Upstream?

To receive updates

from

Original Project.

---

# 9. git push

Push sends commits

from

Local Repository

to

GitHub.

---

Syntax

```bash
git push
```

---

Example

```bash
git push origin main
```

Meaning

Push

```
main
```

branch

to

```
origin
```

---

## Workflow

```
Commit

↓

Local Repository

↓

git push

↓

GitHub
```

---

# 10. git push -u

One of the most useful Git commands.

Syntax

```bash
git push -u origin main
```

---

Why use -u?

Git remembers

```
origin

main
```

Next time

you simply run

```bash
git push
```

instead of

```bash
git push origin main
```

---

## Example

First Push

```bash
git push -u origin main
```

Second Push

```bash
git push
```

No need to specify

origin

or

main

again.

---

# Real World DevOps Scenario

Imagine you join a company.

You clone the infrastructure repository.

Every day

You

```
Commit

↓

Push

↓

GitHub

↓

Jenkins detects change

↓

CI/CD Pipeline

↓

Deployment
```

Everything begins with

```
git push
```

---

# Best Practices

✅ Keep only one

```
origin
```

for your main repository.

---

✅ Verify remote

before pushing.

```bash
git remote -v
```

---

✅ Use

```bash
git push -u
```

only once.

---

✅ Never push directly

to

```
main
```

in company projects.

---

# 🧠 Memory Tip

Think of

```
origin
```

as

**"My GitHub Repository."**

Think of

```
upstream
```

as

**"Original Repository."**

---

# ✅ End of Part 1

In Part 2 we'll learn

- git fetch
- git pull
- Fetch vs Pull
- Push Branch
- HTTPS Authentication
- Personal Access Token (PAT)
- SSH Authentication
- Generate SSH Keys
- Add SSH Keys to GitHub
- DevOps Authentication Workflow
- Interview Questions
- Summary

---

# Part 2

# 11. git fetch

## What is git fetch?

`git fetch` downloads the latest changes from the remote repository **without modifying your current branch**.

Think of it as:

> "Download the latest information, but don't apply it yet."

---

## Syntax

```bash
git fetch
```

---

## Example

```bash
git fetch origin
```

Git downloads

- New commits
- New branches
- Updated references

Your working files remain unchanged.

---

## Workflow

```
GitHub Repository

↓

git fetch

↓

Local Repository

(No Merge)
```

---

## When to Use?

Suppose your teammate pushed new code.

You want to see the changes first.

Run

```bash
git fetch
```

Review the updates.

Merge later when you're ready.

---

# 12. git pull

## What is git pull?

`git pull` downloads the latest changes **and immediately merges them** into your current branch.

It is equivalent to

```bash
git fetch
git merge
```

---

## Syntax

```bash
git pull
```

---

## Example

```bash
git pull origin main
```

Git performs

```
Fetch

↓

Merge
```

automatically.

---

## Workflow

```
GitHub

↓

git pull

↓

Fetch

↓

Merge

↓

Working Directory Updated
```

---

# 13. Fetch vs Pull

| git fetch | git pull |
|------------|-----------|
| Downloads changes | Downloads + Merges |
| Safe | Can create merge conflicts |
| No code changes | Updates current branch |
| Good before reviewing | Good for daily synchronization |

---

## Which Should You Use?

Use

```bash
git fetch
```

when

- You want to review changes.

Use

```bash
git pull
```

when

- You trust the changes.
- You want to update immediately.

---

# 14. Push a Specific Branch

Sometimes you don't want to push the main branch.

Instead,

push a feature branch.

Example

```bash
git push origin feature-login
```

Now only

```
feature-login
```

is uploaded.

---

# Why?

Suppose

```
feature-payment
```

is incomplete.

You only finished

```
feature-login
```

Push only

```
feature-login
```

Create Pull Request.

Merge later.

---

# 15. GitHub Authentication

GitHub must verify

who is pushing code.

Authentication methods

```
HTTPS

↓

PAT

↓

SSH
```

---

# HTTPS Authentication

Older method.

```
Username

Password
```

Nowadays,

GitHub no longer supports passwords for Git operations.

Instead,

GitHub requires

**Personal Access Tokens (PATs).**

---

# 16. Personal Access Token (PAT)

A Personal Access Token is a secure replacement for your GitHub password.

Instead of entering

```
Password
```

use

```
PAT
```

---

## Why PAT?

Improved security.

Tokens can

- Expire
- Be revoked
- Have limited permissions

---

## PAT Workflow

```
Git Push

↓

Username

↓

PAT

↓

GitHub Authentication

↓

Success
```

---

# When is PAT Used?

Whenever using

```
HTTPS URLs
```

Example

```bash
https://github.com/username/project.git
```

Git asks

```
Username

↓

PAT
```

---

# 17. SSH Authentication

Professional DevOps teams usually prefer SSH.

Instead of typing a PAT every time,

SSH uses a key pair.

```
Private Key

↓

Public Key
```

---

## Benefits

✔ Faster

✔ More Secure

✔ No Password Every Push

✔ Preferred in Automation

---

# SSH Workflow

```
Local Machine

↓

Private Key

↓

GitHub

↓

Public Key

↓

Authentication
```

---

# 18. Generate SSH Key

Generate a new SSH key.

Command

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

If your system doesn't support `ed25519`, you can use RSA:

```bash
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```

Git creates

```
Private Key

↓

~/.ssh/id_ed25519
```

and

```
Public Key

↓

~/.ssh/id_ed25519.pub
```

---

# 19. Add SSH Key to GitHub

Display the public key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output.

Go to

```
GitHub

↓

Settings

↓

SSH and GPG Keys

↓

New SSH Key

↓

Paste

↓

Save
```

Now test

```bash
ssh -T git@github.com
```

Example Output

```
Hi abhijeet-salunke-in!

You've successfully authenticated.
```

---

# HTTPS vs SSH

| HTTPS | SSH |
|---------|------|
| Uses PAT | Uses SSH Keys |
| Easier for beginners | Preferred by professionals |
| Can ask for authentication | Password-less after setup |
| Good for personal use | Good for teams and automation |

---

# 20. Real World DevOps Scenario

Suppose

Your company has

50 developers.

Every push triggers

```
GitHub

↓

Jenkins

↓

Docker Build

↓

Kubernetes Deployment
```

Typing PAT every time

is inefficient.

Instead,

every developer configures SSH.

Now

```bash
git push
```

works instantly.

---

# 21. Best Practices

✅ Use SSH for company projects.

---

✅ Keep Personal Access Tokens secret.

---

✅ Never commit SSH private keys.

---

✅ Verify remotes using

```bash
git remote -v
```

---

✅ Pull latest changes before pushing.

---

# 22. Common Mistakes

❌ Using passwords instead of PAT.

---

❌ Uploading private SSH keys.

---

❌ Forgetting

```bash
git fetch
```

before merging.

---

❌ Pushing directly to

```
main
```

---

# 23. Interview Questions

### Q1. What is a Remote Repository?

A Git repository hosted on another system like GitHub.

---

### Q2. Difference between Fetch and Pull?

`git fetch`

Downloads changes only.

`git pull`

Downloads and merges changes.

---

### Q3. What is Origin?

The default name of the remote repository.

---

### Q4. What is Upstream?

The original repository from which a project was forked.

---

### Q5. Why is PAT used?

GitHub replaced password authentication with Personal Access Tokens for better security.

---

### Q6. Why is SSH preferred?

It provides secure authentication without entering credentials for every push.

---

### Q7. How do you verify configured remotes?

```bash
git remote -v
```

---

# 24. Summary

In this chapter you learned

- Remote Repository
- Local vs Remote
- git remote
- git remote add
- git remote rename
- git remote remove
- origin
- upstream
- git push
- git push -u
- git fetch
- git pull
- Fetch vs Pull
- HTTPS Authentication
- Personal Access Token
- SSH Authentication
- Generate SSH Keys
- Add SSH Keys to GitHub

---

# 📝 Quick Revision

View Remote

```bash
git remote -v
```

---

Add Remote

```bash
git remote add origin URL
```

---

Rename Remote

```bash
git remote rename origin github
```

---

Remove Remote

```bash
git remote remove origin
```

---

Push

```bash
git push
```

---

First Push

```bash
git push -u origin main
```

---

Fetch

```bash
git fetch
```

---

Pull

```bash
git pull
```

---

Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

---

Test SSH

```bash
ssh -T git@github.com
```

---

# 📌 Command Reference

| Command | Purpose |
|----------|---------|
| `git remote` | Show remote names |
| `git remote -v` | Show remote URLs |
| `git remote add origin URL` | Add a new remote |
| `git remote rename old new` | Rename a remote |
| `git remote remove origin` | Remove a remote |
| `git push` | Upload commits |
| `git push -u origin main` | First push and set upstream |
| `git fetch` | Download changes without merging |
| `git pull` | Download and merge changes |
| `ssh-keygen -t ed25519 -C "email"` | Generate SSH key |
| `ssh -T git@github.com` | Test SSH authentication |

---

# 🎯 Key Takeaways

- Remote repositories enable collaboration and CI/CD.
- `origin` is the default remote; `upstream` usually refers to the original fork source.
- Use `git fetch` to review remote changes before merging.
- Use `git pull` to synchronize your branch quickly.
- Configure SSH for a smoother and more secure workflow.
- Keep PATs and private SSH keys secure.

---

## 📖 Navigation

⬅ Previous:
**08-Git-Rebase-Stash-and-Cherry-Pick.md**

➡ Next:
**10-GitHub-Collaboration-and-Features.md**
