---

# 📘 Git & GitHub – Beginner’s Guide

Welcome to the **Git & GitHub Notes**!
This file covers everything a **beginner** needs to know, from **basic concepts to practical commands**.

---

## 🔹 1. What is Git?

* **Git** is a **Distributed Version Control System (DVCS)**.
* It helps track **changes in code** and lets multiple people work on a project **simultaneously**.
* Works **locally on your computer**.
* Think of Git as a **time machine** for your code.

✅ Key Benefits:

* Save different versions of your project.
* Go back to older versions anytime.
* Create branches to experiment safely.
* Merge changes from different team members.

---

## 🔹 2. What is GitHub?

* **GitHub** is a **cloud platform** that hosts Git repositories.
* Think of it as **Google Drive for your Git projects**.
* It allows you to:

  * Store your Git repos online.
  * Share with others.
  * Collaborate with teams using Pull Requests, Issues, etc.

✅ Git = tool
✅ GitHub = place where you keep/share Git projects

---

## 🔹 3. Basic Git Workflow

Here’s how you typically use Git:

1. **Create / Clone a Repo**

   ```bash
   git init   # Start a new repository
   git clone <repo-url>   # Download existing repo from GitHub
   ```

2. **Make Changes**

   * Edit or create files in your project.

3. **Check Status**

   ```bash
   git status
   ```

4. **Stage Changes**

   ```bash
   git add filename.txt   # Stage specific file
   git add .              # Stage everything
   ```

5. **Commit Changes**

   ```bash
   git commit -m "Meaningful commit message"
   ```

6. **Push to GitHub**

   ```bash
   git push origin main
   ```

7. **Pull Latest Changes**

   ```bash
   git pull origin main
   ```

---

## 🔹 4. Tracking Files and Commits

1. Create a sample file:

   ```bash
   echo "Hello Git" > example.txt
   ```

2. Check status:

   ```bash
   git status
   ```

3. Add to staging:

   ```bash
   git add example.txt
   ```

4. Commit:

   ```bash
   git commit -m "Added example.txt"
   ```

5. View commit history:

   ```bash
   git log --oneline
   git log
   git log --author="Your Name"
   ```

---

## 🔹 5. Making Changes & Git Diff

1. Modify file:

   ```bash
   echo "This is an update" >> example.txt
   ```

2. See changes before committing:

   ```bash
   git diff
   ```

3. Stage and commit:

   ```bash
   git add example.txt
   git commit -m "Updated example.txt"
   ```

---

## 🔹 6. Branching in Git

Branches let you work on **features/bug fixes** without affecting main code.

* Create a branch:

  ```bash
  git branch feature-branch
  ```

* Switch to branch:

  ```bash
  git checkout feature-branch
  ```

  or

  ```bash
  git switch feature-branch
  ```

* Push branch to GitHub:

  ```bash
  git push -u origin feature-branch
  ```

* Merge branch back into main:

  ```bash
  git checkout main
  git merge feature-branch
  ```

* Delete branch:

  ```bash
  git branch -d feature-branch
  ```

---

## 🔹 7. Connecting Git to GitHub

1. Create a repo on GitHub.

2. Link local repo to GitHub:

   ```bash
   git remote add origin https://github.com/username/repo.git
   ```

3. Push code:

   ```bash
   git push -u origin main
   ```

4. Verify remote:

   ```bash
   git remote -v
   ```

---

## 🔹 8. Cloning, Pulling & Pushing

* Clone a repo:

  ```bash
  git clone https://github.com/username/repo.git
  ```

* Pull latest changes:

  ```bash
  git pull origin main
  ```

* Push your changes:

  ```bash
  git push origin main
  ```

---

## 🔹 9. Authentication with GitHub

Since GitHub removed password authentication, you need a **Personal Access Token (PAT).**

* Generate PAT from GitHub → Settings → Developer Settings → Tokens.
* Use it instead of password when pushing.

Example:

```bash
git remote set-url origin https://<username>@github.com/<username>/<repo>.git
```

---

## 🔹 10. Useful Git Commands at a Glance

| Command                 | Purpose           |
| ----------------------- | ----------------- |
| `git init`              | Initialize repo   |
| `git clone <url>`       | Clone remote repo |
| `git status`            | Show changes      |
| `git add <file>`        | Stage file        |
| `git commit -m "msg"`   | Commit changes    |
| `git log`               | Show history      |
| `git branch`            | List branches     |
| `git checkout <branch>` | Switch branch     |
| `git merge <branch>`    | Merge branches    |
| `git push`              | Upload changes    |
| `git pull`              | Download changes  |

---

## 🔹 11. Git vs GitHub (Quick Comparison)

| Feature           | Git                         | GitHub              |
| ----------------- | --------------------------- | ------------------- |
| What it is        | Version Control Tool        | Hosting Platform    |
| Works             | Locally on computer         | Online (cloud)      |
| Internet Required | ❌ No                        | ✅ Yes               |
| Purpose           | Track changes               | Share & collaborate |
| Example           | Save versions of your files | Upload & share repo |

---

## 🚀 Summary

* **Git** = Tool to track your project history locally.
* **GitHub** = Online platform to store and collaborate on Git projects.
* Together, they make teamwork in coding projects smooth and efficient.

---

