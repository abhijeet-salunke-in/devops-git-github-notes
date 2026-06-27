# 07. Branching and Merging

> 📘 Module: Branching & Merging
>
> 🎯 Difficulty: Intermediate
>
> ⏱ Estimated Reading Time: 30–35 Minutes
>
> 💻 Prerequisites:
>
> - Git Workflow
> - Git Commits
> - Git History
> - Undoing Changes & Recovery

---

# 📖 Introduction

One of Git's most powerful features is **Branching**.

Branches allow developers to work on different features, bug fixes, and releases without affecting the main project.

Imagine an e-commerce website that is already live.

Customers are using it every day.

Now the company wants to add a new **Payment Gateway**.

Should developers directly modify the live code?

**No.**

Instead, they create a new branch, develop the feature safely, test it, and merge it into the main branch only when it is ready.

Branching is the foundation of modern software development and DevOps.

---

# 📚 Table of Contents

## Part 1 – Branching

1. What is a Branch?
2. Why Branching is Needed
3. How Branches Work
4. Main Branch
5. Development Branch
6. Feature Branch
7. Release Branch
8. Hotfix Branch
9. Branch Naming Convention
10. git branch
11. Create Branch
12. List Branches
13. Current Branch
14. Rename Branch
15. Delete Branch
16. Force Delete Branch
17. git switch
18. git checkout
19. switch vs checkout

## Part 2 – Merging

20. What is Merge?
21. Fast Forward Merge
22. Three Way Merge
23. Merge Conflict
24. Resolve Merge Conflict
25. Real World DevOps Scenario
26. Best Practices
27. Interview Questions
28. Summary

---

# 1. What is a Branch?

A branch is an independent line of development.

Think of a branch as a copy of your project where you can work safely.

Instead of changing the main project,

you create another branch.

```
Main Branch

↓

Feature Branch
```

The feature branch contains the same project,

but changes made here do not affect the main branch until merged.

---

# Real Life Example

Imagine writing a book.

Original Book

↓

Create Copy

↓

Write New Chapter

↓

Review

↓

Merge into Original

Git branches work the same way.

---

# 2. Why Branching is Needed?

Suppose your company has a live website.

```
www.company.com
```

Users are actively using it.

Now you need to add

```
Payment Gateway
```

If you modify the live project directly,

customers may experience bugs.

Instead

```
Main Branch

↓

Feature Branch

↓

Testing

↓

Merge

↓

Production
```

This keeps production safe.

---

# Benefits of Branching

✔ Safe Development

✔ Team Collaboration

✔ Easy Bug Fixes

✔ Parallel Development

✔ Better Code Review

✔ Easy Rollback

---

# 3. How Branches Work

Initially,

Git has only one branch.

```
main
```

After creating a branch

```
main

│

├── feature-login
```

Both branches contain the same code initially.

After some time

```
main

Home Page

Products

Cart

│

├── feature-login

Home Page

Products

Cart

Login Page
```

Only the feature branch changes.

Main remains unchanged.

---

# 4. Main Branch

The Main branch is the primary branch.

Usually

```
main
```

or

```
master
```

(Older Git versions.)

Production-ready code should always remain here.

---

## Rules

Never experiment directly on the main branch.

Always use Pull Requests.

Protect the main branch.

---

# 5. Development Branch

Many companies create another branch called

```
develop
```

Workflow

```
main

↓

develop

↓

feature branches
```

Developers merge into

```
develop
```

After testing,

develop merges into

```
main
```

---

# Why Use Develop Branch?

Keeps production isolated.

Allows multiple developers to work together safely.

---

# 6. Feature Branch

Every new feature gets its own branch.

Examples

```
feature-login

feature-payment

feature-search

feature-profile
```

Once completed,

the feature branch is merged.

---

# Example Workflow

```
main

↓

feature-login

↓

Login Completed

↓

Merge

↓

main
```

---

# 7. Release Branch

When the software is almost ready,

companies create a

```
release
```

branch.

Purpose

- Final Testing

- Bug Fixes

- Documentation

Only critical changes are allowed.

---

# Example

```
main

↓

develop

↓

release-v2.0
```

After testing

Release

↓

Main

---

# 8. Hotfix Branch

Suppose

Production website crashes.

Customers cannot place orders.

Developers don't wait for the next release.

They create

```
hotfix-payment
```

Fix

↓

Merge into Main

↓

Deploy

Problem solved.

---

# Hotfix Workflow

```
main

↓

hotfix-payment

↓

Bug Fixed

↓

Merge

↓

Production
```

---

# 9. Branch Naming Convention

Professional naming examples

```
feature/login

feature/cart

feature/payment

bugfix/navbar

hotfix/login

release/v2.0

develop

main
```

Avoid names like

```
test

abc

new

branch1
```

---

# 10. git branch

Shows all local branches.

Command

```bash
git branch
```

