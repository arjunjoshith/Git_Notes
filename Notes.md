Git_Notes:

What are Git and GitHub?

Git : A tool that tracks changes in your code.

Think of it like:
A time machine for your code
You can save snapshots and go back anytime
Undo button for programming

What it does:
Saves different versions of your project
Lets you experiment without breaking things
Works on your computer (offline)


GitHub : A website to store your Git projects online.

Think of it like:
Google Drive for code
Social media for programmers
Online backup for your projects

What it does:
Backs up your code in the cloud
Share code with others
Collaborate with teams
Show off your projects

Verify installation:

git --version

##Local Setup (On your Laptop)
Open your terminal (VS Code terminal is best) inside your project folder and run these commands one by one.

**Introduce yourself to Git (One-time setup)
-Git needs to know who is making these changes.

git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"



## Starting from Scratch

mkdir my-project

**What it does:** Creates a new folder called "my-project"
- `mkdir` = "make directory" (directory = folder)
- Like right-clicking and creating a new folder

cd my-project

**What it does:** Goes inside that folder
- `cd` = "change directory"
- You need to be inside the folder to work with it

git init

**What it does:** Turns this folder into a Git repository
- Creates a hidden `.git` folder that tracks all changes
- Now Git is watching this folder for changes
- Use this when starting a NEW project from scratch



## Downloading an Existing Project

git clone https://github.com/username/repository.git

**What it does:** Downloads a copy of a project from GitHub to your computer
- `clone` = make a complete copy
- Downloads all files AND the entire history
- Creates a new folder automatically with the project name

cd repository

**What it does:** Goes inside the downloaded folder
- The folder name is usually the repository name
- Now you can start working on the files

When you use `git clone`, it **automatically creates a new folder** and downloads files into it, but you're still **outside** that folder.

**Think of it like this:**
# You are here: /home/yourname/

git clone https://github.com/facebook/react.git

# Git creates: /home/yourname/react/
# But you're STILL in: /home/yourname/

cd react

# NOW you're in: /home/yourname/react/

## Visual Example

Before clone:
📁 My Computer
  📁 Documents  ← You are here
 
