#### ​**​`pull`（拉取镜像）​**​

```sh
# 拉取指定标签的镜像（默认 latest）
docker pull ubuntu:22.04

# 拉取所有标签的镜像（慎用，体积大）
docker pull -a ubuntu

# 从私有仓库拉取（需先登录）
docker pull my-registry.com:5000/my-image:v1
```

#### ​**​`images`（查看镜像）​**​

```sh
# 列出所有镜像（含大小）
docker images --format "{{.ID}}\t{{.Repository}}\t{{.Size}}"

# 仅显示镜像ID（常用于批量操作）
docker images -q

# 显示摘要信息（Digest）
docker images --digests
```

#### ​**​`search`（搜索镜像）​**​

```sh
# 限制搜索结果数量
docker search --limit 3 nginx

# 过滤官方镜像且星标≥50
docker search --filter is-official=true stars=50 nginx

# 显示完整描述（避免截断）
docker search --no-trunc python
```

#### ​**​`rmi`（删除镜像）​**​

```sh
# 强制删除（即使有容器使用）
docker rmi -f ubuntu:latest

# 删除所有悬空镜像（未被任何容器引用的中间层镜像）
docker image prune

# 按条件删除（如删除 7 天前的镜像）
docker image prune -a --filter "until=168h"
```
​
#### ​**​`tag`（打标签）​**​

```sh
# 为镜像添加新标签（常用于版本管理或推送到私有仓库）
docker tag ubuntu:22.04 my-ubuntu:v1
```

#### ​**​`save` & `load`（导出/导入镜像）​**​

```sh
# 将镜像保存为压缩文件（用于离线传输）
docker save -o ubuntu.tar ubuntu:22.04

# 从文件加载镜像
docker load -i ubuntu.tar
```

#### ​**​`history`（查看镜像构建历史）​**​

```sh
# 显示镜像的构建步骤（Dockerfile 每层指令）
docker history ubuntu:22.04

# 显示完整命令（避免截断）
docker history --no-trunc ubuntu:22.04
```

#### ​**​`inspect`（查看镜像详情）​**​

```sh
# 显示镜像的完整元数据（JSON 格式）
docker inspect ubuntu:22.04

# 提取特定信息（如镜像的入口命令）
docker inspect --format='{{.Config.Entrypoint}}' ubuntu:22.04
```

#### ​**​`build`（构建镜像）​**​

```sh
# 使用当前目录的 Dockerfile 构建镜像
docker build -t my-app:v1 .

# 指定不同 Dockerfile 路径
docker build -f /path/to/Dockerfile .

# 构建时不使用缓存（强制重新执行所有步骤）
docker build --no-cache -t my-app:v2 .
```

### ​**​常用组合操作示例​**​

```sh
# 删除所有名为 `<none>` 的悬空镜像
docker rmi $(docker images -f "dangling=true" -q)

# 批量删除所有非官方镜像
docker rmi $(docker images | grep -v "OFFICIAL" | awk 'NR>1 {print $3}')

# 导出多个镜像到一个文件
docker save -o all-images.tar ubuntu:22.04 nginx:alpine
```

### ​**​注意事项​**​

1. ​**​镜像命名规范​**​：
    - 格式为 `[仓库地址/]用户名/镜像名:标签`（如 `registry.example.com/dev/nginx:v1`）。
2. ​**​空间清理​**​：
    - 定期运行 `docker system prune` 清理未使用的镜像、容器和缓存。
3. ​**​安全建议​**​：
    - 避免使用 `latest` 标签，明确指定版本（如 `python:3.9`）。