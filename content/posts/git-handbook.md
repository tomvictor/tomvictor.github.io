---
title: "Git Handbook for power users"
date: "2025-06-05"
# description: "Refresh C Programming"
tags: ["git"]
categories: ["posts"]
aliases: ["git"]
# ShowToc: true
# TocOpen: true
ShowBreadCrumbs: true
draft: false
---

I’ve documented a collection of useful Git commands that I use in my work. Feel free to contribute your suggestions by creating a PR on github.

**Change the commit message of last commit**

Use this when you want to edit the message of your most recent commit without creating a new one.

```bash
git commit --amend
```

**Squash commit branch B to branch A**

This merges changes from branch-B into branch-A as a single commit, which helps keep the commit history clean.

```bash
# Run this in branch A
git merge --squash branch-B
```

**Combine multiple commits to one commit**

Use interactive rebase to squash multiple recent commits into one. Great for tidying up commit history before pushing.

```bash
git rebase -i HEAD~3

You’ll see something like this in your text editor:

pick 123abc Commit message 1
pick 456def Commit message 2
pick 789ghi Commit message 3

Change the second and third pick to squash (or just s):

pick 123abc Commit message 1
squash 456def Commit message 2
squash 789ghi Commit message 3
```

**Force push to remote(For diverged branch)**

Force pushing is useful when your local branch history differs from the remote, such as after a rebase or amend.

```bash
git push --force
```

**Git pretty logs**

View a concise and clean list of the latest 10 commits in your repository.

```bash
git log -10 --pretty=oneline
```
