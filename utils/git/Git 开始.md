## Git 是什么？
- 分布式版本控制系统（DVCS）
- 核心目标：高效管理代码历史记录
- 关键特性：
  - 本地完整仓库
  - 非线性开发（分支/合并）
  - 数据完整性（SHA-1哈希）

## 核心概念
- **仓库（Repository）**
  - 本地仓库 vs 远程仓库
- **三区结构**
  - 工作区 → 暂存区 → 版本库
- **提交（Commit）**
  - 快照（非差异）
  - 父子引用
- **分支（Branch）**
  - 轻量级指针
  - 默认`main/master`
- **HEAD指针**
  - 当前工作位置标记

## 基础工作流
1. 初始化：`git init` / `git clone`
2. 修改文件 → `git add` → `git commit`
3. 同步远程：`git pull` ↔ `git push`
4. 分支操作：`git branch` / `git checkout` / `git merge`

## 常用命令速查表

| 命令             | 说明        | 详细笔记                   |
| -------------- | --------- | ---------------------- |
| `git init`     | 初始化本地仓库   | [[Git 初始化仓库（init）]]    |
| `git clone`    | 克隆远程仓库    |                        |
| `git status`   | 查看当前状态    |                        |
| `git add`      | 添加文件到暂存区  |                        |
| `git commit`   | 提交更改      |                        |
| `git branch`   | 分支管理      | [[Git 分支管理（branch）]]   |
| `git checkout` | 分支切换/文件恢复 | [[Git 分支切换（checkout）]] |
| `git switch`   | 推荐的分支切换命令 | [[Git 分支切换（checkout）]] |
| `git merge`    | 合并分支      |                        |
| `git fetch`    | 获取远程分支    | [[Git 获取远程（fetch）]]    |
| `git pull`     | 拉取并合并远程分支 | [[Git 获取远程（fetch）]]    |
| `git push`     | 推送到远程仓库   |                        |
| `git log`      | 查看提交历史    |                        |
| `git reflog`   | 查看操作历史    |                        |
| `git remote`   | 远程仓库管理    |                        |
| `git config`   | 配置用户信息    |                        |
| `git help`     | 查看帮助文档    | [[Git 全局选项]]           |

> 更多全局选项和命令详解见 [[Git 全局选项]]

## 关键优势
- 离线工作能力
- 分支操作高效
- 数据不可篡改
- 灵活的工作流支持（Git Flow, GitHub Flow等）

## 扩展体系
- 托管平台：GitHub/GitLab/Gitee
- 图形化工具：GitKraken/SourceTree
- CI/CD集成

## 学习路线
- 基础命令 → 分支管理 → 冲突解决 → 高级操作（rebase/stash等）