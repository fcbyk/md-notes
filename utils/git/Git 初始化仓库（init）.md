`git init` 用于初始化一个新的 Git 仓库。

## 仓库类型
- **普通仓库**：包含工作区和 .git 目录，适合日常开发。
- **裸仓库**：只有版本数据，没有工作区，常用于远程服务器。

## 初始化命令
```shell
# 在当前目录初始化仓库
git init
# 在指定目录初始化仓库
git init <directory>
# 创建裸仓库
git init --bare
# 指定模板目录
git init --template=/path/to/template-directory
# 静默模式
git init --quiet
# 指定初始分支名
git init --initial-branch=main
```

## 初始化后建议
- 配置用户名邮箱：`git config --global user.name`、`git config --global user.email`
- 建议立即添加 `.gitignore` 文件
- 可用 `git status` 查看仓库状态