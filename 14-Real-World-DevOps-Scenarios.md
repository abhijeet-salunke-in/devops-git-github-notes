# 14. Real-World DevOps Scenarios

> 📘 Module: Real-World DevOps Scenarios
>
> 🎯 Difficulty: Intermediate to Advanced
>
> ⏱ Estimated Reading Time: 35–40 Minutes
>
> 💻 Prerequisites:
>
> - Git Basics
> - Git Branching
> - GitHub Collaboration
> - Git Workflows
> - Remote Repositories

---

# 📖 Introduction

Learning Git commands is only the first step.

In real companies,

DevOps Engineers solve problems.

This chapter covers real situations you are likely to face in production environments.

Each scenario explains

- Problem
- Solution
- Commands Used
- Best Practice

These scenarios are based on common software development and DevOps workflows.

---

# 📚 Table of Contents

1. Clone Company Repository
2. Create a New Feature
3. Working with Multiple Developers
4. Fix Wrong Commit Message
5. Forgot to Add a File
6. Undo Last Commit
7. Recover Deleted Commit
8. Resolve Merge Conflict
9. Emergency Hotfix
10. Release New Version
11. Deploy Through Jenkins
12. Production Rollback
13. Recover Lost Work
14. Accidental Push to Main
15. Real Team Workflow
16. Best Practices
17. Interview Scenarios
18. Summary

---

# Scenario 1 – Clone Company Repository

## Problem

You join a company as a DevOps Engineer.

Your manager shares the repository URL.

---

## Solution

Clone the repository.

```bash
git clone https://github.com/company/project.git
```

---

## Why?

It downloads

- Source Code
- Branches
- Commit History

Everything needed to start working.

---

# Scenario 2 – Create a New Feature

## Problem

Manager asks

> Add Login Feature.

Never work directly on

```
main
```

---

## Solution

```bash
git switch -c feature/login
```

Develop

↓

Commit

↓

Push

↓

Create Pull Request

---

# Scenario 3 – Working with Multiple Developers

Suppose

Developer A

works on

```
Login
```

Developer B

works on

```
Payment
```

Developer C

works on

```
Dashboard
```

Each developer creates

their own feature branch.

```
feature/login

feature/payment

feature/dashboard
```

No one's work affects another developer.

---

# Scenario 4 – Fix Wrong Commit Message

Problem

```
git commit -m "Final"
```

Wrong message.

---

Solution

```bash
git commit --amend -m "Add Login Authentication"
```

Latest commit message updated.

---

# Scenario 5 – Forgot to Add One File

Problem

Committed

```
Login Page
```

Forgot

```
README.md
```

---

Solution

```bash
git add README.md

git commit --amend --no-edit
```

Git updates

the previous commit.

---

# Scenario 6 – Undo Last Commit

Commit created

but not pushed.

Use

```bash
git reset --soft HEAD~1
```

Changes remain staged.

Edit

Commit again.

---

# Scenario 7 – Recover Deleted Commit

Mistakenly executed

```bash
git reset --hard HEAD~2
```

Need old commit.

---

Solution

```bash
git reflog
```

Find commit hash.

Recover

```bash
git reset --hard CommitID
```

Project restored.

---

# Scenario 8 – Resolve Merge Conflict

Developer A

updates

```
index.html
```

Developer B

also updates

```
index.html
```

Merge

↓

Conflict

---

Solution

- Open conflicting file.
- Choose correct content.
- Save.
- Stage.

```bash
git add index.html
```

Commit.

Conflict resolved.

---

# Scenario 9 – Emergency Hotfix

Production website crashes.

Never wait for

next release.

---

Workflow

```
main

↓

hotfix/payment

↓

Fix

↓

Commit

↓

Pull Request

↓

Merge

↓

Deploy
```

---

# Scenario 10 – Release New Version

Application ready.

Create Release.

```
v2.0.0
```

Tag

