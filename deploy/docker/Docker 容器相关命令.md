
#### ​**​1. `run`（创建并启动容器）​**​

```sh
# 启动一个交互式容器（-it：分配终端）
docker run -it ubuntu:22.04 /bin/bash

# 后台运行容器并映射端口（-d：后台，-p：主机端口:容器端口）
docker run -d -p 8080:80 nginx

# 指定容器名称（--name）
docker run --name my-nginx -d nginx

# 设置环境变量（-e）
docker run -e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0

# 挂载数据卷（-v 主机路径:容器路径）
docker run -v /home/user/data:/app/data -d my-app

# 限制资源（--cpus, --memory）
docker run --cpus=2 --memory=1g -d my-app
```

#### ​**​2. `start`/`stop`/`restart`（启停容器）​**​

```sh
# 启动已停止的容器
docker start my-nginx

# 停止运行中的容器
docker stop my-nginx

# 强制停止（发送 SIGKILL）
docker kill my-nginx

# 重启容器
docker restart my-nginx
```

#### ​**​3. `rm`（删除容器）​**​

```sh
# 删除已停止的容器
docker rm my-nginx

# 强制删除运行中的容器（-f）
docker rm -f my-nginx

# 删除所有停止的容器
docker container prune
```

---

### ​**​容器状态与信息查询​**​

#### ​**​4. `ps`（查看容器列表）​**​

```sh
# 查看运行中的容器
docker ps

# 查看所有容器（包括已停止的）
docker ps -a

# 显示简洁输出（仅容器ID）
docker ps -q

# 按条件过滤（如退出状态为 0 的容器）
docker ps -a --filter "exited=0"
```

#### ​**​5. `logs`（查看容器日志）​**​

```sh
# 查看实时日志（-f：跟随输出）
docker logs -f my-nginx

# 显示最后 N 行（--tail）
docker logs --tail 100 my-nginx

# 添加时间戳（-t）
docker logs -t my-nginx
```

#### ​**​6. `inspect`（查看容器详情）​**​

```sh
# 查看容器完整配置（JSON 格式）
docker inspect my-nginx

# 提取特定信息（如 IP 地址）
docker inspect -f '{{.NetworkSettings.IPAddress}}' my-nginx
```

#### ​**​7. `stats`（实时资源监控）​**​

```sh
# 查看所有容器的 CPU/内存占用
docker stats

# 监控指定容器
docker stats my-nginx
```

---

### ​**​容器交互与操作​**​

#### ​**​8. `exec`（进入运行中的容器）​**​

```sh
# 进入容器并启动交互式终端（常用调试）
docker exec -it my-nginx /bin/bash

# 在容器内执行单条命令
docker exec my-nginx ls /app
```

#### ​**​9. `cp`（容器与主机间复制文件）​**​

```sh
# 从容器复制到主机
docker cp my-nginx:/etc/nginx/nginx.conf ./nginx.conf

# 从主机复制到容器
docker cp ./config.json my-nginx:/app/config.json
```

#### ​**​10. `commit`（将容器保存为新镜像）​**​

```sh
# 将当前容器状态保存为镜像（慎用，建议用 Dockerfile）
docker commit my-nginx my-nginx:v2
```

---

### ​**​网络与端口管理​**​

#### ​**​11. 端口映射与网络​**​

```sh
# 查看容器的端口映射
docker port my-nginx

# 创建自定义网络（推荐替代默认 bridge）
docker network create my-network

# 将容器连接到指定网络
docker run --network=my-network -d my-app
```

#### ​**​12. `top`（查看容器内进程）​**​

```sh
# 查看容器内运行的进程
docker top my-nginx
```

---

### ​**​实用组合命令示例​**​

```sh
# 批量停止所有运行中的容器
docker stop $(docker ps -q)

# 删除所有容器（危险！慎用）
docker rm -f $(docker ps -aq)

# 清理未使用的容器和镜像
docker system prune

# 导出容器文件系统到 tar 包
docker export my-nginx > nginx-container.tar
```

---

### ​**​关键注意事项​**​

1. ​**​数据持久化​**​：
    - 使用 `-v` 挂载卷（Volume）保存重要数据，避免容器删除后丢失。
2. ​**​容器 vs 镜像​**​：
    - 容器是镜像的运行实例，修改容器不会影响原始镜像（除非 `commit`）。
3. ​**​资源限制​**​：
    - 生产环境务必限制 CPU/内存（`--cpus`, `--memory`），防止单个容器耗尽资源。
4. ​**​日志管理​**​：
    - 长期运行的容器需配置日志轮转（如 `docker run --log-opt max-size=10m`）。