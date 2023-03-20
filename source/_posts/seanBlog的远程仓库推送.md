---
title: seanBlog的远程仓库推送
author: icesoda
date: 2022-12-19 16:09:09
categories:
- [icesodaMall]
description:
---

#### github

- create a new repository on the command line

  ```
  echo "# seanblog" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin git@github.com:icesoda105/seanblog.git
  git push -u origin main
  ```

- ### push an existing repository from the command line

  ```
  git remote add origin git@github.com:icesoda105/seanblog.git
  git branch -M main
  git push -u origin main
  ```