Output

```text
* main

develop

feature-login
```

The

```
*
```

shows the current branch.

---

# 11. Create Branch

Command

```bash
git branch feature-login
```

Git creates the branch.

You still remain on

```
main
```

---

# Verify

```bash
git branch
```

Output

```
* main

feature-login
```

---

# 12. Current Branch

Check current branch

```bash
git branch
```

Example

```
* main
```

You are currently on

```
main
```

---

# 13. Rename Branch

Command

```bash
git branch -m old-name new-name
```

Example

```bash
git branch -m feature-login feature-authentication
```

Branch renamed successfully.

---

# 14. Delete Branch

Delete merged branch

```bash
git branch -d feature-login
```

Git deletes the branch safely.

---

# 15. Force Delete Branch

Delete unmerged branch

```bash
git branch -D feature-login
```

Use carefully.

---

# 16. git switch

Modern Git command.

Switch branches.

```bash
git switch feature-login
```

---

Create and switch

```bash
git switch -c feature-payment
```

Equivalent to

```
Create Branch

↓

Switch Branch
```

---

# 17. git checkout

Older Git command.

Switch branch

```bash
git checkout feature-login
```

Create branch

```bash
git checkout -b feature-payment
```

---

# 18. switch vs checkout

| git switch | git checkout |
|------------|--------------|
| New command | Older command |
| Easier | More powerful |
| Branch switching | Branch + File operations |
| Recommended | Backward compatibility |

---

# Real World DevOps Scenario

Suppose you join Amazon as a DevOps Engineer.

The production Kubernetes cluster is already running.

Manager asks you

> "Increase nginx replicas from 3 to 5."

Would you modify

```
main
```

No.

Workflow

```
main

↓

feature/increase-replicas

↓

Modify deployment.yaml

↓

Testing

↓

Pull Request

↓

Review

↓

Merge

↓

Jenkins

↓

Deploy
```

Production remains safe.

---

# Best Practices

✅ One feature → One branch

✅ Use meaningful branch names

✅ Never work directly on main

✅ Delete merged feature branches

✅ Keep feature branches small

---

# 🧠 Memory Tip

Imagine a tree.

```
          main

        /      \

 feature-A   feature-B

      \        /

       \      /

        Merge
```

Every branch grows independently.

Only after merging do all branches become one project again.

---

# ✅ End of Part 1

In Part 2 we'll learn:

- What is Merge?
- Fast Forward Merge
- Three Way Merge
- Merge Conflicts
- Resolve Merge Conflicts
- Merge Strategy
- Real Company Workflow
- Git Flow
- Best Practices
- Interview Questions
- Summary
- Quick Revision
- Navigation

---

# Part 2 – Merging

After completing work on a branch, the next step is to combine those changes into another branch.

This process is called **Merging**.

Without merging, every branch would remain isolated forever.

---

# 19. What is Merge?

A merge combines changes from one branch into another.

Most commonly,

a feature branch is merged into the main branch.

```
main

│

├── feature-login

│

│ Login Completed

│

▼

Merge

↓

main
```

Now the login feature becomes part of the main branch.

---

# Why Merge?

Suppose

You created

```
feature-payment
```

and completed the Payment Gateway.

Users still cannot use it because it exists only inside

```
feature-payment
```

To make it available,

merge it into

```
main
```

---

# Merge Workflow

```
Create Branch

↓

Develop Feature

↓

Test

↓

Merge

↓

Delete Branch
```

This is the workflow followed by almost every software company.

---

# 20. Merge Command

Before merging,

switch to the target branch.

Example

```bash
git switch main
```

Now merge

```bash
git merge feature-login
```

Git combines both branches.

---

# Example

Current Branch

```
main
```

Other Branch

```
feature-login
```

Command

```bash
git merge feature-login
```

Result

```
Login Page

↓

Added to Main
```

---

# 21. Fast Forward Merge

A Fast Forward Merge happens when

the target branch has **no new commits**.

Example

```
main

↓

Commit A

↓

feature-login

↓

Commit B
```

Main has not changed.

Git simply moves the pointer.

```
Before

main

↓

A

↓

feature

↓

B

After Merge

main

↓

B
```

No merge commit is created.

---

# Advantages

✔ Clean history

✔ Faster

✔ No extra merge commit

---

# 22. Three-Way Merge

Sometimes both branches change.

Example

```
main

↓

Commit A

↓

Commit C

feature

↓

Commit B
```

Now Git cannot simply move the pointer.

It creates a new Merge Commit.

```
Commit A

│

├── Commit B

│

└── Commit C

↓

Merge Commit
```

This is called a **Three-Way Merge**.

---

# Advantages

✔ Preserves history

✔ Shows branch relationships

✔ Most common in team projects

---

# Fast Forward vs Three-Way Merge

