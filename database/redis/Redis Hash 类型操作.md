
Hash 类型是 Redis 中用于存储对象的结构，适合存储字段-值（field-value）对。

## 常用命令
```shell
# 设置和获取单个字段
hset myhash field1 "Hello"
hget myhash field1

# 批量设置和获取
hmset myhash field1 "Hello" field2 "World"
hmget myhash field1 field2

# 获取字段数量
hlen myhash
``` 