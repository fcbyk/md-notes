Git 提供了一系列全局选项（以 `--` 开头的选项），这些选项可以影响 Git 命令的默认行为，适用于大多数 Git 子命令（如 `commit`、`log`、`status` 等）。以下是常用全局选项的整理和说明。

---

## 📌 常用 Git 全局选项

| 选项（短格式） | 选项（长格式）                | 用途说明                                          |
| ------- | ---------------------- | --------------------------------------------- |
| `-v`    | `--version`            | 显示 Git 版本信息（如 `git --version`）。               |
| `-h`    | `--help`               | 显示帮助信息（如 `git --help` 或 `git commit --help`）。 |
| —       | `--html-path`          | 显示 Git HTML 文档的存储路径（用于离线文档访问）。                |
| —       | `--man-path`           | 显示 Git man 手册的路径（Linux/macOS 手册页）。            |
| —       | `--info-path`          | 显示 Git info 文档的路径（GNU Info 格式文档）。             |
| —       | `--exec-path`          | **显示** Git 可执行文件的安装路径（如 `/usr/lib/git-core`）。 |
| —       | `--exec-path=<path>`   | **临时指定** Git 可执行文件路径（用于多版本切换，不影响系统默认路径）。      |
| —       | `--git-dir=<path>`     | 指定自定义 `.git` 目录路径（覆盖默认查找逻辑）。                  |
| —       | `--work-tree=<path>`   | 指定工作目录路径（覆盖当前目录）。                             |
| —       | `--no-pager`           | 禁用分页输出（直接打印全部内容，不进入 `less` 分页）。               |
| —       | `--bare`               | 以裸仓库模式操作（无工作目录，常用于服务器仓库）。                     |
| —       | `--no-replace-objects` | 禁用 Git 对象替换机制（`git replace`）。                 |
| —       | `--literal-pathspecs`  | 禁用路径通配符（`*`、`?`），按字面匹配路径。                     |
| —       | `--icase-pathspecs`    | 路径匹配时忽略大小写（如 `README.md` 和 `readme.md` 视为相同）。 |
| —       | `--no-optional-locks`  | 禁用 Git 的自动锁机制（适用于脚本或并发操作场景）。                  |

## 🚀 使用示例

### 1. **查看 Git 版本**
```bash
git --version
````

### 2. ​**​指定 Git 仓库目录和工作目录​**​

```
git --git-dir=/path/to/repo/.git --work-tree=/path/to/code status
```

### 3. ​**​禁用分页输出（适合脚本）​**​

```
git --no-pager log --oneline -n 5
```

### 4. ​**​裸仓库初始化​**​

```
git --bare init /path/to/repo.git
```

### 5. ​**​临时切换 Git 版本​**​

```
git --exec-path=/opt/git/2.40.0/bin status
```

---

## 🔍 注意事项

1. ​**​优先级规则​**​
    
    - 命令行指定的选项（如 `--git-dir`）会覆盖环境变量和配置文件。
    - 例如：`git --work-tree=/custom/path status` 会忽略当前目录的 `.git` 配置。
2. ​**​路径规范​**​
    
    - `--git-dir` 和 `--work-tree` 需使用​**​绝对路径​**​。
    - 示例：
        
 ```
git --git-dir=/home/user/project/.git --work-tree=/home/user/project status
```
        
3. ​**​脚本友好选项​**​
    
    - `--no-pager`：避免交互式分页，适合自动化脚本。
    - `--no-optional-locks`：减少并发操作时的锁冲突。
4. ​**​调试与帮助​**​
    
    - 使用 `git --help` 查看所有支持的全局选项。
    - 通过 `git --exec-path` 检查 Git 的安装位置。

---

## 📚 扩展阅读

- [Git 官方文档 - 全局选项](https://git-scm.com/docs/git#_options)
- [Git 路径规范 (Pathspec)](https://git-scm.com/docs/gitglossary#Documentation/gitglossary.txt-aiddefpathspecapathspec)

---

✅ ​**​提示​**​：全局选项通常用于临时覆盖配置，若需永久生效，建议使用 `git config` 修改配置文件。

### 文件保存建议
- 文件名：`git-global-options.md`
- 适用场景：Git 学习笔记、团队文档共享、命令行参考手册。