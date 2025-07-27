
## 创建数据库
```sql
CREATE DATABASE S_T;
CREATE DATABASE IF NOT EXISTS hello CHARACTER SET utf8;
```

## 切换/查看数据库
```sql
SHOW DATABASES;
USE S_T;
SELECT DATABASE();
SHOW CREATE DATABASE hello;
```

## 修改数据库
```sql
ALTER DATABASE hello CHARACTER SET gbk;
```

## 删除数据库
```sql
DROP DATABASE S_T;
DROP DATABASE IF EXISTS hello;
``` 