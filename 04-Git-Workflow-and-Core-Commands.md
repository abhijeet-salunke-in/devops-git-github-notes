# 04. Git Workflow and Core Commands

> 📘 Module: Git Workflow & Core Commands
>
> 🎯 Difficulty: Beginner
>
> ⏱ Estimated Reading Time: 20–25 Minutes
>
> 💻 Prerequisites:
>
> - Git Installed
> - Git Configured
> - Basic Linux Commands

---

# 📖 Introduction

Git is not just a collection of commands.

It follows a workflow that every developer and DevOps engineer uses every day.

Before learning commands like `git add`, `git commit`, or `git push`, you must understand **how Git works internally**.

Once you understand the workflow, Git commands become very easy to remember.

This chapter explains the complete Git lifecycle from creating a repository to storing your changes.

---

# 📚 Table of Contents

1. What is Git Workflow?
2. Why Git Workflow is Important?
3. Git Three Areas
   - Working Directory
   - Staging Area
   - Local Repository
4. Complete Git Lifecycle
5. Git Workflow Diagram
6. What is a Repository?
7. Creating Repository (`git init`)
8. Cloning Repository (`git clone`)
9. Difference between `git init` and `git clone`
10. Repository Structure
11. Real World DevOps Scenario
12. Best Practices

---

# 1. What is Git Workflow?

Git Workflow is the **sequence of steps** followed while managing source code using Git.

Every change follows the same journey.

```
Create File

↓

Modify File

↓

Stage File

↓

Commit File

↓

Push to GitHub
```

Every developer in the world follows this workflow.

---

# Why Learn Git Workflow?

Without understanding the workflow,

Git commands look random.

With workflow knowledge,

every command has a purpose.

For example,

You now know

```
git add
```

moves files to the Staging Area,

while

```
git commit
```

stores those staged changes permanently in the local repository.

---

# 2. Why Git Workflow is Important?

Git workflow helps developers

- Track changes
- Organize commits
- Work safely
- Collaborate with teams
- Deploy applications

Imagine editing a production application directly.

One mistake could crash the application.

Instead,

Git workflow allows changes to be reviewed before deployment.

---

# 3. Git Three Areas

This is the **most important concept in Git.**

Git stores your work in three stages.

```
Working Directory

↓

Staging Area

↓

Local Repository
```

Almost every Git command works with one of these areas.

Understanding these three areas is the key to mastering Git.

---

# Working Directory

The Working Directory is your project folder.

Example

```
Website/

index.html

style.css

about.html

contact.html
```

This is where you create or modify files.

Git does **not** automatically save changes made here.

---

## Example

You create

```
login.html
```

It exists only inside the Working Directory.

Git has not yet recorded it.

---

# Staging Area

The Staging Area acts like a **waiting room**.

Files placed here are prepared for the next commit.

Command used

```bash
git add
```

Example

```
Working Directory

↓

git add

↓

Staging Area
```

Only staged files will be committed.

---

## Why Staging Exists?

Imagine modifying

```
index.html

style.css

README.md
```

Today,

only

```
index.html
```

is complete.

You stage only that file.

```bash
git add index.html
```

Tomorrow,

you stage the remaining files.

This gives you complete control over commits.

---

# Local Repository

After staging,

you permanently save changes using

```bash
git commit
```

Now changes move into the Local Repository.

```
Working Directory

↓

Staging Area

↓

git commit

↓

Local Repository
```

Local Repository stores

- Commit History
- Branches
- Tags
- Git Objects

---

# Relationship Between Three Areas

```
            git add

Working Directory ------------>

                    Staging Area

                           |

                           |

                    git commit

                           |

                           V

                  Local Repository
```

Every Git project follows this process.

---

# 4. Complete Git Lifecycle

Below is the complete lifecycle of a Git project.

```
Create Project

↓

git init

↓

Create Files

↓

git status

↓

git add

↓

git commit

↓

git push

↓

GitHub Repository
```

This lifecycle repeats every day.

---

# Example Lifecycle

Suppose you build an E-commerce Website.

Day 1

```
mkdir Ecommerce

cd Ecommerce

git init
```

Create

```
index.html
```

Check status

```
git status
```

Stage

```
git add index.html
```

Commit

```
git commit -m "Initial homepage"
```

Push

```
git push
```

Project is now saved.

---

# 5. Git Workflow Diagram

```
Create File

↓

Modify File

↓

git status

↓

git add

↓

Staging Area

↓

git commit

↓

Local Repository

↓

git push

↓

GitHub
```

---

# 6. What is a Repository?

A Repository (Repo) is a storage location that contains

- Source Code
- Commit History
- Branches
- Tags
- Git Configuration

