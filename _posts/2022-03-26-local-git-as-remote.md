---
title: "Use local git as remote repository"
date: 2022-03-26
categories:
  - git
classes: wide
excerpt: This blog describes about using local git as remote repository.
---

While working in local network sometimes we need to work multiple people in same repository. But without remote git like Github we need to set it for our local usage. Here is the simple step by step to clone, push, pull local repository. 

## Clone
```bash
git clone username@ip:repo_path
example:
git clone sagor@172.16.16.152:/media/sagor/myrepo
# provide sagor password to clone
```

## Pushing new branch
```bash
git branch hello
git checkout hello
# do your work and commit then
git push origin hello
# provide sagor password to push
```

## Pulling updates
```bash
git pull origin branch_name
example:
git pull origin dev
# provide sagor pass to pull
```