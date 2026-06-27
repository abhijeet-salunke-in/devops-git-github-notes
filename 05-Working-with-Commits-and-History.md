# 05. Working with Commits and History

> 📘 Module: Working with Commits & History
>
> 🎯 Difficulty: Beginner to Intermediate
>
> ⏱ Estimated Reading Time: 20–25 Minutes
>
> 💻 Prerequisites:
>
> - Git Installation & Configuration
> - Git Workflow
> - Working Directory
> - Staging Area

---

# 📖 Introduction

A commit is the **heart of Git**.

Every time you save your work permanently in Git, you create a **commit**.

Think of a commit as a **snapshot** of your project at a specific point in time.

If something goes wrong later, Git allows you to return to any previous commit.

Without commits, Git cannot maintain project history.

---

# 📚 Table of Contents

1. What is a Commit?
2. Why Commits are Needed?
3. Anatomy of a Commit
4. Commit Lifecycle
5. Creating Commits
6. git commit
7. git commit -m
8. Commit Specific Files
9. Atomic Commits
10. Commit Message Best Practices
11. Real World DevOps Scenario
12. Best Practices

---

# 1. What is a Commit?

A **commit** is a permanent snapshot of the project stored in the Git repository.

Every commit records:

- Project Snapshot
- Author
- Email
- Date & Time
- Commit Message
- Parent Commit
- Unique Commit ID (Hash)

Think of a commit like saving a game.

```
Save Point 1

↓

Save Point 2

↓

Save Point 3
```

If something breaks,

you can return to an earlier save point.

Git works the same way.

---

# Example

Suppose your project contains

```
Student-Inquiry-System/

index.html

style.css

about.html
```

You stage all files

```bash
git add .
```

Now you create a commit

```bash
git commit -m "Initial project structure"
```

Git stores a complete snapshot.

---

# 2. Why Commits are Needed?

Commits help developers

- Save project history
- Track changes
- Restore old versions
- Collaborate with teams
- Identify who made changes
- Roll back mistakes

Without commits,

Git cannot maintain version history.

---

## Imagine This Situation

You update

```
payment.php
```

The application crashes.

Yesterday,

everything worked perfectly.

Because you committed yesterday,

Git allows you to restore that version.

Without commits,

the working version is lost.

---

# 3. Anatomy of a Commit

Every commit contains important information.

Example

```
Commit ID

↓

9f4a8d23

↓

Author

Abhijeet Salunke

↓

Email

abhijeetsalunke@gmail.com

↓

Date

25 June 2026

↓

Message

Added Login Page
```

Every commit has its own unique identity.

---

# 4. Commit Lifecycle

Before a commit is created,

changes follow this path.

```
Working Directory

↓

git add

↓

Staging Area

↓

git commit

↓

Local Repository
```

Only staged files become part of the commit.

---

# 5. Creating a Commit

First stage your files.

Example

```bash
git add index.html
```

Now commit them.

```bash
git commit -m "Created homepage"
```

Git creates a new snapshot.

---

# 6. git commit

## Syntax

```bash
git commit
```

If you don't provide a message,

Git opens the default editor.

Example

```
Vim

Nano

VS Code
```

You write

```
Added login functionality
```

Save and exit.

Commit created.

---

# Command Breakdown

```
git
```

Git program.

```
commit
```

Create a new snapshot.

---

# Why use git commit without -m?

Useful when writing long commit messages.

Example

```
Added Login Module

Implemented authentication

Added validation

Updated README

Fixed CSS alignment
```

Professional teams often write detailed commit descriptions.

---

# 7. git commit -m

Most commonly used command.

Syntax

```bash
git commit -m "Commit Message"
```

Example

```bash
git commit -m "Added student registration page"
```

Here

```
-m
```

means

```
message
```

Git creates the commit immediately.

---

# Example

```
git add index.html

git commit -m "Created homepage"
```

Output

```
1 file changed

Commit created successfully
```

---

# 8. Commit Specific Files

Many beginners think

```
git commit
```

commits every file.

This is **not true**.

Git commits only **staged files**.

Example

Modified

```
index.html

style.css

README.md
```

Stage only

```bash
git add index.html
```

Commit

```bash
git commit -m "Updated homepage"
```

Result

Only

```
index.html
```

is committed.

Remaining files stay unchanged.

---

# Example Scenario

Suppose

```
about.html

contact.html
```

Both modified.

You finished only

```
about.html
```

Stage

```bash
git add about.html
```

Commit

```bash
git commit -m "Added About page"
```

Later

```
git add contact.html

git commit -m "Added Contact page"
```

Two clean commits.

This is the correct workflow.

---

# 9. Atomic Commits

One of the most important Git concepts.

## What is an Atomic Commit?

An atomic commit contains **one logical change**.

Good Example

```
Added Login Page
```

Another Commit

```
Fixed Login Validation
```

Another Commit