After clone:
📁 My Computer
  📁 Documents  ← You are still here
    📁 react    ← Files downloaded here (but you're not inside yet)
 
After cd react:
📁 My Computer
  📁 Documents
    📁 react    ← NOW you are here



echo "# My First Project" > README.md

Breaking it down:
echo = print/display text
"# My First Project" = the text content
> = redirect/save the output into a file
README.md = the file name

What it does: Creates a new file called README.md and puts the text "# My First Project" inside it.
Alternative ways to create a file:

Open any text editor (Notepad, VS Code, etc.)
Create a new file called README.md
Type whatever you want
Save it in your project folder

The echo command is just a quick way to create a file from the command line.

git status

**What it does:** Shows you what has changed
- Which files are new/modified/deleted
- Which files are staged (ready to commit)
- Which files are not tracked by Git yet

git branch -M main

Parts:
git branch = branch command
-M = Move/rename (force)
main = new name for the branch

Why git branch -M main?
When you do git init, Git creates a default branch automatically:

Older Git versions: Creates branch called master
Newer Git versions: Creates branch called main

The problem: You don't know which one you have!
GitHub always expects main, so this command makes sure your branch is called main.

What if you skip this?
If your branch is called master and you try git push -u origin main
It will fail because the names don't match
You'd have to push to master instead, which GitHub doesn't expect

Simple rule: Always run this to be safe and match GitHub's default.

git push -u origin main

Breaking it down:
git push = upload your code
-u = set upstream (remember this connection for future)
origin = nickname for your GitHub repository URL
main = the branch name you're pushing

What it does:
Uploads your code to GitHub
Sets up a connection so next time you can just type git push

git remote -v

Breaking it down:
git remote = manage remote repositories (GitHub, etc.)
-v = verbose (show more details)

What it does: Shows you where your code will be pushed to/pulled from.
example output:

git remote -v

**You'll see something like:**

origin  https://github.com/username/my-project.git (fetch)
origin  https://github.com/username/my-project.git (push)

## Understanding the Output

origin  https://github.com/username/my-project.git (fetch)
origin  https://github.com/username/my-project.git (push)

git commit -m "Your message"

What it does: Saves your changes with a description
Breaking it down:
git commit = save a snapshot of your code
-m = message
"Your message" = description of what you changed

git push -f origin main

What it does: Forcefully uploads your code to GitHub (DANGEROUS!)
Breaking it down:
git push = upload code to GitHub
-f = force (ignore conflicts, overwrite everything)
origin = nickname for your GitHub repository
main = branch name
⚠️ WARNING: This is DANGEROUS!

git remote remove origin

What It Does
Disconnects your local project from GitHub

Breaking It Down
git remote remove origin
\- `git remote` = manage connections to online repositories
\- `remove` = delete/disconnect
\- `origin` = the nickname for your GitHub repository URL

\## Before vs After
\### Before:
Your Computer ←──connected──→ GitHub
(via "origin")
You can `git push` and `git pull`

\### After:
Your Computer     GitHub
(disconnected)

Create a New Branch:

git checkout -b feature-name

Switch Between Branches:
git checkout main
git checkout feature-name

See Your Branches:
git branch

See Commit History:
git log --oneline


Fix wrong remote URL:
git remote -v
\# Oh no! Wrong URL!


git remote set-url origin https://correct-url.git

git remote -v    # Verify it's fixed


View your configuration:

git config --list

Purpose:
It displays all Git configuration settings currently applied to your environment.
In plain terms:
It shows who you are in Git, how Git behaves, and where those settings come from.
What kind of information it shows
Typical output looks like this:

user.name=Joshith
user.email=joshith@gmail.com
core.editor=code
core.autocrlf=true
init.defaultBranch=main
remote.origin.url=https://github.com/username/repo.git

git branch -d bad-branch

What It Does:
Deletes a branch safely
Example:
bash# See all branches
git branch
# Output:
#   main
# * feature-login
#   old-feature

# Delete old branch you don't need
git branch -d old-feature
# Output: Deleted branch old-feature

# Check again
git branch
# Output:
#   main
# * feature-login
# (old-feature is gone!)

Safe Delete (-d) vs Force Delete (-D)
-d (lowercase) = Safe delete
git branch -d feature
# ✅ Works if: branch is merged
# ❌ Fails if: branch has unmerged work (protects you!)
-D (uppercase) = Force delete
git branch -D feature
# ✅ Always works (deletes everything!)
# ⚠️ Dangerous: Loses unmerged work

touch file.txt

What it does:
Creates an empty file
Does not open any editor

Example:
touch app.py
touch README.md


ls — what it is:

Command:

ls

Meaning:
ls stands for list.

Use:
It displays files and folders in the current directory.

In simple terms:
“Show me what is inside this folder.”


If the GIT folder is EMPTY (most likely)
Command (Windows / Git Bash / Linux / macOS):

rmdir GIT


This deletes the folder only if it is empty.

If the GIT folder has files or subfolders
Command (force delete):

rm -r GIT

-r = recursive (delete everything inside)

If it asks for confirmation:

rm -rf GIT

-f = force (no questions)

⚠ Be careful: This permanently deletes the folder.

Simple Decision Tree
Question: Whose repository do you want to push to?

Answer 1: "The same repository I cloned from"
git clone https://github.com/username/repository.git
cd repository
\# make changes
git add .
git commit -m "My changes"
git push  # (You need permission!)

Answer 2: "My own new repository"
git clone https://github.com/username/repository.git
cd repository
git remote remove origin
git remote add origin https://github.com/YOUR-USERNAME/your-new-repo.git
\# make changes
git add .
git commit -m "My changes"
git push -u origin main

Answer 3: "I want to fork it properly"
\# 1. Fork on GitHub first (click Fork button)
\# 2. Clone YOUR fork
git clone https://github.com/YOUR-USERNAME/repository.git
cd repository
\# make changes
git add .
git commit -m "My changes"
git push



Complete Fork Workflow
Step-by-step example:
On GitHub Website:
Go to someone's repository: https://github.com/facebook/react
Click the "Fork" button (top-right corner)
GitHub creates: https://github.com/YOUR-USERNAME/react
On Your Computer:
\# Clone YOUR fork (not the original!)
git clone https://github.com/YOUR-USERNAME/react.git
cd react
\# Make changes
\# Edit some files...
\# Save changes
git add .
git commit -m "Fixed a typo"
\# Push to YOUR fork
git push
\# ✅ Success! Your fork now has your changes
\# ❌ Original facebook/react is unchanged

\### When to Fork?
\- You want to contribute to open-source projects
\- You don't have permission to push to the original repo
\- You want to experiment without affecting the original
\- You want your own version of a project

\*\*Example scenarios:\*\*

\*\*Scenario 1: Contributing to React\*\*
1.	Fork facebook/react
2. Clone your fork
3. Fix a bug
4. Push to your fork
5. Create "Pull Request" to suggest your fix to Facebook
6. If they like it, they merge it into the original!

\*\*Scenario 2: Using a template\*\*
1.	Find a website template on GitHub
2. Fork it
3. Clone your fork
4. Customize it for your needs
5. You now have your own version!


> vs >>:
Symbol	Meaning    Example		  Result
>	Overwrite  echo "Hi" > file.txt   File contains only "Hi"
>>	Append	   echo "Bye" >> file.txt Adds "Bye" to end

cat Command:
Command			Purpose
cat file.txt		Show file contents
cat file1.txt file2.txt Show multiple files
cat file.txt > new.txt  Copy file

Why Called "cat"?
Original purpose: Concatenate (join) multiple files

cat file1.txt file2.txt > combined.txt
# Joins file1 and file2 into combined.txt
But mostly used to just view files!

less file.txt

How It Works
Let me show you step by step!

What is less?
A file viewer that lets you scroll through large files
Think of it like opening a book - you can flip pages, search, and read comfortably.

Navigation Keys:
Key			Action
Arrow Down or j 	Move down one line
Arrow Up or k		Move up one line
Space or Page Down	Move down one page
b or Page Up		Move up one page
g			Go to beginning of file
G (Shift+g)		Go to end of file
q			QUIT (exit less)

cat file.txt       # Show entire file
head file.txt      # Show first 10 lines
tail file.txt      # Show last 10 lines
less file.txt      # View file (scroll with arrows, press 'q' to quit)

## Simple .gitignore (Put This in Every Project)

Create `.gitignore` file:

node_modules/
.env
.DS_Store
*.log

Multiple Remotes:

You can have multiple remotes with different names!
# Original project
git remote add upstream https://github.com/original/project.git
# Your fork
git remote add origin https://github.com/yourusername/project.git
# Check all remotes
git remote -v
Output:
origin    https://github.com/yourusername/project.git (fetch)
origin    https://github.com/yourusername/project.git (push)
upstream  https://github.com/original/project.git (fetch)
upstream  https://github.com/original/project.git (push)
Then you can:
git pull upstream main    # Pull from original
git push origin main      # Push to your fork






## Cheat Sheets:

# Daily Commands
git pull                    # Start of day
git status                  # Check changes
git add .                   # Stage files
git commit -m "message"     # Save
git push                    # Upload

# Branching
git checkout -b new-branch  # Create branch
git checkout main           # Switch to main
git branch                  # List branches

# Fixing Mistakes
git reset --soft HEAD~1     # Undo last commit
git stash                   # Save changes temporarily
git stash pop               # Get changes back

# Info
git log --oneline           # See history
git remote -v               # See GitHub URL


Essential Git commands (non-negotiable):
git init            # Initialize repository
git status          # Check file status
git add .           # Stage changes
git commit -m "msg" # Save snapshot
git branch          # List branches
git checkout -b dev # Create \& switch branch
git merge dev       # Merge branch
git remote add origin URL
git push origin main
git pull origin main



## Daily Commands (Memorize These 6)

git pull                    # Start of day - get latest code
git status                  # Check what changed
git add .                   # Stage all changes
git commit -m "message"     # Save changes
git push                    # Upload to GitHub
git checkout -b branch-name # Create new branch

**That's 90% of your work!**

## Setup (One-Time)

git config --global user.name "Your Name"
git config --global user.email "your.email@gmail.com"

## Starting Work

### New Project:

mkdir project
cd project
git init
# Create files...
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/project.git
git push -u origin main

### Existing Project:

git clone https://github.com/username/project.git
cd project

## Daily Workflow

git pull                         # Morning: Get latest
git checkout -b feature-name     # Create branch
# Make changes...
git add .
git commit -m "Added feature"
git push -u origin feature-name
# Create Pull Request on GitHub

## Important Rules

1. Always `git pull` before starting
2. Always work on branches, never on `main`
3. Never use `git push -f` (force)
4. Commit often with clear messages

## Fixing Mistakes

git reset --soft HEAD~1  # Undo last commit (keep changes)
git stash                # Save changes temporarily
git stash pop            # Restore saved changes

## Quick Info

git status        # See current state
git log --oneline # See commit history
git branch        # See branches
git remote -v     # See GitHub URL


Useful pager controls (remember these):
While inside the pager:
q → quit (exit)
Enter → next line
Space → next page
b → previous page
/text → search for text



## Most Common Mistakes (And Fixes)

### Made Changes on Wrong Branch
# Don't panic! Stash your changes:
git stash
git checkout correct-branch
git stash pop

### Need to Undo Last Commit
git reset --soft HEAD~1  # Undo but keep changes

### Working on a Task:
# Create branch for your task
git checkout -b fix-login-bug
# Save your work
git add .
git commit -m "Fixed login validation"
git push -u origin fix-login-bug

### On GitHub:
- Create **Pull Request** (ask team to review your code)
- Wait for approval
- They'll merge it to main

### After Merge:
git checkout main
git pull  # Get the merged code
git branch -d fix-login-bug  # Delete your old branch

### Next task:
git checkout -b add-new-feature
# Repeat...






# Git Stash Explained

**`git stash` = Temporarily save your work without committing**

Think of it like putting your work in a drawer - you can take it out later!

---

## Why Use Stash?

### Scenario:
```
You're coding a feature (half-done, not ready to commit)
Boss: "Emergency! Switch to main and fix a bug NOW!"
Problem: Can't switch branches with uncommitted changes
Solution: Stash your work!
```

---

## 1. `git stash` - Save Your Work

### What It Does:
**Saves your changes and cleans your working directory**

### Example:

```bash
# You're working on a feature
echo "New feature code" >> feature.txt
git status
# Output: modified: feature.txt (RED)

# Emergency! Need to switch branches
# But can't switch with uncommitted changes

# Stash your work
git stash

# Now check status
git status
# Output: nothing to commit, working tree clean ✅

# Your changes are SAVED but HIDDEN
# You can now switch branches!
git checkout main
```

---

### What Happened to Your Changes?

```
Before stash:
Working Directory: feature.txt (modified)

After stash:
Working Directory: feature.txt (clean, original version)
Stash Storage: Your changes saved here 📦
```

---

## 2. `git stash pop` - Get Your Work Back (and Delete Stash)

### What It Does:
**Restores your changes AND removes them from stash**

### Example:

```bash
# You stashed your work earlier
git stash
# Switch and do other work...
git checkout main
# Fix bug, commit, push...

# Now go back to your feature
git checkout feature-branch

# Get your stashed work back
git stash pop

# Check status
git status
# Output: modified: feature.txt (RED)
# Your changes are BACK! ✅

# Check stash list
git stash list
# Output: (empty)
# Stash is GONE after pop
```

---

### Visual Flow:

```
1. Working → git stash → Stash Storage 📦
2. Do other work...
3. git stash pop → Stash Storage 📦 → Working (stash deleted)
```

---

## 3. `git stash apply` - Get Your Work Back (Keep Stash)

### What It Does:
**Restores your changes BUT keeps them in stash**

### Example:

```bash
# Stash your work
echo "Important code" >> important.txt
git stash

# Later, apply it
git stash apply

# Check status
git status
# Output: modified: important.txt (RED)
# Changes are back! ✅

# Check stash list
git stash list
# Output: stash@{0}: WIP on main: abc1234 Your message
# Stash is STILL THERE! 📦
```

---

## Difference: `pop` vs `apply`

### `git stash pop`
```bash
git stash pop
# ✅ Restores changes
# ❌ Deletes stash
# Use when: You only need it once
```

### `git stash apply`
```bash
git stash apply
# ✅ Restores changes
# ✅ Keeps stash
# Use when: You might need it again
```

---

## Complete Real-World Example

### Scenario: Emergency Bug Fix

```bash
# 1. You're coding a feature
git checkout -b add-login
echo "Login code line 1" >> login.js
echo "Login code line 2" >> login.js
git status
# Output: modified: login.js (RED)

# 2. URGENT! Boss needs bug fix NOW
# Can't commit (code is incomplete)

# 3. Stash your work
git stash save "Login feature in progress"
# Output: Saved working directory and index state

git status
# Output: nothing to commit, working tree clean

# 4. Switch to main and fix bug
git checkout main
echo "Bug fix" >> bugfix.js
git add bugfix.js
git commit -m "Fixed critical bug"
git push

# 5. Back to your feature
git checkout add-login

# 6. Restore your work
git stash pop

# 7. Continue coding
git status
# Output: modified: login.js (RED)
echo "Login code line 3" >> login.js

# 8. Now commit your completed feature
git add login.js
git commit -m "Added login feature"
git push
```

---

## Multiple Stashes

### You Can Stash Multiple Times:

```bash
# Stash 1
echo "Feature A" >> fileA.txt
git stash save "Feature A work"

# Stash 2
echo "Feature B" >> fileB.txt
git stash save "Feature B work"

# Stash 3
echo "Feature C" >> fileC.txt
git stash save "Feature C work"

# List all stashes
git stash list
# Output:
# stash@{0}: On main: Feature C work
# stash@{1}: On main: Feature B work
# stash@{2}: On main: Feature A work
```

---

### Apply Specific Stash:

```bash
# Apply the second stash
git stash apply stash@{1}

# Pop the first stash
git stash pop stash@{0}
```

---

## Useful Stash Commands

### View Stash Contents
```bash
# List all stashes
git stash list

# See what's in latest stash
git stash show

# See detailed changes
git stash show -p
```

### Delete Stash
```bash
# Delete latest stash
git stash drop

# Delete specific stash
git stash drop stash@{1}

# Delete ALL stashes
git stash clear
```

### Stash with Message
```bash
git stash save "Work in progress on login feature"
```

---

## Common Scenarios

### Scenario 1: Wrong Branch

```bash
# Oops! Coding on wrong branch
git checkout main  # Should be on feature branch!
echo "Code" >> file.txt

# Quick fix:
git stash
git checkout -b correct-branch
git stash pop
# Continue working ✅
```

---

### Scenario 2: Need to Pull

```bash
# You have uncommitted changes
git pull
# Error: Your local changes would be overwritten

# Solution:
git stash
git pull
git stash pop
```

---

### Scenario 3: Experimenting

```bash
# Try something risky
echo "Experimental code" >> test.txt
git stash  # Save it

# Try different approach
echo "Better code" >> test.txt
git add test.txt
git commit -m "Better solution"

# Want to compare? Apply old attempt
git stash apply
# Now you have both versions to compare
```

---

## Visual Summary

```
Your Changes
     ↓
git stash → 📦 Stash Storage
     ↓
Working Directory: Clean ✅
     ↓
Do other work (switch branches, pull, etc.)
     ↓
git stash pop → 📦 Stash → Your Changes (stash deleted)
     OR
git stash apply → 📦 Stash → Your Changes (stash kept)
```

## Quick Reference

| Command 	    | What It Does 	| Stash After? |
|-------------------|-------------------|--------------|
| `git stash` 	    | Save changes      | Kept 	       |
| `git stash pop`   | Restore + Delete  | Deleted      |
| `git stash apply` | Restore + Keep    | Kept 	       |
| `git stash list`  | Show all stashes  | - 	       |
| `git stash drop`  | Delete stash      | Deleted      |
| `git stash clear` | Delete all stashes| All deleted  |


git log --oneline --all --graph

What It Does:
Shows pretty visual history of all commits

Breaking It Down:
git log --oneline --all --graph
        ↑         ↑     ↑
        |         |     └── Show as visual tree
        |         └──────── Show all branches
        └────────────────── One line per commit

Without Flags (Basic):
git log
```

**Output:**
```
commit a1b2c3d4e5f6g7h8i9j0 (long hash)
Author: Your Name <email@example.com>
Date:   Mon Dec 15 10:30:00 2024

    Added login feature
    
commit 9f8e7d6c5b4a3g2h1i0j (another long hash)
Author: Your Name <email@example.com>
Date:   Mon Dec 15 09:00:00 2024

    Initial commit
Too much info! Hard to read!

With --oneline (Compact):
git log --oneline
```

**Output:**
```
a1b2c3d Added login feature
9f8e7d6 Initial commit
Much better! ✅

With --all (All Branches):
git log --oneline --all
```

**Output:**
```
d4e5f6g (feature-b) Added feature B
c3d4e5f (feature-a) Added feature A
a1b2c3d (main) Added login
9f8e7d6 Initial commit
Shows commits from ALL branches!

With --graph (Visual Tree):
git log --oneline --all --graph
```

**Output:**
```
* d4e5f6g (feature-b) Added feature B
| * c3d4e5f (feature-a) Added feature A
|/
* a1b2c3d (HEAD -> main) Added login
* 9f8e7d6 Initial commit
Visual branches! ✅

Real Example:
bash# Create some history
git init
echo "v1" > file.txt
git add file.txt
git commit -m "Version 1"

echo "v2" >> file.txt
git add file.txt
git commit -m "Version 2"

git checkout -b feature
echo "feature" >> file.txt
git add file.txt
git commit -m "Added feature"

git checkout main
echo "v3" >> file.txt
git add file.txt
git commit -m "Version 3"

# Now view history
git log --oneline --all --graph
```

**Output:**
```
* e5f6g7h (HEAD -> main) Version 3
| * d4e5f6g (feature) Added feature
|/
* c3d4e5f Version 2
* a1b2c3d Version 1
Beautiful! You can see:

* = commits
| = branch lines
HEAD -> main = where you are now
Branch names in parentheses


git branch --set-upstream-to=origin/main main

What It Does:
Links your local branch to GitHub branch for easy push/pull

The Problem:
bash# You created branch locally
git checkout -b feature

# Try to push
git push
# Error: no upstream branch

The Solution:
git branch --set-upstream-to=origin/main main
                              ↑            ↑
                              |            └── Local branch
                              └─────────────── Remote branch

Simpler Way:
bash# Instead of that long command, just use:
git push -u origin main
            ↑
            └── -u sets upstream automatically!

Example:
bash# Create local branch
git checkout -b new-feature

# First push (set upstream)
git push -u origin new-feature
# Now link is created! ✅

# Future pushes (easy!)
git push  # Works automatically!
git pull  # Works automatically!

When You Need This:
Scenario 1: Clone then create branch
git clone <url>
git checkout -b feature
git push  # Error!
git push -u origin feature  # Fix! ✅
Scenario 2: Local branch needs tracking
git branch --set-upstream-to=origin/main main
# Now git push/pull work without specifying branch

git restore <file>

What It Does:
Undoes changes to a file (goes back to last commit)
⚠️ WARNING: This DELETES your changes permanently!

Example:
bash# You have a file
echo "Original content" > file.txt
git add file.txt
git commit -m "Added file"

# You edit it
echo "New changes" >> file.txt

# Check what changed
cat file.txt
# Output:
# Original content
# New changes

# Oops! I don't want these changes
git restore file.txt

# Check again
cat file.txt
# Output:
# Original content
# (New changes are GONE forever!)
```

---

### Before Restore:
```
Last Commit:     "Original content"
Working File:    "Original content" + "New changes"
```

### After Restore:
```
Last Commit:     "Original content"
Working File:    "Original content" ✅
                 ("New changes" deleted!)

Common Use:
bash# Made a mistake while coding
echo "Bad code" >> script.js
git status
# modified: script.js

# Undo it
git restore script.js
# Back to last committed version! ✅

Restore Specific File vs All Files:
bash# Restore one file
git restore file.txt

# Restore all files
git restore .
# ⚠️ All uncommitted changes deleted!

git reset --soft HEAD~1

What It Does:
Undoes last commit BUT keeps your changes

Breaking It Down:
git reset --soft HEAD~1
          ↑      ↑    ↑
          |      |    └── Go back 1 commit
          |      └─────── Current commit
          └────────────── Keep changes staged

Example:
bash# Make commits
echo "Version 1" > file.txt
git add file.txt
git commit -m "Commit 1"

echo "Version 2" >> file.txt
git add file.txt
git commit -m "Commit 2"

echo "Version 3" >> file.txt
git add file.txt
git commit -m "Commit 3"  # Oops! Wrong commit message!

# Undo last commit
git reset --soft HEAD~1

# Check status
git status
# Output: modified: file.txt (GREEN - still staged!)

# Check file
cat file.txt
# Output:
# Version 1
# Version 2
# Version 3
# (Content is STILL THERE!)

# Commit again with correct message
git commit -m "Commit 3 - Correct message"
```

---

### Visual:

**Before:**
```
Commits: A → B → C (HEAD here)
File content: "v1 v2 v3"
```

**After `git reset --soft HEAD~1`:**
```
Commits: A → B (HEAD moved back)
Staged changes: "v3" (ready to commit again)
File content: "v1 v2 v3" (unchanged!)

Different Reset Types:
--soft (Keep everything)
git reset --soft HEAD~1
# ✅ Undo commit
# ✅ Keep changes staged (GREEN)
# ✅ File unchanged
--mixed (Default - unstage)
git reset HEAD~1
# OR
git reset --mixed HEAD~1
# ✅ Undo commit
# ⚠️ Changes unstaged (RED)
# ✅ File unchanged
--hard (Delete everything!)
git reset --hard HEAD~1
# ✅ Undo commit
# ❌ Changes DELETED
# ❌ File reverts to previous version
# ⚠️ DANGEROUS!

HEAD1, HEAD2, HEAD~3
git reset --soft HEAD~1  # Undo 1 commit
git reset --soft HEAD~2  # Undo 2 commits
git reset --soft HEAD~3  # Undo 3 commits
```

**Visual:**
```
Commits: A → B → C → D → E (HEAD)
                    ↑
HEAD~1 = D
HEAD~2 = C
HEAD~3 = B

Real Use Cases:
Use Case 1: Wrong commit message
git commit -m "Fixed bug"  # Oops! Typo!
git reset --soft HEAD~1
git commit -m "Fixed bug in login"  # Correct! ✅
Use Case 2: Forgot to add file
git commit -m "Added feature"
# Oh no! Forgot to add config.js

git reset --soft HEAD~1
git add config.js
git commit -m "Added feature"  # Now includes config.js ✅
Use Case 3: Split one commit into multiple
bash# One big commit with many changes
git reset --soft HEAD~1
# Now changes are staged

# Commit separately
git add file1.txt
git commit -m "Added file1"

git add file2.txt
git commit -m "Added file2"