# 06. Undoing Changes and Recovery

> 📘 Module: Undoing Changes & Recovery
>
> 🎯 Difficulty: Intermediate
>
> ⏱ Estimated Reading Time: 25–30 Minutes
>
> 💻 Prerequisites:
>
> - Git Workflow
> - Git Commit
> - Git History

---

# 📖 Introduction

No developer writes perfect code every time.

Sometimes you accidentally:

- Modify the wrong file
- Stage the wrong file
- Commit incorrect code
- Delete important files
- Push unwanted changes

Git provides several commands to safely undo changes and recover lost work.

Understanding these commands is one of the most important skills for every DevOps Engineer and Software Developer.

---

# 📚 Table of Contents

## Part A – Undoing Changes

1. Why Undo Changes?
2. Git Restore
3. git restore
4. git restore --staged
5. git rm
6. git mv
7. .gitignore
8. Ignoring Files
9. Ignoring Folders
10. Ignoring Sensitive Files
11. git commit --amend

## Part B – Recovery

12. git reset
13. Soft Reset
14. Mixed Reset
15. Hard Reset
16. git revert
17. git reflog
18. Recover Deleted Commits
19. Best Practices
20. Interview Questions
21. Summary

---

# Part A – Undoing Changes

---

# 1. Why Undo Changes?

Mistakes happen in every project.

Imagine these situations.

- Accidentally modified a file.
- Added the wrong files to staging.
- Deleted a file by mistake.
- Forgot to add a file before committing.
- Added passwords into Git.

Git provides different commands for each situation.

Understanding **which command to use** is more important than memorizing commands.

---

# Git Undo Decision Tree

```
Modified File
        │
        ▼
git restore

-----------------------

Wrong File Staged
        │
        ▼
git restore --staged

-----------------------

Need to Delete File
        │
        ▼
git rm

-----------------------

Rename File
        │
        ▼
git mv

-----------------------

Forgot File in Last Commit
        │
        ▼
git commit --amend
```

---

# 2. Git Restore

Before Git 2.23,

developers used

```bash
git checkout
```

for almost everything.

Nowadays,

Git recommends

```bash
git restore
```

for restoring files.

It is easier to understand and safer.

---

# What is git restore?

It restores a file from the last committed version.

It discards local modifications.

Think of it as

> "Undo my local changes."

---

# When Should You Use It?

Use

```bash
git restore
```

when

- You modified a file.
- You don't want those changes.
- The file is NOT committed yet.

---

# Example

Current project

```
Student-System/

index.html

about.html

style.css
```

You accidentally change

```
style.css
```

You decide to discard all modifications.

Run

```bash
git restore style.css
```

Git restores the previous committed version.

---

# Syntax

```bash
git restore <filename>
```

Example

```bash
git restore index.html
```

---

# Before Restore

```
index.html

Modified
```

After

```bash
git restore index.html
```

```
index.html

Original Version Restored
```

---

# 3. git restore --staged

This command removes files from the Staging Area.

It does NOT delete your work.

It only unstages the file.

---

## Why Use It?

Suppose

```
git add .
```

accidentally stages

```
password.txt

index.html

README.md
```

You only wanted

```
README.md
```

Instead of committing everything,

remove unwanted files.

---

Command

```bash
git restore --staged password.txt
```

Now

```
password.txt
```

returns to

Working Directory.

Your work remains safe.

---

# Difference

```
git restore
```

Discard changes.

---

```
git restore --staged
```

Remove from staging only.

---

# Workflow

```
Working Directory

↓

git add

↓

Staging Area

↓

git restore --staged

↓

Working Directory
```

---

# Example

```bash
git add .
```

Oops...

Wrong files staged.

Run

```bash
git restore --staged .
```

Everything becomes unstaged.

---

# 4. git rm

Used to remove files from

- Working Directory
- Git Repository

Command

```bash
git rm filename
```

Example

```bash
git rm old-logo.png
```

Git removes

```
old-logo.png
```

and stages the deletion.

---

# Difference

```
rm file
```

Linux command.

Git doesn't know.

---

```
git rm file
```

Git knows.

Deletion becomes part of the next commit.

---

# Example

```
images/

logo.png
```

Delete

```bash
git rm images/logo.png
```

Commit

```bash
git commit -m "Remove old logo"
```

History records the deletion.

---

# 5. git mv

Used to rename or move files.

Instead of

```
mv file1 file2
```

use

```bash
git mv
```

Git automatically tracks the rename.

---

# Syntax

```bash
git mv old-name new-name
```

Example

```bash
git mv home.html index.html
```

Git stages the rename.

---

# Why git mv?

Without Git

```
Delete File

Create New File
```

Git may see it as two separate actions.

With

```bash
git mv
```

Git understands it is a rename.

---

# 6. .gitignore

Some files should never be committed.

Examples

```
Passwords

Logs

Temporary Files

Build Files

Node Modules

IDE Settings
```

Git ignores these using

```
.gitignore
```

---

# Example