```
Updated Login UI
```

Each commit has one purpose.

---

## Bad Example

```
Added Login

Fixed Footer

Changed Database

Updated README

Modified CSS

Deleted Images
```

Everything inside one commit.

Very difficult to understand.

---

## Why Atomic Commits?

Suppose

```
Commit 25
```

contains

```
Login Feature
```

Only login has a bug.

Easy to revert.

If the commit contains

20 unrelated changes,

rollback becomes difficult.

---

# 10. Commit Message Best Practices

A commit message should explain

**what changed**, not how.

---

## Good Messages

```
Add login page

Fix payment validation

Update README

Create Dockerfile

Configure Jenkins pipeline

Increase Kubernetes replicas
```

---

## Bad Messages

```
Update

Final

Done

Changes

abc

xyz
```

These messages are meaningless.

---

## Follow This Format

```
Add

Fix

Update

Remove

Refactor

Configure

Create

Rename

Delete
```

Example

```
Add student inquiry dashboard

Fix login authentication

Update Docker configuration

Remove unused CSS

Refactor API routes
```

---

# Commit Message Examples

Project

```
E-commerce Website
```

Good commits

```
Create project structure

Add homepage

Add product listing

Fix cart calculation

Configure payment gateway

Update README
```

History becomes very clean.

---

# 11. Real World DevOps Scenario

Suppose you are maintaining

```
Terraform Infrastructure
```

Today

You only update

```
EC2 Instance Type
```

Commit

```
Update EC2 instance type to t3.medium
```

Tomorrow

You configure

```
Security Groups
```

New Commit

```
Configure inbound SSH access
```

Each infrastructure change has its own commit.

If production breaks,

finding the responsible change becomes easy.

---

# 12. Best Practices

✅ Commit frequently.

---

✅ Make small commits.

---

✅ Write meaningful commit messages.

---

✅ One feature = One commit.

---

✅ Commit only tested code.

---

✅ Never mix unrelated changes.

---

# ✅ End of Part 1

In Part 2, we'll learn:

- git log
- git log --oneline
- git log -2
- git show
- Commit Hash
- HEAD
- HEAD~1
- HEAD~2
- git diff
- git diff --staged
- Compare Commits
- Compare Branches
- Common Mistakes
- Interview Questions
- Summary
- Quick Revision
- Navigation

---

# 13. Viewing Commit History

After creating commits, you often need to see what has happened in your repository.

Git provides several commands to inspect commit history.

The most commonly used command is:

```bash
git log
```

---

# 14. git log

## What is git log?

`git log` displays the complete history of commits in the current repository.

It shows:

- Commit ID (Hash)
- Author
- Email
- Date
- Commit Message

---

## Syntax

```bash
git log
```

---

## Example

```bash
git log
```

Output

```text
commit 9f4a8d23a7b4d3e4c5d6e7f8

Author: Abhijeet Salunke <abhijeetsalunke@gmail.com>

Date: Thu Jun 26 11:20:15 2026

    Added Login Page

commit 2a5e4f98d6b1c2a3d4e5f6

Author: Abhijeet Salunke <abhijeetsalunke@gmail.com>

Date: Wed Jun 25 09:15:11 2026

    Initial Project Structure
```

Git displays the **latest commit first**.

---

# Why Use git log?

Use `git log` to:

- View project history
- Check previous commits
- Find commit IDs
- Audit changes
- Identify who made a change

---

# 15. git log --oneline

Sometimes the normal log is too long.

Git provides a shorter format.

```bash
git log --oneline
```

Example

```text
9f4a8d2 Added Login Page

2a5e4f9 Initial Project Structure
```

Benefits

- Compact
- Easy to read
- Useful for daily work

---

# 16. git log -2

Display only the latest **2 commits**.

```bash
git log -2
```

Example

```text
commit 9f4a8d2

Added Login Page

commit 2a5e4f9

Initial Project Structure
```

Similarly

```bash
git log -5
```

shows the latest five commits.

---

# 17. git show

`git show` displays detailed information about a specific commit.

It includes

- Commit information
- Commit message
- Files changed
- Lines added
- Lines removed

---

## Syntax

```bash
git show
```

Shows the latest commit.

---

Specific commit

```bash
git show 9f4a8d2
```

---

Example

```bash
git show HEAD
```

Displays the latest commit.

---

# Why Use git show?

Suppose your teammate says,

> "Check what I changed yesterday."

Instead of opening every file,

simply run

```bash
git show
```

---

# 18. Commit Hash

Every commit has a unique identifier.

Example

```
9f4a8d23a7b4d3e4c5d6e7
```

This is called the **Commit Hash**.

No two commits have the same hash.

Git uses the hash to identify commits.

---

## Short Hash

Usually

```
9f4a8d2
```

is enough.

Git automatically understands it.

---

# Why Commit Hash is Important?

Used for

