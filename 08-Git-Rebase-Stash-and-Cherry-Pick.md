# 08. Git Rebase, Stash and Cherry-Pick

> 📘 Module: Advanced Git Operations
>
> 🎯 Difficulty: Intermediate to Advanced
>
> ⏱ Estimated Reading Time: 35–40 Minutes
>
> 💻 Prerequisites:
>
> - Git Branches
> - Git Merge
> - Git Workflow

---

# 📖 Introduction

As projects grow larger, developers often need to manage commits, temporarily save unfinished work, or move specific commits between branches.

Git provides three powerful features for these situations:

- Git Rebase
- Git Stash
- Git Cherry-Pick

These commands are commonly used in professional software development and DevOps environments.

Understanding them helps maintain a clean commit history and improves collaboration.

---

# 📚 Table of Contents

## Part 1

1. What is Git Rebase?
2. Why Rebase is Needed?
3. Rebase Workflow
4. git rebase
5. Interactive Rebase
6. Squash Commits
7. Rebase vs Merge

## Part 2

8. Git Stash
9. Stash Commands
10. Cherry Pick
11. Real World DevOps Scenarios
12. Best Practices
13. Interview Questions
14. Summary

---

# 1. What is Git Rebase?

Rebase is used to move or replay commits from one branch onto another branch.

Instead of creating a merge commit,

Git replays your commits one by one.

The result is a cleaner project history.

---

## Normal Merge

```
main

A

↓

B

↓

feature

↓

C

↓

Merge Commit
```

History becomes

```
A

↓

B

├── C

↓

Merge
```

---

## Rebase

```
main

A

↓

B

↓

feature

↓

C
```

After Rebase

```
A

↓

B

↓

C
```

No merge commit.

History becomes linear.

---

# Why Use Rebase?

Suppose

Five developers work on

```
main
```

Your branch becomes outdated.

Instead of merging,

you replay your work on top of the latest commits.

Advantages

✔ Clean history

✔ Easier debugging

✔ Better project timeline

---

# 2. Rebase Workflow

```
main

↓

Commit A

↓

Commit B

↓

feature

↓

Commit C

↓

Commit D
```

Run

```bash
git switch feature

git rebase main
```

Git moves

```
Commit C

Commit D
```

to the latest

```
main
```

---

# 3. git rebase

## Syntax

```bash
git rebase <branch-name>
```

Example

```bash
git switch feature-login

git rebase main
```

Git updates

```
feature-login
```

using the latest changes from

```
main
```

---

# Before Rebase

```
main

↓

A

↓

B

↓

feature

↓

C

↓

D
```

---

# After Rebase

```
A

↓

B

↓

C

↓

D
```

Linear history.

---

# 4. Interactive Rebase

One of Git's most powerful features.

Command

```bash
git rebase -i HEAD~3
```

Git opens an editor.

Example

```
pick

pick

pick
```

You can

- Reorder commits
- Edit commits
- Delete commits
- Squash commits
- Rename commit messages

---

# Why Interactive Rebase?

Suppose

History

```
Fix Login

Update README

Fix Login Again

Fix Login Again

Fix Login Again
```

Looks messy.

Interactive Rebase lets you clean it.

---

# 5. Squash Commits

Squashing combines multiple commits into one.

Example

```
Commit 1

Added Login

↓

Commit 2

Fixed Login

↓

Commit 3

Updated Login CSS
```

After Squash

```
One Commit

Complete Login Feature
```

History becomes much cleaner.

---

# Command

```bash
git rebase -i HEAD~3
```

Change

```
pick
```

to

```
squash
```

Git combines commits.

---

# Why Squash?

Professional teams don't like

```
Fix

Fix Again

Small Change

Another Fix
```

Instead

```
Implement Login Module
```

One meaningful commit.

---

# 6. Rebase vs Merge

| Rebase | Merge |
|----------|----------|
| Linear History | Branch History Preserved |
| No Merge Commit | Merge Commit Created |
| Cleaner | Complete Timeline |
| Rewrites History | Doesn't Rewrite History |