```
node_modules/

.env

*.log

*.tmp
```

Git ignores them.

---

# Why Use .gitignore?

Imagine

```
node_modules/
```

contains

200,000 files.

Uploading them to GitHub is unnecessary.

Instead

```
.gitignore
```

prevents Git from tracking them.

---

# Ignore Sensitive Files

Never commit

```
.env

password.txt

secret.key

aws.pem

id_rsa
```

Instead

```
.gitignore
```

```
.env

*.pem

id_rsa
```

---

# 7. git commit --amend

Sometimes

you create a commit,

then realize

"I forgot one file."

Instead of creating another commit,

Git allows you to modify the latest commit.

---

# Example

Commit

```bash
git commit -m "Added Login Module"
```

Oops...

Forgot

```
README.md
```

Stage

```bash
git add README.md
```

Now run

```bash
git commit --amend --no-edit
```

Git updates the previous commit.

No new commit is created.

---

# Change Commit Message

```bash
git commit --amend -m "Add Login Module with Documentation"
```

Git updates only the latest commit message.

---

# Change Author

```bash
git commit --amend --author="Abhijeet Salunke <abhijeetsalunke@gmail.com>"
```

Useful when you accidentally commit with the wrong username or email.

---

# Real World DevOps Scenario

Suppose you create

```
Dockerfile

docker-compose.yml
```

Commit

```
Configure Docker
```

Later,

you realize

```
README.md
```

was forgotten.

Instead of

```
Configure Docker

Update README
```

you simply amend the previous commit.

Your Git history remains clean.

---

# Best Practices (Part A)

✅ Use `git restore` for local changes.

✅ Use `git restore --staged` when only the staging area is wrong.

✅ Prefer `git mv` over the Linux `mv` command for tracked files.

✅ Never commit passwords, API keys, or certificates.

✅ Use `.gitignore` from the beginning of every project.

---

# ✅ End of Part 1

In Part 2, we'll learn:

- `git reset`
- Soft, Mixed, and Hard Reset
- `git revert`
- `git reflog`
- Recover Deleted Commits
- Reset vs Revert
- Real DevOps Recovery Scenarios
- Common Mistakes
- Interview Questions
- Summary
- Quick Revision
- Navigation

---

# Part B – Recovery

Sometimes mistakes are bigger than modifying a file.

Examples

- Wrong commit
- Wrong commit message
- Deleted commit
- Accidental reset
- Pushed bad code

Git provides recovery commands to safely handle these situations.

---

# 8. Git Reset

## What is git reset?

`git reset` moves the **HEAD** pointer to another commit.

Depending on the option used, it can also modify the

- Staging Area
- Working Directory

Git Reset has three modes.

```
Soft Reset

↓

Mixed Reset

↓

Hard Reset
```

---

# Reset Decision Diagram

```
Need to remove only commit?

↓

git reset --soft

-----------------------

Need to remove commit + unstage files?

↓

git reset --mixed

-----------------------

Need to remove everything?

↓

git reset --hard
```

---

# 9. git reset --soft

Soft Reset removes only the latest commit.

Your files remain staged.

---

## Syntax

```bash
git reset --soft HEAD~1
```

---

## Example

History

```
Commit 1

↓

Commit 2

↓

Commit 3 ← HEAD
```

Run

```bash
git reset --soft HEAD~1
```

Now

```
Commit 1

↓

Commit 2 ← HEAD
```

Commit 3 disappears from history,

but its changes remain in the Staging Area.

---

## When to Use

Suppose

You committed

```
Add Login Page
```

Then realized

the commit message is wrong.

Use

```bash
git reset --soft HEAD~1
```

Edit

Commit again.

---

# 10. git reset --mixed

Mixed Reset removes the commit

and also removes files from the Staging Area.

Your code is still safe inside the Working Directory.

---

## Syntax

```bash
git reset --mixed HEAD~1
```

or simply

```bash
git reset HEAD~1
```

because `--mixed` is the default mode.

---

## Workflow

Before

```
Working Directory

↓

Staging

↓

Commit
```

After

```
Working Directory
```

Only.

Files become unstaged.

---

## When to Use

You committed too early.

Need to reorganize commits.

---

# 11. git reset --hard

⚠ Warning

This command permanently deletes local changes.

---

## Syntax

```bash
git reset --hard HEAD~1
```

---

## Example

Before

```
Commit 1

↓

Commit 2

↓

Commit 3 ← HEAD
```

Run

```bash
git reset --hard HEAD~1
```

After

```
Commit 1

↓

Commit 2 ← HEAD
```

Commit 3

Files

Changes

Everything disappears.

---

## When Should You Use It?

Only when

You are 100% sure

those changes are no longer needed.

---

# Reset Comparison

| Command | Commit | Staging | Working Directory |
|----------|---------|----------|-------------------|
| Soft | Removed | Safe | Safe |
| Mixed | Removed | Cleared | Safe |
| Hard | Removed | Removed | Removed |

---

# 12. Git Revert

## What is git revert?