| Fast Forward | Three-Way |
|--------------|-----------|
| No merge commit | Creates merge commit |
| Linear history | Branch history preserved |
| Simple | Used in team projects |
| Faster | More informative |

---

# 23. What is a Merge Conflict?

A Merge Conflict occurs when

two branches modify the **same part** of the same file.

Git cannot decide which change should be kept.

Human intervention is required.

---

# Example

Main Branch

```html
<h1>Welcome</h1>
```

Feature Branch

```html
<h1>Welcome to Student Portal</h1>
```

Both changed the same line.

Git reports

```
CONFLICT
```

---

# Why Merge Conflicts Occur?

Common reasons

- Two developers edit the same file.
- Same line modified.
- One branch deletes a file while another modifies it.
- Delayed merging.

---

# Merge Conflict Diagram

```
Main

↓

index.html

↓

Welcome

──────────────

Feature

↓

index.html

↓

Welcome Student

──────────────

Merge

↓

Conflict
```

---

# 24. Resolve Merge Conflict

Suppose Git displays

```text
<<<<<<< HEAD

Welcome

=======

Welcome Student Portal

>>>>>>> feature-login
```

Choose the correct content.

Example

```html
<h1>Welcome Student Portal</h1>
```

Save file.

Stage

```bash
git add index.html
```

Commit

```bash
git commit
```

Conflict resolved.

---

# Steps to Resolve Merge Conflict

```
Git Reports Conflict

↓

Open File

↓

Choose Correct Code

↓

Save

↓

git add

↓

git commit
```

---

# Merge Strategy

Professional workflow

```
Feature Branch

↓

Development Branch

↓

Testing

↓

Pull Request

↓

Code Review

↓

Merge

↓

Production
```

Every company follows some variation of this strategy.

---

# 25. Real World DevOps Scenario

Suppose you work in a company.

Developers

```
Developer A

↓

Feature Login
```

Developer B

```
Feature Payment
```

Developer C

```
Feature Dashboard
```

Everyone works independently.

After testing

```
Pull Request

↓

Code Review

↓

Merge into develop

↓

Testing

↓

Merge into main

↓

Jenkins Pipeline

↓

Production
```

This workflow prevents unstable code from reaching production.

---

# 26. Best Practices

✅ Create one branch per feature.

---

✅ Merge frequently.

---

✅ Pull latest changes before starting work.

---

✅ Resolve conflicts immediately.

---

✅ Delete merged branches.

---

✅ Never commit directly to production.

---

# 27. Common Mistakes

❌ Working directly on

```
main
```

---

❌ Huge feature branches.

---

❌ Delayed merging.

---

❌ Ignoring merge conflicts.

---

❌ Force pushing to production branches.

---

# 28. Interview Questions

### Q1. What is a Branch?

An independent line of development.

---

### Q2. Why do we use branches?

To develop features without affecting the main project.

---

### Q3. Difference between git switch and git checkout?

`git switch`

Used mainly for switching branches.

`git checkout`

Older command.

Can switch branches and restore files.

---

### Q4. Difference between Fast Forward and Three-Way Merge?

Fast Forward

No merge commit.

Three-Way

Creates a merge commit.

---

### Q5. What is a Merge Conflict?

A conflict occurs when Git cannot automatically merge changes.

---

### Q6. How do you resolve Merge Conflicts?

- Open conflicting file
- Edit manually
- Save
- Stage
- Commit

---

### Q7. When should a feature branch be deleted?

After it has been successfully merged.

---

# 29. Summary

In this chapter you learned

- What is Branch?
- Why Branches?
- Main Branch
- Develop Branch
- Feature Branch
- Release Branch
- Hotfix Branch
- Branch Naming
- git branch
- git switch
- git checkout
- Merge
- Fast Forward Merge
- Three-Way Merge
- Merge Conflicts
- Merge Strategies

---

# 📝 Quick Revision

Create Branch

```bash
git branch feature-login
```

---

Switch Branch

```bash
git switch feature-login
```

---

Create & Switch

```bash
git switch -c feature-payment
```

---

List Branches

```bash
git branch
```

---

Rename Branch

```bash
git branch -m old new
```

---

Delete Branch

```bash
git branch -d feature-login
```

---

Force Delete

```bash
git branch -D feature-login
```

---

Merge Branch

```bash
git switch main

git merge feature-login
```

---

# 🎯 Key Takeaways

- Branches allow parallel development.
- Never work directly on the `main` branch.
- Feature branches keep production code safe.
- Merge combines changes from one branch into another.
- Fast Forward Merge occurs when history is linear.
- Three-Way Merge creates a merge commit when histories diverge.
- Merge conflicts require manual resolution.
- Small, frequently merged branches reduce conflicts and improve collaboration.

---

## 📖 Navigation

⬅ Previous:
**06-Undoing-Changes-and-Recovery.md**

➡ Next:
**08-Advanced-Branching.md**