---

# When Should You Use Rebase?

Use Rebase

✔ Before creating Pull Requests

✔ To clean feature branch history

✔ On your local feature branches

---

# When Should You Avoid Rebase?

Never rebase

- Shared branches
- Public branches
- Main branch

Because it rewrites history.

---

# Real World DevOps Scenario

Suppose

You work on

```
feature-monitoring
```

Meanwhile,

other developers push

15 commits

to

```
main
```

Instead of creating a huge merge commit,

run

```bash
git rebase main
```

Your feature now appears as if it was built on the latest project.

History remains clean.

---

# Best Practices

✅ Rebase only local branches.

---

✅ Pull latest changes before rebasing.

---

✅ Never rebase public branches.

---

✅ Squash unnecessary commits before Pull Request.

---

# 🧠 Memory Tip

Think of Rebase as

"Moving your work to the latest version of the project"

instead of

"Connecting two branches together."

---

# ✅ End of Part 1

Next we'll learn

- Git Stash
- git stash list
- git stash pop
- git stash apply
- git stash drop
- Git Cherry Pick
- Real DevOps Scenarios
- Interview Questions
- Summary

---

# Part 2

# 7. Git Stash

## What is Git Stash?

Git Stash is used to **temporarily save your uncommitted changes** without creating a commit.

Think of it as putting your current work into a locker.

You can come back later and continue exactly where you left off.

---

## Why Use Git Stash?

Suppose you are working on

```
feature-login
```

You have modified

```
login.html

login.css
```

Suddenly your manager says

> "Fix the production issue immediately."

Your work is incomplete.

You don't want to commit unfinished code.

Instead of committing,

run

```bash
git stash
```

Your working directory becomes clean.

Now switch branches and fix the production issue.

Later,

restore your work.

---

# Git Stash Workflow

```
Working Directory

↓

Modified Files

↓

git stash

↓

Temporary Storage

↓

Switch Branch

↓

Finish Urgent Work

↓

git stash pop

↓

Continue Previous Work
```

---

# 8. git stash

## Syntax

```bash
git stash
```

Example

```bash
git stash
```

Output

```
Saved working directory and index state
```

Git stores

- Modified files
- Staged files

and cleans the working directory.

---

# Check Stash List

Git can store multiple stashes.

View them

```bash
git stash list
```

Example

```
stash@{0}

stash@{1}

stash@{2}
```

Each stash has its own ID.

---

# Restore Latest Stash

Command

```bash
git stash pop
```

Git

✔ Restores files

✔ Removes stash

---

Workflow

```
Temporary Storage

↓

git stash pop

↓

Working Directory
```

---

# Apply Stash

Sometimes

you want to restore

without deleting the stash.

Use

```bash
git stash apply
```

Difference

```
git stash pop

↓

Restore

↓

Delete Stash
```

```
git stash apply

↓

Restore

↓

Keep Stash
```

---

# Delete Stash

Delete latest stash

```bash
git stash drop
```

Delete all

```bash
git stash clear
```

Use carefully.

---

# Real Example

Morning

Working on

```
Payment Module
```

Afternoon

Production issue reported.

Run

```bash
git stash
```

Switch

```bash
git switch hotfix-payment
```

Fix issue.

Commit.

Merge.

Return

```bash
git switch feature-payment
```

Restore

```bash
git stash pop
```

Continue development.

---

# 9. Git Cherry Pick

## What is Cherry Pick?

Cherry Pick copies **one specific commit**

from one branch

to another.

Instead of merging the entire branch,

only the selected commit is copied.

---

# Example

```
main

↓

Commit A

↓

Commit B

──────────────

feature

↓

Commit C

↓

Commit D
```

Need only

```
Commit C
```

Run

```bash
git cherry-pick CommitID
```

Now

```
main

↓

Commit A

↓

Commit B

↓

Commit C
```

