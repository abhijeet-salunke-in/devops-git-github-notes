# 12. DevOps Git Workflows

> 📘 Module: DevOps Git Workflows
>
> 🎯 Difficulty: Intermediate to Advanced
>
> ⏱ Estimated Reading Time: 35–40 Minutes
>
> 💻 Prerequisites:
>
> - Git Branches
> - Git Merge
> - GitHub Collaboration
> - Pull Requests

---

# 📖 Introduction

Knowing Git commands is only one part of being a DevOps Engineer.

The second part is understanding **how teams organize their work**.

A Git Workflow defines how developers create branches, review code, merge changes, and release software.

Different companies use different workflows depending on:

- Team Size
- Project Type
- Release Frequency
- Production Strategy

Choosing the correct workflow improves collaboration and reduces deployment problems.

---

# 📚 Table of Contents

## Part 1

1. What is a Git Workflow?
2. Why Git Workflows are Important
3. Feature Branch Workflow
4. Git Flow
5. GitHub Flow
6. Trunk-Based Development
7. Release Workflow
8. Workflow Comparison
9. Real World DevOps Scenario
10. Best Practices
11. Summary

---

# 1. What is a Git Workflow?

A Git Workflow is a predefined process that teams follow while developing software.

Instead of everyone committing directly to the main branch,

developers work through branches and code reviews.

Every company follows a workflow.

---

# Why Workflows?

Without a workflow

```
Developer A

↓

Push

↓

Main

↓

Developer B

↓

Push

↓

Main
```

Code becomes difficult to manage.

With a workflow

```
Feature Branch

↓

Review

↓

Testing

↓

Merge

↓

Deployment
```

Everything remains organized.

---

# Benefits

✔ Better Collaboration

✔ Safer Releases

✔ Easier Rollback

✔ Cleaner History

✔ Better Code Quality

---

# 2. Feature Branch Workflow

This is the simplest and one of the most popular workflows.

Every new feature gets its own branch.

Example

```
main

│

├── feature-login

├── feature-payment

└── feature-dashboard
```

Developers work independently.

Once a feature is complete,

it is merged into

```
main
```

through a Pull Request.

---

# Workflow

```
Main

↓

Create Feature Branch

↓

Develop

↓

Commit

↓

Push

↓

Pull Request

↓

Review

↓

Merge
```

---

# Advantages

✔ Easy to understand

✔ Suitable for small and medium teams

✔ Isolates features

---

# Disadvantages

❌ Long-running feature branches can cause merge conflicts.

---

# 3. Git Flow

Git Flow is a structured branching model designed for projects with planned releases.

It uses multiple long-lived branches.

```
main

↓

develop

↓

feature/*

↓

release/*

↓

hotfix/*
```

---

## Branch Purpose

### main

Production-ready code.

---

### develop

Integration branch where completed features are combined.

---

### feature/*

New features.

---

### release/*

Preparing a new release.

Only bug fixes and documentation updates are allowed.

---

### hotfix/*

Emergency fixes for production issues.

---

# Git Flow Diagram

```
main

│

├── develop

│      │

│      ├── feature/login

│      ├── feature/payment

│      └── feature/profile

│

├── release/v2.0

│

└── hotfix/payment
```

---

# Advantages

✔ Excellent for enterprise projects

✔ Supports scheduled releases

✔ Clear branch responsibilities

---

# Disadvantages

❌ More complex.

❌ Too many long-lived branches for small teams.

---

# 4. GitHub Flow

GitHub Flow is a lightweight workflow promoted by GitHub.

Only one permanent branch exists:

```
main
```

Every feature creates a short-lived branch.

Workflow

```
main

↓

feature branch

↓

Pull Request

↓

Review

↓

Merge

↓

Deploy
```

---

# Advantages

✔ Very simple

✔ Continuous Deployment

✔ Fast releases

✔ Easy collaboration

---

# Disadvantages

❌ Requires strong automated testing.

---

# Real Example

```
main

↓

feature-dark-mode

↓

Pull Request

↓

Review

↓

Merge

↓

Deploy
```

---

# 5. Trunk-Based Development

Trunk-Based Development is widely used in modern DevOps environments.