↓

Release Notes

↓

Deploy

Users download

stable version.

---

# Scenario 11 – Deploy Through Jenkins

Developer pushes

```
git push
```

↓

GitHub

↓

Webhook

↓

Jenkins

↓

Build

↓

Test

↓

Docker Build

↓

Kubernetes Deployment

Deployment completed automatically.

---

# Scenario 12 – Production Rollback

Deployment fails.

Need previous version.

Options

- Git Revert
- Previous Release
- Previous Docker Image

Rollback

↓

Production Restored.

---

# Scenario 13 – Recover Lost Work

Developer accidentally deletes

```
deployment.yaml
```

before committing.

If changes were committed

recover using

```
git checkout <commit> -- deployment.yaml
```

or restore the file from the appropriate commit.

If changes were never committed,

Git usually cannot recover them.

---

# Scenario 14 – Accidental Push to Main

Developer

pushes

unfinished code

to

```
main
```

Company Policy

↓

Branch Protection

↓

Push Rejected

Developer creates

Feature Branch

instead.

---

# Scenario 15 – Real Team Workflow

```
Issue

↓

Developer Assigned

↓

Feature Branch

↓

Development

↓

Commit

↓

Push

↓

Pull Request

↓

Code Review

↓

CI Pipeline

↓

Merge

↓

Deployment

↓

Release
```

Most software companies

follow a workflow very similar to this.

---

# Best Practices

✅ Create feature branches.

---

✅ Commit frequently.

---

✅ Write meaningful commit messages.

---

✅ Pull latest changes.

---

✅ Review Pull Requests.

---

✅ Protect

```
main
```

---

# Common Mistakes

❌ Working directly on

```
main
```

---

❌ Large commits.

---

❌ Ignoring merge conflicts.

---

❌ Forgetting

```
git pull
```

---

❌ Committing secrets.

---

# Interview Scenarios

### Q1

Production is broken.

Which Git command is safer?

```
git reset

or

git revert
```

Answer

```
git revert
```

because it preserves history.

---

### Q2

Forgot one file

after committing.

Answer

```
git commit --amend
```

---

### Q3

Deleted two commits.

Recover?

Answer

```
git reflog
```

---

### Q4

Need temporary storage

without committing.

Answer

```
git stash
```

---

### Q5

Need one commit

from another branch.

Answer

```
git cherry-pick
```

---

# Summary

In this chapter you learned

- Company Workflow
- Feature Development
- Team Collaboration
- Merge Conflicts
- Hotfix Workflow
- Production Rollback
- Jenkins Deployment
- Recovery
- Git Best Practices

---

# 📝 Quick Revision

Join Company

```
git clone
```

---

New Feature

```
git switch -c feature/login
```

---

Forgot File

```
git commit --amend
```

---

Recover Commit

```
git reflog
```

---

Emergency Fix

```
hotfix branch
```

---

Temporary Save

```
git stash
```

---

One Commit Only

```
git cherry-pick
```

---

# 📌 Scenario Reference

| Situation | Solution |
|-----------|----------|
| Wrong Commit Message | `git commit --amend` |
| Forgot File | `git commit --amend --no-edit` |
| Lost Commit | `git reflog` |
| Undo Commit | `git reset --soft` |
| Production Fix | Hotfix Branch |
| Temporary Work | `git stash` |
| One Commit | `git cherry-pick` |

---

# 🎯 Key Takeaways

- Most Git work in companies follows repeatable workflows rather than isolated commands.
- Protect the `main` branch and use feature branches for development.
- Use `git revert` for shared history and `git reset` carefully on local history.
- Recovery tools like `git reflog` can save work after mistakes.
- Automation through CI/CD starts with good Git practices.

---

## 📖 Navigation

⬅ Previous:
**13-DevOps-Git-Best-Practices.md**

➡ Next:
**15-Git-GitHub-Interview-Questions.md**