Commit D remains untouched.

---

# Syntax

```bash
git cherry-pick <commit-id>
```

Example

```bash
git cherry-pick 9f4a8d2
```

---

# Why Cherry Pick?

Suppose

Feature Branch contains

```
Login

Payment

Profile
```

Production needs only

```
Login
```

Instead of merging everything,

Cherry Pick

only the Login commit.

---

# Cherry Pick Workflow

```
Feature Branch

↓

Commit A

↓

Commit B

↓

Commit C

↓

Cherry Pick

↓

Main Branch

↓

Commit B
```

Only selected commit moves.

---

# When to Use Cherry Pick?

Use Cherry Pick

✔ Hotfixes

✔ Production patches

✔ Copying one bug fix

✔ Moving one feature

---

Avoid

Cherry Picking

large groups of commits.

Merge is better.

---

# 10. Real World DevOps Scenario

Suppose

Production has a bug.

Feature branch contains

20 commits.

Only one commit

fixes the bug.

Instead of merging

all 20 commits,

run

```bash
git cherry-pick CommitID
```

Bug fixed.

Production remains stable.

---

Another Scenario

You are deploying Kubernetes.

Feature branch contains

```
Deployment

Service

Ingress

README
```

Production only needs

```
Ingress Fix
```

Cherry Pick

that single commit.

---

# 11. Best Practices

## Git Rebase

✅ Rebase local branches only.

✅ Squash unnecessary commits.

✅ Keep history clean.

---

## Git Stash

✅ Stash unfinished work.

✅ Name your stash (optional)

```bash
git stash push -m "Working on Login UI"
```

---

## Cherry Pick

✅ Cherry Pick only small changes.

✅ Verify commit before Cherry Picking.

---

# 12. Common Mistakes

❌ Rebasing public branches.

---

❌ Forgetting stashed work.

---

❌ Cherry Picking many commits instead of merging.

---

❌ Using stash as permanent storage.

---

# 13. Interview Questions

### Q1. What is Rebase?

Moves commits onto another branch to create a linear history.

---

### Q2. Difference between Rebase and Merge?

Merge preserves branch history.

Rebase rewrites history.

---

### Q3. What is Git Stash?

Temporary storage for uncommitted work.

---

### Q4. Difference between

```bash
git stash pop
```

and

```bash
git stash apply
```

Pop

Restore + Delete.

Apply

Restore + Keep.

---

### Q5. What is Cherry Pick?

Copies one specific commit from one branch to another.

---

### Q6. When should Cherry Pick be used?

When only one commit is required instead of an entire branch.

---

# 14. Summary

In this chapter you learned

- Git Rebase
- Interactive Rebase
- Squash Commits
- Rebase vs Merge
- Git Stash
- Stash List
- Stash Pop
- Stash Apply
- Stash Drop
- Git Cherry Pick
- Real DevOps Scenarios

---

# 📝 Quick Revision

Rebase

```bash
git rebase main
```

---

Interactive Rebase

```bash
git rebase -i HEAD~3
```

---

Stash Changes

```bash
git stash
```

---

View Stashes

```bash
git stash list
```

---

Restore Stash

```bash
git stash pop
```

---

Restore Without Removing

```bash
git stash apply
```

---

Delete Latest Stash

```bash
git stash drop
```

---

Cherry Pick

```bash
git cherry-pick CommitID
```

---

# 🎯 Key Takeaways

- Rebase creates a clean, linear commit history by replaying commits.
- Interactive Rebase helps clean up commit history before sharing changes.
- Stash temporarily saves unfinished work without creating a commit.
- Cherry Pick copies only the commits you need from another branch.
- Use Rebase carefully—avoid rewriting the history of shared branches.
- Use Stash for short-term work, not as a long-term backup.

---

## 📖 Navigation

⬅ Previous:
**07-Branching-and-Merging.md**

➡ Next:
**09-Git-Remote-and-GitHub-Authentication.md**