Instead of deleting history,

Git creates a **new commit**

that reverses previous changes.

History remains safe.

---

## Syntax

```bash
git revert HEAD
```

---

## Example

History

```
Commit A

↓

Commit B

↓

Commit C
```

Run

```bash
git revert HEAD
```

Git creates

```
Commit D

Undo Commit C
```

History

```
A

↓

B

↓

C

↓

D
```

Nothing is deleted.

---

## Why Use git revert?

Safe for

Production repositories.

Shared repositories.

Team projects.

---

# Reset vs Revert

| Reset | Revert |
|---------|---------|
| Deletes history | Preserves history |
| Rewrites commits | Creates new commit |
| Good before push | Good after push |
| Dangerous on shared branches | Safe on shared branches |

---

# 13. Git Reflog

One of Git's most powerful commands.

---

## What is Reflog?

Git records every movement of HEAD.

Even deleted commits can often be recovered.

---

## Syntax

```bash
git reflog
```

---

## Example

```text
HEAD@{0}

Commit Login

HEAD@{1}

Commit Homepage

HEAD@{2}

Initial Commit
```

Even if commits disappear from

```
git log
```

they usually remain inside

```
git reflog
```

---

# Why is Reflog Important?

Imagine

```
git reset --hard HEAD~3
```

Oops...

Important commits disappeared.

Instead of panicking

Run

```bash
git reflog
```

Git shows the lost commit IDs.

Recover them.

---

# 14. Recover Deleted Commits

Suppose

```
git reset --hard HEAD~2
```

deleted

```
Login Module
```

Run

```bash
git reflog
```

Find

```
9f4a8d2
```

Recover

```bash
git reset --hard 9f4a8d2
```

Project restored.

---

# Recovery Workflow

```
Deleted Commit

↓

git reflog

↓

Find Commit Hash

↓

git reset --hard CommitID

↓

Recovered
```

---

# 15. Real World DevOps Scenario

Imagine

Production deployment failed.

Yesterday

Someone committed

```
Incorrect Kubernetes YAML
```

Production is broken.

DevOps Engineer

checks

```bash
git log
```

Finds bad commit.

Instead of deleting history,

uses

```bash
git revert HEAD
```

Rollback complete.

History remains intact.

Entire team can understand

what happened.

---

# 16. Best Practices

✅ Use `git restore` for local file changes.

---

✅ Use `git commit --amend` only for the latest commit.

---

✅ Use `git reset --soft` before pushing.

---

✅ Avoid `git reset --hard` unless absolutely necessary.

---

✅ Use `git revert` for shared repositories.

---

✅ Learn `git reflog`.

It can save hours of work.

---

# 17. Common Mistakes

❌ Running

```bash
git reset --hard
```

without understanding it.

---

❌ Forgetting

```bash
git reflog
```

exists.

---

❌ Using Reset

after pushing to GitHub.

---

❌ Deleting files manually instead of

```bash
git rm
```

---

# 18. Interview Questions

### Q1. Difference between git restore and git restore --staged?

---

### Q2. Difference between Reset and Revert?

---

### Q3. Difference between Soft, Mixed and Hard Reset?

---

### Q4. Which Reset mode is default?

Answer

```
Mixed
```

---

### Q5. Which command recovers deleted commits?

```bash
git reflog
```

---

### Q6. Which command is safest after pushing?

```bash
git revert
```

---

### Q7. Can git reflog recover accidentally deleted commits?

Answer

Yes.

As long as Git still has the commit reference.

---

# 19. Summary

In this chapter you learned

- git restore
- git restore --staged
- git rm
- git mv
- .gitignore
- git commit --amend
- git reset
- Soft Reset
- Mixed Reset
- Hard Reset
- git revert
- git reflog
- Recover Deleted Commits

---

# 📝 Quick Revision

Discard Local Changes

```bash
git restore file.txt
```

---

Unstage File

```bash
git restore --staged file.txt
```

---

Delete File

```bash
git rm file.txt
```

---

Rename File

```bash
git mv old.txt new.txt
```

---

Ignore Files

```
.gitignore
```

---

Amend Last Commit

```bash
git commit --amend
```

---

Soft Reset

```bash
git reset --soft HEAD~1
```

---

Mixed Reset

```bash
git reset HEAD~1
```

---

Hard Reset

```bash
git reset --hard HEAD~1
```

---

Revert Commit

```bash
git revert HEAD
```

---

Recover Lost Commits

```bash
git reflog
```

---

# 🎯 Key Takeaways

- `git restore` is for undoing local file changes.
- `git restore --staged` removes files from the staging area without deleting your work.
- `git commit --amend` modifies only the latest commit.
- `git reset` rewrites history and should be used carefully.
- `git revert` is the safest option for undoing changes that have already been shared.
- `git reflog` is an essential recovery tool that can often restore commits after mistakes.

---

## 📖 Navigation

⬅ Previous:
**05-Working-with-Commits-and-History.md**

➡ Next:
**07-Branching-and-Merging.md**
