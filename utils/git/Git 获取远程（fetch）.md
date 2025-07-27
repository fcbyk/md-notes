`git fetch` 用于从远程仓库获取最新分支和提交信息，但不会自动合并到本地分支。

## fetch 与 pull 区别
- `fetch`：只下载，不合并。
- `pull`：下载并自动合并到当前分支。

## 常用命令
```shell
# 获取所有远程分支和提交信息
git fetch
# 获取指定远程仓库（如 origin）
git fetch <remote>
# 只获取指定远程分支
git fetch <remote> <branch>
```

## 常见场景
- 查看远程分支最新进展但不影响本地代码。
- 多人协作时，先 fetch 再手动合并，避免自动冲突。