# 11. Git Hooks and Git Internals

> 📘 Module: Git Hooks & Git Internals
>
> 🎯 Difficulty: Advanced
>
> ⏱ Estimated Reading Time: 35–40 Minutes
>
> 💻 Prerequisites:
>
> - Git Workflow
> - Git Commits
> - Git Branches
> - Git History

---

# 📖 Introduction

Most developers know how to use Git commands.

Very few know **how Git actually works internally**.

Understanding Git Internals helps you

- Troubleshoot Git problems
- Understand repository structure
- Learn how Git stores data
- Automate tasks using Git Hooks

Every DevOps Engineer should know these concepts.

---

# 📚 Table of Contents

## Part 1

1. What are Git Hooks?
2. Why Git Hooks?
3. Types of Git Hooks
4. Pre-commit Hook
5. Post-commit Hook
6. Pre-push Hook
7. Hook Location
8. Creating Hooks
9. Real DevOps Scenario

## Part 2

10. Detached HEAD
11. Git Objects
12. Blob Object
13. Tree Object
14. Commit Object
15. Git Index
16. Git Garbage Collection
17. Best Practices
18. Interview Questions
19. Summary

---

# Part 1

# 1. What are Git Hooks?

Git Hooks are scripts that Git automatically executes when certain events occur.

Think of them as **automation points** inside Git.

Example

```
git commit

↓

Pre-commit Hook

↓

Commit Created
```

Hooks allow you to perform actions automatically before or after Git commands.

---

# Why Git Hooks?

Imagine every developer in your team should:

- Format code
- Run tests
- Check for secrets
- Validate commit messages

Instead of relying on developers to remember,

Git Hooks automate these checks.

---

# Hook Workflow

```
Developer

↓

git commit

↓

Git Hook

↓

Validation

↓

Commit
```

---

# 2. Types of Git Hooks

Git provides many hooks.

The most common ones are:

- Pre-commit
- Commit-msg
- Post-commit
- Pre-push

Each runs at a different stage of the Git workflow.

---

# 3. Pre-commit Hook

Runs **before a commit is created**.

If the hook fails,

the commit is stopped.

---

## Common Uses

✔ Run unit tests

✔ Check code formatting

✔ Scan for secrets

✔ Validate files

---

## Example

```
git commit

↓

Pre-commit

↓

Tests Pass

↓

Commit Created
```

---

# Real Example

Suppose your project requires every Python file to be formatted.

A Pre-commit Hook automatically runs:

```
black .
```

If formatting fails,

Git prevents the commit.

---

# 4. Post-commit Hook

Runs **after a successful commit**.

Unlike Pre-commit,

it cannot stop the commit.

---

## Common Uses

- Notifications
- Logging
- Triggering local scripts

---

Workflow

```
git commit

↓

Commit Created

↓

Post-commit Hook

↓

Notification
```

---

# 5. Pre-push Hook

Runs **before code is pushed** to the remote repository.

---

## Common Uses

✔ Run tests

✔ Check build status

✔ Prevent pushing sensitive files

✔ Security scanning

---

Example

```
git push

↓

Pre-push Hook

↓

Security Scan

↓

Push Allowed
```

---

# 6. Where are Hooks Stored?

Every Git repository contains a hooks directory.

Location

```
.git/hooks/
```

Example

```
.git/

hooks/

pre-commit.sample

pre-push.sample

post-commit.sample
```

Git provides sample hook files.

You can rename and customize them.

---

# 7. Creating a Hook

Example

```
.git/hooks/pre-commit
```

Make it executable

```bash
chmod +x .git/hooks/pre-commit
```

Example Script

```bash
#!/bin/bash

echo "Running Tests..."

npm test
```

Now every commit runs the tests automatically.

---

# 8. Real World DevOps Scenario

Imagine your company stores infrastructure as code.

Developers modify

```
Terraform

Kubernetes YAML

Dockerfile
```

Before every commit,

a Pre-commit Hook automatically checks

✔ YAML syntax

✔ Terraform formatting

✔ Secret scanning

Only valid code is committed.

---

# Best Practices

✅ Keep hooks fast.

---

✅ Automate repetitive tasks.

---

✅ Never store sensitive data inside hooks.

---

✅ Use hooks to improve code quality.

---

# 🧠 Memory Tip

Think of Git Hooks as

**Automatic Security Guards**

Every Git action passes through them.

---

# ✅ End of Part 1

In Part 2 we'll learn

- Detached HEAD
- Git Objects
- Blob
- Tree
- Commit Object
- Git Index
- Git Garbage Collection
- Interview Questions
- Summary

---

# Part 2

# 9. Detached HEAD

## What is HEAD?

HEAD is a pointer that always points to your current branch or current commit.

Normally

```
HEAD

↓

main

↓

Latest Commit
```

Git knows where you are.

---

## What is Detached HEAD?

A Detached HEAD occurs when HEAD points directly to a commit instead of a branch.

Example

```
main

↓

Commit A

↓

Commit B

↓

Commit C
```

Command

```bash
git checkout 9f4a8d2
```

Now

```
HEAD

↓

Commit B
```

You are no longer on

```
main
```

You are directly on a commit.

---

## Why Does Detached HEAD Happen?

Common reasons

- Viewing old commits
- Testing old versions
- Debugging previous code
- Checking releases

---

## Why is Detached HEAD Dangerous?

Suppose

You modify files

Commit

```bash
git commit -m "Temporary Fix"
```

Later

Switch back

```bash
git switch main
```

Your new commit becomes difficult to find because it is not attached to any branch.

---

## How to Fix Detached HEAD?

Create a branch immediately.