- Reset
- Revert
- Cherry Pick
- Checkout
- Show
- Compare Commits

Many advanced Git commands use commit hashes.

---

# 19. HEAD

One of the most important Git concepts.

## What is HEAD?

HEAD is a pointer to the **current commit**.

Think of HEAD as:

> "Where am I currently?"

Example

```
Commit 1

↓

Commit 2

↓

Commit 3

↓

HEAD
```

HEAD always points to the latest checked-out commit.

---

# HEAD Example

Suppose your history is

```
Commit A

↓

Commit B

↓

Commit C
```

Current position

```
HEAD

↓

Commit C
```

---

# HEAD~1

Means

```
One commit before HEAD
```

Example

```
Commit A

↓

Commit B ← HEAD~1

↓

Commit C ← HEAD
```

---

# HEAD~2

Means

```
Two commits before HEAD
```

Example

```
Commit A ← HEAD~2

↓

Commit B ← HEAD~1

↓

Commit C ← HEAD
```

Many Git commands use this notation.

Example

```bash
git reset --soft HEAD~1
```

---

# 20. git diff

Before committing,

you may want to see exactly what changed.

Use

```bash
git diff
```

---

## What does git diff show?

It compares

Working Directory

with

Staging Area.

---

Example

Modify

```
index.html
```

Run

```bash
git diff
```

Git displays

- Added lines
- Deleted lines
- Modified lines

---

# 21. git diff --staged

After staging files,

use

```bash
git diff --staged
```

to see what will actually be committed.

This compares

Staging Area

with

Local Repository.

---

Example Workflow

```
Modify File

↓

git add

↓

git diff --staged

↓

git commit
```

This is considered a good habit.

---

# 22. Compare Commits

Git can compare two commits.

Example

```bash
git diff commit1 commit2
```

Git displays

- Added code
- Removed code
- Modified code

Very useful while debugging.

---

# 23. Compare Branches

Compare two branches.

Example

```bash
git diff main feature-login
```

Git displays all differences between the branches.

Very useful before merging.

---

# 24. Real World DevOps Scenario

Suppose your team maintains Terraform infrastructure.

Yesterday

```
Commit

Add EC2 Instance
```

Today

```
Commit

Configure Security Group
```

Production suddenly breaks.

Using

```bash
git log
```

you identify recent commits.

Then

```bash
git show
```

checks the exact change.

Finally

```bash
git diff
```

compares commits to find what introduced the issue.

This makes troubleshooting much faster.

---

# 25. Best Practices

✅ Commit frequently.

---

✅ Use meaningful commit messages.

---

✅ Review changes using

```bash
git diff
```

before committing.

---

✅ Use

```bash
git log --oneline
```

for quick history.

---

✅ Keep commits small and focused.

---

# 26. Common Mistakes

❌ Writing meaningless commit messages.

---

❌ Creating huge commits.

---

❌ Forgetting to review changes before committing.

---

❌ Not checking history before reverting.

---

# 27. Interview Questions

### Q1. What is a Commit?

A permanent snapshot of the project.

---

### Q2. What information does a commit contain?

- Commit Hash
- Author
- Email
- Date
- Message

---

### Q3. What is HEAD?

A pointer to the current commit.

---

### Q4. Difference between

```bash
git log
```

and

```bash
git log --oneline
```

`git log`

Shows detailed history.

`git log --oneline`

Shows compact history.

---

### Q5. Difference between

```bash
git diff
```

and

```bash
git diff --staged
```

`git diff`

Shows unstaged changes.

`git diff --staged`

Shows staged changes.

---

### Q6. What is a Commit Hash?

A unique identifier for every commit.

---

# 28. Summary

In this chapter, you learned:

- What is a Commit?
- Commit Lifecycle
- Atomic Commits
- Commit Message Best Practices
- git commit
- git log
- git log --oneline
- git log -2
- git show
- Commit Hash
- HEAD
- HEAD~1
- HEAD~2
- git diff
- git diff --staged
- Compare Commits
- Compare Branches

---

# 📝 Quick Revision

Create Commit

```bash
git commit -m "message"
```

---

View History

```bash
git log
```

---

Compact History

```bash
git log --oneline
```

---

Latest Two Commits

```bash
git log -2
```

---

Show Latest Commit

```bash
git show
```

---

Show Differences

```bash
git diff
```

---

Show Staged Differences

```bash
git diff --staged
```

---

# 🎯 Key Takeaways

- A commit is a permanent snapshot of your project.
- Every commit has a unique hash.
- HEAD always points to your current commit.
- Use `git log` to explore history.
- Use `git show` to inspect commits.
- Use `git diff` before committing to review changes.
- Small, meaningful commits make collaboration and debugging much easier.

---

## 📖 Navigation

⬅ Previous:
**04-Git-Workflow-and-Core-Commands.md**

➡ Next:
**06-Undoing-Changes-and-Recovery.md**