Think of it as the project's database.

---

## Types of Repository

### Local Repository

Stored on your computer.

Example

```
/home/abhijeet/project
```

---

### Remote Repository

Stored on GitHub.

Example

```
https://github.com/abhijeet/project
```

---

# 7. Creating Repository

Command

```bash
git init
```

Meaning

Initialize a new Git repository.

---

## Syntax

```bash
git init
```

---

## Example

```bash
mkdir Student-Inquiry-System

cd Student-Inquiry-System

git init
```

Output

```
Initialized empty Git repository
```

Now,

Git creates

```
.git
```

inside the project.

---

# What Happens Internally?

```
Student-Inquiry-System/

↓

git init

↓

Student-Inquiry-System/

.git/

index.html

style.css
```

The hidden

```
.git
```

directory stores all Git information.

---

# Why Use git init?

Use `git init` when

- Starting a brand-new project
- Existing folder is not tracked by Git
- Creating personal projects

---

# 8. Cloning Repository

Instead of creating a repository,

sometimes we download an existing one.

Command

```bash
git clone
```

---

## Syntax

```bash
git clone <repository-url>
```

---

## Example

```bash
git clone https://github.com/abhijeet-salunke-in/devops-git-github-notes.git
```

Git downloads

- Source Code
- Commit History
- Branches
- Tags

Everything.

---

# What Happens Internally?

```
GitHub

↓

git clone

↓

Your Computer
```

Now you have a complete copy.

---

# Why Use git clone?

Used when

- Joining a company
- Working with a team
- Downloading Open Source Projects
- Continuing existing work

---

# 9. Difference Between git init and git clone

| git init | git clone |
|-----------|------------|
| Creates new repository | Downloads existing repository |
| Empty Git history | Complete Git history |
| Used for new projects | Used for existing projects |
| Creates .git folder | Downloads .git folder |
| No remote configured | Remote (origin) configured automatically |

---

# 10. Repository Structure

A Git project usually looks like

```
Student-Inquiry-System/

│

├── .git/

├── README.md

├── .gitignore

├── index.html

├── style.css

├── images/

└── scripts/
```

The most important directory is

```
.git
```

Never delete it unless you intentionally want to remove Git tracking.

---

# 11. Real World DevOps Scenario

Imagine you join a company on your first day.

Your manager says:

> "Clone our Infrastructure repository and start working."

You run:

```bash
git clone https://github.com/company/infrastructure.git
```

Now your laptop contains the exact same repository as the company server.

You don't create a new repository with `git init`; you **clone** the existing one because you need its full history and collaboration setup.

---

# 12. Best Practices

- Always initialize Git before starting a new project.
- Use `git clone` instead of downloading ZIP files when contributing.
- Never delete the `.git` directory accidentally.
- Understand the three Git areas before learning advanced commands.
- Keep your repository organized with a `README.md` and `.gitignore`.


---

# 13. Checking Repository Status

After creating or cloning a repository, the first command you should use is:

```bash
git status
```

## What is `git status`?

`git status` displays the current state of your Git repository.

It tells you:

- Current branch
- Files that are tracked
- Files that are untracked
- Modified files
- Staged files
- Whether your working tree is clean

It **does not modify anything**. It only displays information.

---

## Syntax

```bash
git status
```

---

## Example

Suppose your project contains:

```
Student-Inquiry-System/

index.html

style.css
```

After creating a new file

```
about.html
```

Run

```bash
git status
```

Output

```text
On branch main

Untracked files:

about.html

nothing added to commit
```

Git informs you that the file exists but is not yet being tracked.

---

# Why is git status Important?

It prevents accidental mistakes.

Before every commit, developers usually run

```bash
git status
```

to verify what will be committed.

This is one of the most frequently used Git commands.

---

# 14. File States in Git

Every file inside Git belongs to one of four states.

```
Untracked

↓

Tracked

↓

Modified

↓

Staged

↓

Committed
```

Understanding these states makes Git much easier.

---

## Untracked Files

An untracked file is a file that Git has never seen before.

Example

```
contact.html
```

Git does not include it in commits until you explicitly add it.

Example

```bash
git status
```

```
Untracked files:

contact.html
```

---

## Tracked Files

Tracked files are files Git already knows about.

Example

```
index.html
```

Once committed,

Git continues monitoring it.

---

## Modified Files

Suppose

```
index.html
```

already exists.

You change one line.

Now

```bash
git status
```

shows

```
Modified:

index.html
```

Git knows the file changed.

---

## Staged Files

After

```bash
git add index.html
```

Git moves the file to the staging area.

Now

```bash
git status
```

shows

```
Changes to be committed
```

This means Git is ready to commit it.

---