"Trunk" refers to the main development branch.

Developers keep feature branches very short-lived,

often less than one day.

```
main

│

├── feature-A

└── feature-B

↓

Merge Quickly

↓

main
```

---

# Rules

- Small commits
- Frequent merges
- Continuous Integration
- Continuous Deployment

---

# Advantages

✔ Fewer merge conflicts

✔ Faster delivery

✔ Excellent CI/CD integration

---

# Disadvantages

❌ Requires discipline.

❌ Requires strong automated testing.

---

# 6. Release Workflow

Organizations with scheduled releases often create release branches.

Example

```
develop

↓

release/v2.1

↓

Testing

↓

Bug Fixes

↓

main

↓

Release
```

During the release phase,

only critical fixes are allowed.

No new features.

---

# Why Release Branches?

Suppose

Version

```
v2.1
```

is scheduled for next week.

Developers continue building

```
v2.2
```

inside

```
develop
```

while QA tests

```
release/v2.1
```

Both activities happen simultaneously.

---

# 7. Workflow Comparison

| Workflow | Best For | Complexity |
|-----------|----------|------------|
| Feature Branch | Small Teams | Low |
| GitHub Flow | Continuous Deployment | Low |
| Git Flow | Enterprise Projects | High |
| Trunk-Based | Modern DevOps | Medium |
| Release Workflow | Planned Releases | Medium |

---

# 8. Real World DevOps Scenario

Suppose you work for an e-commerce company.

Every developer creates a feature branch.

```
feature/cart

feature/payment

feature/profile
```

After development,

a Pull Request is opened.

GitHub Actions or Jenkins runs automated tests.

If all checks pass,

the code is reviewed and merged into `main`.

The deployment pipeline automatically deploys the new version.

This workflow ensures quality, traceability, and reliable releases.

---

# 9. Best Practices

✅ Choose a workflow that matches your team size.

---

✅ Keep feature branches short-lived.

---

✅ Use Pull Requests for every merge.

---

✅ Automate testing with CI.

---

✅ Protect production branches.

---

# 10. Common Mistakes

❌ Working directly on `main`.

---

❌ Keeping feature branches open for weeks.

---

❌ Skipping code reviews.

---

❌ Releasing without testing.

---

# 11. Interview Questions

### Q1. What is a Git Workflow?

A defined process that teams follow for branching, development, review, and merging.

---

### Q2. Which workflow is most suitable for Continuous Deployment?

GitHub Flow.

---

### Q3. Which workflow is commonly used by enterprise projects?

Git Flow.

---

### Q4. Which workflow is preferred in modern DevOps?

Trunk-Based Development.

---

### Q5. Why are feature branches used?

To isolate development and prevent changes from affecting the main branch.

---

# 12. Summary

In this chapter you learned

- Git Workflows
- Feature Branch Workflow
- Git Flow
- GitHub Flow
- Trunk-Based Development
- Release Workflow
- Workflow Comparison
- DevOps Scenarios
- Best Practices

---

# 📝 Quick Revision

Feature Branch

```
Feature

↓

Pull Request

↓

Merge
```

---

GitHub Flow

```
Main

↓

Feature

↓

Merge

↓

Deploy
```

---

Git Flow

```
Main

↓

Develop

↓

Feature

↓

Release

↓

Hotfix
```

---

Trunk-Based

```
Small Branch

↓

Merge Quickly

↓

Main
```

---

# 📌 Workflow Reference

| Workflow | Used By |
|----------|---------|
| Feature Branch | Most Teams |
| GitHub Flow | SaaS Companies |
| Git Flow | Enterprise Software |
| Trunk-Based Development | Modern DevOps Teams |

---

# 🎯 Key Takeaways

- Git workflows standardize collaboration across teams.
- Feature Branch Workflow is simple and widely used.
- Git Flow is suitable for structured release cycles.
- GitHub Flow works well for continuous deployment.
- Trunk-Based Development emphasizes frequent integration and automation.
- Choosing the right workflow depends on your team's needs and release process.

---

## 📖 Navigation

⬅ Previous:
**11-Git-Hooks-and-Git-Internals.md**

➡ Next:
**13-DevOps-Git-Best-Practices.md**
