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

---

# 🏷️ Git Tags

## What are Git Tags?

A Git Tag is a reference (or label) that points to a specific commit.

Unlike branches, tags do not move when new commits are created.

Tags are mainly used to mark important milestones such as software releases.

Example:

```
v1.0.0
v1.1.0
v2.0.0
```

These tags indicate different released versions of an application.

---

## Why are Git Tags Used?

Git Tags help developers:

- Mark stable releases
- Identify production versions
- Roll back to older releases
- Simplify deployment
- Maintain version history

---

## DevOps Use Case

Suppose your company has successfully tested version **1.0.0** of an application.

You want Jenkins or another CI/CD tool to deploy only this stable version.

Instead of deploying the latest commit, you create a tag.

```
main

↓

Commit A

↓

Commit B

↓

Commit C

↓

🏷️ v1.0.0
```

Now Jenkins can deploy **v1.0.0** instead of the latest commit.

---

# Types of Tags

Git provides two types of tags.

## 1. Lightweight Tag

A lightweight tag is simply a pointer to a commit.

It does not store additional information.

Command

```bash
git tag v1.0.0
```

---

## 2. Annotated Tag

Annotated tags contain additional metadata.

They store

- Tag Name
- Tag Message
- Author
- Email
- Date

Command

```bash
git tag -a v1.0.0 -m "First Stable Release"
```

This is the recommended type for production releases.

---

# View All Tags

Command

```bash
git tag
```

Example Output

```
v1.0.0

v1.1.0

v2.0.0
```

---

# View Tag Information

Command

```bash
git show v1.0.0
```

This displays

- Commit
- Author
- Date
- Tag Message
- Code Changes

---

# Push a Single Tag

Creating a tag only creates it locally.

To upload it to GitHub

```bash
git push origin v1.0.0
```

---

# Push All Tags

Command

```bash
git push origin --tags
```

This uploads every local tag to GitHub.

---

# Delete Local Tag

Command

```bash
git tag -d v1.0.0
```

---

# Delete Remote Tag

Command

```bash
git push origin --delete v1.0.0
```

---

# Checkout a Tag

Command

```bash
git checkout v1.0.0
```

Git moves to that tagged commit.

Note:

This creates a **Detached HEAD** state.

To continue development, create a new branch.

```bash
git switch -c bugfix-v1
```

---

# Semantic Versioning

Most software projects follow Semantic Versioning.

Format

```
MAJOR.MINOR.PATCH
```

Example

```
1.4.2
```

Meaning

- Major → Breaking Changes
- Minor → New Features
- Patch → Bug Fixes

Example

```
1.0.0

↓

1.1.0

↓

1.1.1

↓

2.0.0
```

---

# Real DevOps Scenario

Suppose your company releases software every month.

```
January

↓

v1.0.0

February

↓

v1.1.0

March

↓

v1.2.0
```

When customers report a bug in **v1.1.0**, developers can instantly check out that exact version using its tag.

---

# Best Practices

✔ Use Annotated Tags for releases.

✔ Follow Semantic Versioning.

✔ Never edit release tags after publishing.

✔ Push tags to the remote repository.

✔ Use meaningful tag names.

Examples

```
v1.0.0

v2.1.3

release-2025-01

production-v5
```

---

# Common Interview Questions

### What is a Git Tag?

A Git Tag is a permanent label pointing to a specific commit.

---

### Why use Tags instead of Branches?

Branches continue moving with new commits.

Tags always point to the same commit.

---

### Which type of Tag is recommended?

Annotated Tags.

---

### How do you push a Tag?

```bash
git push origin v1.0.0
```

---

### How do you push all Tags?

```bash
git push origin --tags
```

---

### What is Semantic Versioning?

Version numbering format

```
MAJOR.MINOR.PATCH
```

used to indicate the type of software changes.

---

# Quick Revision

| Command | Purpose |
|----------|---------|
| `git tag` | List all tags |
| `git tag v1.0.0` | Create lightweight tag |
| `git tag -a v1.0.0 -m "msg"` | Create annotated tag |
| `git show v1.0.0` | Show tag details |
| `git push origin v1.0.0` | Push one tag |
| `git push origin --tags` | Push all tags |
| `git tag -d v1.0.0` | Delete local tag |
| `git push origin --delete v1.0.0` | Delete remote tag |
| `git checkout v1.0.0` | Checkout tag |


---

# 🔍 Git Bisect

## What is Git Bisect?

Git Bisect is a debugging tool that helps you find the exact commit that introduced a bug.

Instead of checking every commit manually, Git Bisect uses a **binary search algorithm** to quickly locate the problematic commit.

---

## Why is Git Bisect Used?

Imagine your application was working yesterday, but today it is failing.

There are hundreds of commits between the working version and the broken version.

Checking each commit manually would take a long time.

Git Bisect automatically narrows down the search and identifies the bad commit in just a few steps.

---

## DevOps Use Case

Suppose your production application starts failing after a deployment.

```
Commit A  ✅ Working

↓

Commit B  ✅ Working

↓

Commit C  ❓

↓

Commit D  ❓

↓

Commit E  ❌ Bug Introduced

↓

Commit F  ❌ Failing
```

Instead of checking all commits one by one, Git Bisect helps you quickly find **Commit E**, where the bug was introduced.

---

# How Git Bisect Works

Git Bisect follows the **Binary Search** algorithm.

Example

```
1

2

3

4

5

6

7

8
```

Instead of checking all 8 commits,

Git checks

```
4

↓

6

↓

5
```

Only a few checks are needed.

This makes Git Bisect extremely fast, even in repositories with thousands of commits.

---

# Basic Workflow

Step 1

Start Bisect

```bash
git bisect start
```

---

Step 2

