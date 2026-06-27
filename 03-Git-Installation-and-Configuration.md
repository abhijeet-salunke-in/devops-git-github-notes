# 03. Git Installation and Configuration

# 📖 Introduction

Before using Git, it must be installed and configured correctly. Configuration is the first thing every developer or DevOps engineer performs before creating or cloning repositories.

Git configuration tells Git who you are by storing your **username** and **email address**. Every commit you make will contain this information.

Without proper configuration, Git cannot correctly identify the author of a commit.

---

# 📚 Table of Contents

1. Why Install Git?
2. Installing Git
3. Verify Git Installation
4. What is Git Configuration?
5. Types of Git Configuration
6. Configure Username
7. Configure Email
8. View Git Configuration
9. Configuration Files
10. Global vs Local Configuration
11. Real World Scenario *(Part 2)*
12. Best Practices *(Part 2)*
13. Common Mistakes *(Part 2)*
14. Interview Questions *(Part 2)*
15. Summary *(Part 2)*

---

# 1. Why Install Git?

Git is not available by default on every operating system.

Before using commands like:

```bash
git init
git clone
git add
git commit
```

Git must be installed.

Without installation:

```
$ git status

git: command not found
```

---

# 2. Installing Git

## Linux (RHEL / CentOS)

```bash
sudo dnf install git -y
```

or

```bash
sudo yum install git -y
```

### Command Breakdown

```
sudo
```

Runs the command with administrator privileges.

```
dnf
```

Package manager for RHEL 8/9.

```
yum
```

Package manager for older CentOS/RHEL versions.

```
install
```

Installs the package.

```
git
```

Package name.

```
-y
```

Automatically answers **Yes** to installation prompts.

---

## Ubuntu / Debian

```bash
sudo apt update

sudo apt install git -y
```

---

## Windows

1. Download Git from

https://git-scm.com/

2. Run Installer

3. Keep default options

4. Finish Installation

---

# 3. Verify Git Installation

After installation,

check whether Git is installed correctly.

Command

```bash
git --version
```

Example Output

```bash
git version 2.47.1
```

Meaning

- Git is installed.
- Installed version is **2.47.1**.

---

## Why verify?

Imagine Jenkins server.

You install Git.

Before configuring Jenkins,

always verify installation.

This prevents pipeline failures.

---

# 4. What is Git Configuration?

Git configuration stores your identity.

Every commit contains

```
Author Name

Author Email
```

Example

```
commit e32a9a1

Author: Abhijeet Salunke <abhijeet@gmail.com>

Date:

Commit Message
```

Git gets this information from configuration.

---

# Why Configuration is Needed?

Imagine

Developer A

Developer B

Developer C

all work on one project.

Git must know

Who created each commit?

Without configuration,

Git cannot identify the author correctly.

---

# 5. Types of Git Configuration

Git has three configuration levels.

```
System

↓

Global

↓

Local
```

Priority

```
Local

↓

Global

↓

System
```

Local overrides Global.

Global overrides System.

---

## System Configuration

Applies to

Every user

on the operating system.

Usually managed by

System Administrator.

Command

```bash
git config --system
```

Not commonly used by developers.

---

## Global Configuration

Applies to

Current user.

Every repository you create will use it.

Example

```
Abhijeet

↓

All Git Repositories
```

Command

```bash
git config --global
```

---

## Local Configuration

Applies only to

One repository.

Example

```
GitHub Notes

↓

Different Email

↓

Other repositories remain unchanged.
```

Command

```bash
git config --local
```

---

# Configuration Hierarchy

```
Repository

↓

Local Config

↓

Global Config

↓

System Config
```

Git always checks

Local first.

If not found,

checks Global.

If still not found,

checks System.

---

# 6. Configure Username

Command

```bash
git config --global user.name "Abhijeet Salunke"
```

### Command Breakdown

```
git
```

Git program.

```
config
```

Configuration command.

```
--global
```

Store configuration for current user.

```
user.name
```

Username field.

```
"Abhijeet Salunke"
```

Actual username.

---

### Verify Username

```bash
git config --global user.name
```

Output

```
Abhijeet Salunke
```

---

# 7. Configure Email

Command

```bash
git config --global user.email "your@email.com"
```

Example

```bash
git config --global user.email "abhijeetsalunke@gmail.com"
```

---

Verify

```bash
git config --global user.email
```

Output

```
abhijeetsalunke@gmail.com
```

---

## Why Email Matters?

GitHub identifies your commits using your email.

If the email matches your GitHub account,

your profile shows

```
Verified Commit

✔
```

Otherwise,

GitHub may not associate the commit with your account.

---

# 8. View Git Configuration

Display all configuration

```bash
git config --list
```

Example Output

```text
user.name=Abhijeet Salunke

user.email=abhijeetsalunke@gmail.com

core.editor=vim

core.autocrlf=input
```

---

Display Username Only

```bash
git config user.name
```

---

Display Email Only

```bash
git config user.email
```

---

Display Global Configuration

```bash
git config --global --list
```

---

Display Local Configuration

```bash
git config --local --list
```

---

# 9. Configuration Files

Git stores configuration in files.

### System

```
/etc/gitconfig
```

---

### Global

```
~/.gitconfig
```

or

```
~/.config/git/config
```

---

### Local

```
project/

.git/

config
```

Every repository has its own

```
.git/config
```

file.

---

# 10. Global vs Local Configuration

| Global | Local |
|---------|--------|
| Current User | Single Repository |
| Shared across all repositories | Only one repository |
| Most commonly used | Used for special cases |
| Stored in ~/.gitconfig | Stored in .git/config |

---

# Example

Suppose

Your Personal GitHub

uses

```
abhijeetsalunke@gmail.com
```

