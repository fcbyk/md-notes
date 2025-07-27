String 是 Redis 最基本的数据类型，支持单值存储、批量操作、过期等。

## 常用命令
```shell
# 设置、获取、删除
set hello 123456
get hello
del hello

# 批量操作
mset key1 value1 key2 value2
mget key1 key2

# 其他
setnx hello 22323   # 仅当key不存在时设置
setex mykey 60 redis # 设置带过期时间的key
``` 