Mark the current broken commit

```bash
git bisect bad
```

---

Step 3

Mark the last known good commit

```bash
git bisect good <commit-id>
```

Example

```bash
git bisect good 3fd45ab
```

Git now checks out a commit in the middle of the history.

---

Step 4

Test your application.

If the bug exists

```bash
git bisect bad
```

If the application works

```bash
git bisect good
```

Git continues selecting the next middle commit.

Repeat until Git identifies the first bad commit.

---

# Example

Suppose your commit history is

```
A

↓

B

↓

C

↓

D

↓

E

↓

F
```

You know

```
B

↓

Working
```

and

```
F

↓

Broken
```

Commands

```bash
git bisect start

git bisect bad

git bisect good B
```

Git checks

```
D
```

If D works

```bash
git bisect good
```

Git checks

```
E
```

If E fails

```bash
git bisect bad
```

Git reports

```
E is the first bad commit.
```

---

# End Bisect Session

After finding the bad commit, return to your original branch.

```bash
git bisect reset
```

This exits Bisect mode.

---

# Common Commands

Start

```bash
git bisect start
```

Mark bad commit

```bash
git bisect bad
```

Mark good commit

```bash
git bisect good <commit-id>
```

Exit Bisect

```bash
git bisect reset
```

---

# Real DevOps Scenario

A CI/CD pipeline deploys version **2.5.0**.

Users report that the application crashes after login.

There are **150 commits** between the last stable release and the current deployment.

Instead of checking all 150 commits manually, the DevOps team uses Git Bisect to locate the exact commit that introduced the issue.

Once identified, developers fix or revert that commit, and the pipeline is triggered again.

---

# Advantages

✔ Finds bugs quickly

✔ Saves debugging time

✔ Uses Binary Search

✔ Works well with large repositories

✔ Ideal for production issue investigation

---

# Limitations

❌ Requires a known good commit

❌ Requires a reproducible bug

❌ Not useful if the issue occurs randomly

---

# Best Practices

✔ Keep commits small and focused.

✔ Write meaningful commit messages.

✔ Test frequently.

✔ Use Git Bisect for difficult-to-find bugs.

✔ Reset Bisect after finishing.

---

# Interview Questions

### What is Git Bisect?

Git Bisect is a debugging tool that uses binary search to identify the commit that introduced a bug.

---

### Which algorithm does Git Bisect use?

Binary Search.

---

### How do you start Git Bisect?

```bash
git bisect start
```

---

### How do you mark a bad commit?

```bash
git bisect bad
```

---

### How do you mark a good commit?

```bash
git bisect good <commit-id>
```

---

### How do you exit Git Bisect?

```bash
git bisect reset
```

---

### When should Git Bisect be used?

When you know the application was working before but is now failing, and you need to identify the exact commit that introduced the bug.

---

# Quick Revision

| Command | Purpose |
|----------|---------|
| `git bisect start` | Start bisect session |
| `git bisect bad` | Mark current commit as bad |
| `git bisect good <commit-id>` | Mark known good commit |
| `git bisect reset` | Exit bisect mode |

---

## Summary

Git Bisect is an advanced Git debugging tool that uses the Binary Search algorithm to quickly locate the commit that introduced a bug.

It is especially valuable in large projects where manually checking every commit would be time-consuming.


---

# 14. Summary

In this chapter you learned

* Git Rebase
* Interactive Rebase
* Squash Commits
* Rebase vs Merge
* Git Stash
* Stash List
* Stash Pop
* Stash Apply
* Stash Drop
* Git Cherry Pick
* Git Tags
* Lightweight Tags
* Annotated Tags
* Semantic Versioning
* Git Bisect
* Real DevOps Scenarios

---

# 📝 Quick Revision

### Rebase

```bash
git rebase main
```

---

### Interactive Rebase

```bash
git rebase -i HEAD~3
```

---

### Stash Changes

```bash
git stash
```

---

### View Stashes

```bash
git stash list
```

---

### Restore Stash

```bash
git stash pop
```

---

### Restore Without Removing

```bash
git stash apply
```

---

### Delete Latest Stash

```bash
git stash drop
```

---

### Cherry Pick

```bash
git cherry-pick CommitID
```

---

### Create Lightweight Tag

```bash
git tag v1.0.0
```

---

### Create Annotated Tag

```bash
git tag -a v1.0.0 -m "First Stable Release"
```

---

### Push Tag

```bash
git push origin v1.0.0
```

---

### Push All Tags

```bash
git push origin --tags
```

---

### Start Git Bisect

```bash
git bisect start
```

---

### Mark Good Commit

```bash
git bisect good <commit-id>
```

---

### Mark Bad Commit

```bash
git bisect bad
```

---

### Exit Git Bisect

```bash
git bisect reset
```

---

# 🎯 Key Takeaways

* Rebase creates a clean, linear commit history by replaying commits.
* Interactive Rebase helps clean up commit history before sharing changes.
* Stash temporarily saves unfinished work without creating a commit.
* Cherry Pick copies specific commits from one branch to another.
* Git Tags are used to mark important milestones such as software releases.
* Annotated Tags are recommended for production releases because they store additional metadata.
* Semantic Versioning (MAJOR.MINOR.PATCH) helps teams manage software releases consistently.
* Git Bisect uses a binary search algorithm to quickly identify the commit that introduced a bug.
* Always use Rebase carefully and avoid rewriting the history of shared branches.
* Use Stash for short-term work, not as a long-term backup.
* Tags and Bisect are commonly used by DevOps engineers during release management and production debugging.

---

## 📖 Navigation

⬅ **Previous:**
**07-Branching-and-Merging.md**

➡ **Next:**
**09-Git-Remote-and-GitHub-Authentication.md**
