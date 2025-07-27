`git checkout` 用于在不同分支间切换，或恢复文件到指定状态。Git 2.23+ 推荐用 `git switch` 切换分支。

## 切换分支
```shell
# 切换到已有分支
git checkout <branch_name>
# 推荐新命令（Git 2.23+）
git switch <branch_name>
```

## 新建并切换分支
```shell
# 创建新分支并切换
git checkout -b <new_branch_name>
# 推荐新命令（Git 2.23+）
git switch -c <new_branch_name>
```

## 注意事项
- 切换分支前请提交或暂存当前更改，否则可能被阻止。
- `checkout` 也可用于恢复文件：`git checkout <branch> -- <file>`