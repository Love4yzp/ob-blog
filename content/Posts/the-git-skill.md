---
title: 简单 Git 入门
aliases: git
permalink: /git
date: 2024-11-03 21:19:48
tags:
  - 项目管理
---

Git 是一种非常流行的版本控制工具，广泛用于管理代码变更、记录项目进展、并支持多人协作。本文将介绍 Git 的一些基本操作，并提供学习资源，帮助大家快速上手。

### 什么是 Git？

Git 是一种分布式的版本控制系统，可以记录文件的每次更改，帮助开发者回溯项目历史。它既适合个人项目，也能支持复杂的团队协作。在 Git 的帮助下，我们可以安全地管理和分享代码变更。

### 基本 Git 操作

Git 的核心功能就是管理项目文件的版本。以下是一些常用命令，新手可以从这些基础操作开始，逐步掌握 Git 的工作流。

#### 1. `git init`：初始化仓库

当你在本地创建新项目时，可以使用 `git init` 将其变成一个 Git 仓库。`git init` 命令会在项目目录中创建一个隐藏的 `.git` 文件夹，用于存储版本控制信息。

```bash
git init
```

#### 或者：`git clone` 克隆已有仓库

如果项目已经有一个远程仓库（例如在 GitHub 上），就可以直接使用 `git clone` 命令来复制该仓库到本地，而不需要执行 `git init`。`git clone` 会下载远程仓库的所有内容和版本历史，并自动与远程仓库关联。

```bash
git clone https://github.com/your-username/your-repository.git
```

#### 2. `git add`：添加文件到暂存区

`git add` 命令会将文件更改放入暂存区，等待提交。可以添加单个文件，也可以使用 `.` 一次性添加所有文件的更改。

```bash
git add filename           # 添加单个文件
git add .                  # 添加所有更改
```

#### 3. `git commit`：提交文件到本地仓库

使用 `git commit` 将暂存区的内容提交到本地仓库，并生成唯一的提交记录。每次提交都需要配上说明，帮助理解变更内容。

```bash
git commit -m "描述本次提交的内容"   # 提交并附上描述
```

#### 4. `git branch`：管理分支

分支用于隔离不同的开发工作，`git branch` 可以查看所有分支，或创建新的分支以测试新功能。主分支通常为 `main` 或 `master`。

```bash
git branch                  # 查看所有分支
git branch new-feature      # 创建一个名为 new-feature 的新分支
```

#### 5. `git checkout`：切换分支

使用 `git checkout` 命令可以在不同分支间切换。例如，可以在主分支上开发基本功能，切换到 `new-feature` 分支进行独立开发，互不影响。

```bash
git checkout new-feature    # 切换到 new-feature 分支
git checkout -b feature2    # 创建并切换到新分支 feature2
```

#### 6. `git merge`：合并分支

当一个分支上的功能开发完成后，可以使用 `git merge` 将其合并到主分支。合并分支是协作开发中的重要步骤，确保功能最终合并到主项目中。

```bash
git checkout main           # 切换到主分支
git merge new-feature       # 将 new-feature 分支合并到 main
```

### 推荐学习资源

以下资源涵盖了图文和视频教程，适合新手从基础命令开始学习 Git 的用法。

#### 图文教程

- **[git - the simple guide - no deep shit!](https://rogerdudler.github.io/git-guide/index.zh.html)**  
  简洁明了的 Git 指南，包含核心命令和概念，特别适合入门。

- **[Git入门图文教程(1.5W字40图)🔥🔥--深入浅出、图文并茂 - 掘金](https://juejin.cn/post/7195030726096453690)**  
  详细的 Git 教程，包含丰富的图示，适合想深入了解 Git 的朋友。

#### 视频教程

- **[Git Tutorial for Beginners: Learn Git in 1 Hour - YouTube](https://www.youtube.com/watch?v=8JJ101D3knE)**  
  快速上手教程，1 小时内覆盖 Git 基础知识和常用命令。

- **[Git and GitHub for Beginners - Crash Course - YouTube](https://www.youtube.com/watch?v=RGOj5yH7evk)**  
  介绍 Git 和 GitHub 的基础用法，帮助新手快速理解 Git 工作流。

### GitHub 实操入门

Git 配合 GitHub 使用可以让代码托管和协作变得更加高效。以下是基本步骤：

#### 1. 注册 GitHub 账号

访问 [GitHub 官网](https://github.com) 注册账号。

#### 2. 创建 GitHub 仓库

在 GitHub 上创建一个新的仓库，用于托管项目代码。

#### 3. 连接本地仓库到 GitHub

在本地 Git 仓库中，使用 `git remote add origin` 命令关联 GitHub 仓库。这样就可以将本地代码推送到远程仓库：

```bash
git remote add origin https://github.com/your-username/your-repository.git
```

#### 4. `git push`：将本地提交推送到 GitHub

`git push` 命令会把本地仓库的更改推送到 GitHub，方便团队成员查看和同步代码。第一次推送时，可以使用 `-u` 参数指定默认的推送分支。

```bash
git push -u origin main    # 第一次推送，将本地 main 分支推送到 GitHub
```

此后每次提交后，只需使用 `git push` 即可同步更改。

### 总结

通过掌握 `git init`、`git clone`、`git add`、`git commit`、`git branch`、`git checkout`、`git merge` 和 `git push` 等基本命令，您可以快速上手 Git 和 GitHub，体验版本控制的强大功能和便利。希望本文的操作指南和资源能够帮你顺利入门 Git，为你的项目管理和团队协作增添助力！
