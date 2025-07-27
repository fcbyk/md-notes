分支是 Git 最核心的功能之一，用于并行开发、功能隔离和版本管理。合理使用分支可以让团队协作和个人开发更加高效。

## 基本概念
- **分支（branch）**：代码开发的独立线索，主分支通常为 `main` 或 `master`。
- **本地分支**：只存在于本地仓库。
- **远程分支**：远程仓库的分支快照，需同步更新。

## 查看分支
列出本地和远程分支，当前分支前有 `*` 标记。
```shell
# 查看本地分支
git branch
# 查看所有分支（本地+远程）
git branch -a
git branch --all
# 仅查看远程分支
git branch -r
git branch --remotes
```

## 重命名分支
```shell
# 重命名本地分支
git branch -m <old-branch-name> <new-branch-name>
git branch --move <old-branch-name> <new-branch-name>
# 重命名当前分支
git branch -m <new-branch-name>
git branch --move <new-branch-name>
# 强制重命名（覆盖同名分支）
git branch -M <old-branch-name> <new-branch-name>
git branch -M <new-branch-name>
```

## 删除分支
```shell
# 删除本地分支（安全，未合并会警告）
git branch -d <branch-name>
# 强制删除本地分支（未合并也会删除）
git branch -D <branch-name>
```

## 常见问题
- 删除分支前请确保重要内容已合并。
- 分支命名建议简洁明了，如 `feature/xxx`、`bugfix/xxx`。