# File State Diagram

```
Create File

↓

Untracked

↓

git add

↓

Staged

↓

git commit

↓

Tracked

↓

Modify

↓

Modified

↓

git add

↓

Staged

↓

git commit

↓

Tracked
```

---

# 15. git add

## What is git add?

The `git add` command moves changes from the **Working Directory** to the **Staging Area**.

Think of it as telling Git:

> "I want these changes to be included in my next commit."

---

## Syntax

```bash
git add <file>
```

---

# Add Single File

Example

```bash
git add index.html
```

Only

```
index.html
```

moves to the staging area.

---

# Add Multiple Files

Example

```bash
git add index.html style.css about.html
```

All three files become staged.

---

# Add Entire Directory

```bash
git add images/
```

Every file inside

```
images/
```

becomes staged.

---

# Add Everything

```bash
git add .
```

Stages every modified and new file in the current directory.

Example

```
index.html

style.css

README.md

images/
```

All become staged.

---

# Difference

```
git add index.html
```

Stages only one file.

---

```
git add .
```

Stages everything.

---

# Why Does Git Have a Staging Area?

This is one of Git's best features.

Imagine you changed

```
index.html

style.css

README.md
```

Only

```
index.html
```

is complete.

You don't want to commit unfinished CSS.

So you run

```bash
git add index.html
```

Then

```bash
git commit -m "Updated homepage"
```

Tomorrow

```bash
git add style.css README.md
```

New commit.

This creates clean and meaningful commit history.

---

# 16. Daily Git Workflow

A developer's daily work usually looks like this.

```
git pull

↓

Modify Files

↓

git status

↓

git add

↓

git commit

↓

git push
```

This workflow repeats every day.

---

# Example

Morning

```bash
git pull
```

Receive latest code.

---

Modify

```
index.html

style.css
```

---

Check

```bash
git status
```

---

Stage

```bash
git add .
```

---

Commit

```bash
git commit -m "Updated homepage design"
```

---

Push

```bash
git push
```

Done.

---

# 17. Real World DevOps Scenario

Suppose you maintain a Kubernetes deployment repository.

Morning

```bash
git pull
```

Receive latest YAML files.

You modify

```
deployment.yaml
```

Check

```bash
git status
```

Stage

```bash
git add deployment.yaml
```

Commit

```bash
git commit -m "Increase nginx replicas to 5"
```

Push

```bash
git push
```

Jenkins detects the push.

Pipeline starts automatically.

Docker image builds.

Kubernetes deploys the latest version.

---

# 18. Best Practices

✅ Run

```bash
git status
```

before every commit.

---

✅ Stage only required files.

---

✅ Write meaningful commit messages.

---

✅ Keep commits small.

---

✅ Commit frequently.

---

# 19. Common Mistakes

❌ Using

```bash
git add .
```

without checking modified files.

---

❌ Forgetting

```bash
git status
```

before committing.

---

❌ Committing unfinished code.

---

❌ Mixing unrelated changes in one commit.

---

# 20. Interview Questions

### Q1. What are the three Git areas?

Answer

- Working Directory
- Staging Area
- Local Repository

---

### Q2. What does `git status` do?

Displays the current state of the repository.

---

### Q3. What is the purpose of the staging area?

It allows developers to choose exactly which changes will be included in the next commit.

---

### Q4. Difference between Tracked and Untracked files?

Tracked files are already managed by Git.

Untracked files are new files Git has never seen.

---

### Q5. Difference between

```bash
git add .
```

and

```bash
git add file.txt
```

`git add .`

Stages everything.

`git add file.txt`

Stages only one file.

---

# 21. Summary

In this chapter you learned

- Git Workflow
- Git Three Areas
- Working Directory
- Staging Area
- Local Repository
- Git Lifecycle
- Repository Creation
- git init
- git clone
- git status
- File States
- git add
- Daily Workflow
- Best Practices

---

# 📝 Quick Revision

Repository

```
git init
```

Clone

```
git clone
```

Check Status

```
git status
```

Stage One File

```
git add index.html
```

Stage All Files

```
git add .
```

Commit

```
git commit -m "message"
```

Push

```
git push
```

---

# 🎯 Key Takeaways

- Every Git change follows the same workflow:
  **Working Directory → Staging Area → Local Repository → Remote Repository.**
- `git status` is the safest command to run before staging or committing.
- The staging area gives you precise control over what goes into a commit.
- Small, focused commits make collaboration and troubleshooting much easier.
- Understanding the workflow is more important than memorizing commands.

---

## 📖 Navigation

⬅ Previous:
**03-Git-Installation-and-Configuration.md**

➡ Next:
**05-Working-with-Commits-and-History.md**