```bash
git switch -c bugfix-old-version
```

Now your work is safe.

---

# 10. Git Objects

Everything in Git is stored as an object.

Git mainly stores four types of objects.

```
Blob

↓

Tree

↓

Commit

↓

Tag
```

Every file and commit eventually becomes one of these objects.

---

# Object Relationship

```
Files

↓

Blob

↓

Tree

↓

Commit

↓

Branch
```

---

# 11. Blob Object

Blob stands for

```
Binary Large Object
```

A Blob stores the contents of a file.

Example

```
index.html
```

Git converts it into

```
Blob Object
```

Blob stores

✔ File Content

Not

✔ File Name

---

Example

```
index.html

↓

Blob
```

---

# 12. Tree Object

Tree Objects store directory information.

Example

```
Project/

index.html

style.css

images/

logo.png
```

Git stores

```
Tree

↓

Blob

↓

Blob

↓

Tree

↓

Blob
```

Tree keeps folder structure.

---

# 13. Commit Object

Commit Object connects everything.

It stores

- Author
- Email
- Date
- Commit Message
- Parent Commit
- Tree Object

---

Diagram

```
Commit

↓

Tree

↓

Blob

↓

File Content
```

---

# Commit Object Example

```
Commit

↓

Tree

↓

index.html

↓

Blob
```

---

# 14. Git Index

Git Index is another name for the

```
Staging Area
```

Whenever you run

```bash
git add
```

Git stores information inside the Index.

Workflow

```
Working Directory

↓

Git Index

↓

Commit
```

---

# Why Git Index?

Allows Git to know

exactly

what will be committed.

---

# 15. Git Garbage Collection (GC)

Git stores many unnecessary objects over time.

Examples

- Old commits
- Temporary objects
- Unreachable objects

Git cleans them automatically.

Command

```bash
git gc
```

---

## Why Use git gc?

Benefits

✔ Reduce Repository Size

✔ Improve Performance

✔ Remove Unused Objects

✔ Optimize Repository

---

Example

```bash
git gc
```

Git compresses objects

and removes unnecessary data.

---

# 16. Real World DevOps Scenario

Suppose

Your company has

a repository with

10 years of history.

Thousands of branches.

Millions of Git objects.

Repository becomes slow.

Git periodically runs

```bash
git gc
```

to optimize storage and improve performance.

Meanwhile,

Git Hooks ensure

every Infrastructure-as-Code commit passes validation.

Both concepts work together to keep repositories healthy and reliable.

---

# 17. Best Practices

## Git Hooks

✅ Keep hook scripts lightweight.

✅ Use hooks to automate quality checks.

✅ Share hook logic using tools like **pre-commit** if your team wants consistent behavior across machines.

---

## Git Internals

✅ Understand HEAD before using advanced commands.

✅ Learn Git Objects for troubleshooting.

✅ Run

```bash
git gc
```

occasionally on very large repositories if needed (Git also performs maintenance automatically).

---

# 18. Common Mistakes

❌ Ignoring Detached HEAD warnings.

---

❌ Editing commits in Detached HEAD without creating a branch.

---

❌ Writing slow Pre-commit Hooks.

---

❌ Assuming Git stores files exactly as they appear on disk.

---

# 19. Interview Questions

### Q1. What is a Git Hook?

A script that automatically runs when specific Git events occur.

---

### Q2. Where are Git Hooks stored?

```
.git/hooks/
```

---

### Q3. Difference between Pre-commit and Post-commit?

Pre-commit

Runs before commit.

Can stop the commit.

Post-commit

Runs after commit.

Cannot stop the commit.

---

### Q4. What is Detached HEAD?

A state where HEAD points directly to a commit instead of a branch.

---

### Q5. What is a Blob Object?

Stores the contents of a file.

---

### Q6. What is a Tree Object?

Stores the directory structure and references to blobs and subtrees.

---

### Q7. What is the Git Index?

Another name for the Staging Area.

---

### Q8. What does

```bash
git gc
```

do?

Optimizes the repository and removes unnecessary objects.

---

# 20. Summary

In this chapter you learned

- Git Hooks
- Pre-commit Hook
- Post-commit Hook
- Pre-push Hook
- Hook Location
- Detached HEAD
- Git Objects
- Blob
- Tree
- Commit Object
- Git Index
- Git Garbage Collection

---

# 📝 Quick Revision

Pre-commit Hook

```
Runs Before Commit
```

---

Post-commit Hook

```
Runs After Commit
```

---

Pre-push Hook

```
Runs Before Push
```

---

Detached HEAD

```
HEAD → Commit
```

---

Git Objects

```
Blob

↓

Tree

↓

Commit
```

---

Git Index

```
Staging Area
```

---

Optimize Repository

```bash
git gc
```

---

# 📌 Command Reference

| Command | Purpose |
|---------|---------|
| `git checkout <commit>` | View an old commit (may enter Detached HEAD state) |
| `git switch -c <branch>` | Create a branch from the current commit |
| `chmod +x .git/hooks/pre-commit` | Make a hook executable |
| `git gc` | Optimize and clean the repository |

---

# 🎯 Key Takeaways

- Git Hooks automate actions before or after Git operations.
- Pre-commit Hooks help enforce code quality before commits.
- Detached HEAD is useful for inspection but risky for ongoing work unless you create a branch.
- Git stores data as objects (Blob, Tree, Commit, and Tag).
- The Git Index is the staging area between your working directory and commits.
- `git gc` helps optimize repository storage and performance.

---

## 📖 Navigation

⬅ Previous:
**10-GitHub-Collaboration-and-Features.md**

➡ Next:
**12-DevOps-Git-Workflows.md**