But your company gives

```
abhijeet@company.com
```

You don't want every repository to use the company email.

So,

Global

```
abhijeetsalunke@gmail.com
```

Company Repository

```
git config user.email "abhijeet@company.com"
```

Only that repository changes.

This is the power of Local Configuration.

---

# 11. First-Time Git Setup

Whenever Git is installed on a new computer or server, the first step is to configure Git.

## Step 1: Verify Git Installation

```bash
git --version
```

Example Output

```bash
git version 2.47.1
```

---

## Step 2: Configure Username

```bash
git config --global user.name "Abhijeet Salunke"
```

---

## Step 3: Configure Email

```bash
git config --global user.email "abhijeetsalunke@gmail.com"
```

---

## Step 4: Verify Configuration

```bash
git config --list
```

Example Output

```text
user.name=Abhijeet Salunke
user.email=abhijeetsalunke@gmail.com
```

---

## Step 5: Ready to Use Git

Now Git is ready.

You can create repositories, clone projects, commit code, and push changes to GitHub.

---

# 12. Real World DevOps Scenario

Imagine you join a new company as a DevOps Engineer.

On your first day, you receive a new Linux server.

Your manager asks you to clone the company's Infrastructure repository.

Before doing anything, you must configure Git.

Workflow

```
Install Git

↓

Verify Installation

↓

Configure Username

↓

Configure Email

↓

Clone Repository

↓

Start Working
```

If Git is not configured,

your commits may appear as

```
Unknown Author
```

or

```
root@localhost
```

which is considered bad practice.

---

## Company Example

Personal Laptop

```
Username

Abhijeet Salunke

Email

abhijeetsalunke@gmail.com
```

Company Repository

```
Username

Abhijeet Salunke

Email

abhijeet@company.com
```

Use Local Configuration

```bash
git config user.email "abhijeet@company.com"
```

Only that repository changes.

---

# 13. Best Practices

## ✔ Configure Git Immediately

Always configure Git after installation.

---

## ✔ Use Your Real Name

Good

```bash
git config --global user.name "Abhijeet Salunke"
```

Bad

```bash
git config --global user.name "Admin"
```

---

## ✔ Use the Same Email as GitHub

This links commits to your GitHub profile.

---

## ✔ Use Local Configuration for Company Projects

Never overwrite your personal Git configuration unless necessary.

---

## ✔ Verify Configuration

Before starting work

```bash
git config --list
```

---

## ✔ Keep Git Updated

Update Git regularly to receive:

- Bug fixes
- Performance improvements
- Security updates

---

# 14. Common Mistakes

## ❌ Forgetting to Configure Git

Result

```
Author Unknown
```

---

## ❌ Typing Wrong Email

GitHub cannot verify your commits.

---

## ❌ Using Company Email in Personal Projects

Keep personal and company identities separate.

---

## ❌ Editing Configuration Files Manually

Use

```bash
git config
```

instead.

---

## ❌ Forgetting --global

Example

```bash
git config user.name "Abhijeet"
```

This changes only the current repository.

Many beginners expect it to apply everywhere.

---

# 15. Frequently Used Configuration Commands

## Configure Username

```bash
git config --global user.name "Abhijeet Salunke"
```

---

## Configure Email

```bash
git config --global user.email "abhijeetsalunke@gmail.com"
```

---

## View All Configuration

```bash
git config --list
```

---

## View Username

```bash
git config user.name
```

---

## View Email

```bash
git config user.email
```

---

## Remove Username

```bash
git config --global --unset user.name
```

---

## Remove Email

```bash
git config --global --unset user.email
```

---

## Open Configuration Editor

```bash
git config --global --edit
```

---

# 16. Interview Questions

### Q1. Why do we configure Git before using it?

**Answer:**

Git needs your username and email to identify the author of every commit.

---

### Q2. Difference between Global and Local Configuration?

| Global | Local |
|---------|--------|
| All repositories | One repository only |
| ~/.gitconfig | .git/config |

---

### Q3. How do you verify Git installation?

```bash
git --version
```

---

### Q4. How do you display all Git configurations?

```bash
git config --list
```

---

### Q5. Which configuration has the highest priority?

Answer

```
Local

↓

Global

↓

System
```

---

### Q6. Which command changes the username for only one repository?

```bash
git config user.name "New Name"
```

(No `--global` option)

---

# 17. Summary

In this chapter, you learned:

- Installing Git
- Verifying Installation
- Configuring Username
- Configuring Email
- Git Configuration Levels
- Global vs Local Configuration
- Configuration Files
- Viewing Git Configuration
- First-Time Git Setup
- DevOps Configuration Workflow
- Best Practices
- Common Mistakes

---

# 📝 Quick Revision

### Install Git

```bash
sudo dnf install git -y
```

---

### Verify Installation

```bash
git --version
```

---

### Configure Username

```bash
git config --global user.name "Abhijeet Salunke"
```

---

### Configure Email

```bash
git config --global user.email "abhijeetsalunke@gmail.com"
```

---

### View Configuration

```bash
git config --list
```

---

### Configuration Priority

```
Local

↓

Global

↓

System
```

---

# 🎯 Key Takeaways

- Git must be installed before use.
- Every commit records the author's username and email.
- Configure Git immediately after installation.
- Use **Global Configuration** for personal development.
- Use **Local Configuration** when a specific repository requires different settings (for example, a company email).
- Always verify your configuration before creating commits.

---

# 🚀 What's Next?

In the next chapter, you'll learn the complete Git workflow, including:

- Working Directory
- Staging Area
- Local Repository
- `git init`
- `git clone`
- `git status`
- `git add`
- File Tracking
- Complete Git Lifecycle

These concepts form the foundation of everyday Git usage.
