
## 用户管理
```sql
-- 创建用户
CREATE USER zhang3 IDENTIFIED BY '123123';
CREATE USER 'kangshifu'@'localhost' IDENTIFIED BY '123456';

-- 修改用户名
UPDATE mysql.user SET USER='li4' WHERE USER='wang5';
FLUSH PRIVILEGES;

-- 删除用户
DROP USER li4;
DROP USER 'kangshifu'@'localhost';
```

## 密码与安全
```sql
ALTER USER 'kangshifu'@'localhost' PASSWORD EXPIRE NEVER;
ALTER USER 'kangshifu'@'localhost' PASSWORD HISTORY 5;
ALTER USER 'kangshifu'@'localhost' PASSWORD REUSE INTERVAL 365 DAY;
SET PASSWORD = '123456';
ALTER USER USER() IDENTIFIED BY '123456';
```

## 权限管理
```sql
-- 查看权限
SHOW PRIVILEGES;
SHOW GRANTS;
SHOW GRANTS FOR CURRENT_USER();
SHOW GRANTS FOR zhang3;
SHOW GRANTS FOR 'li4'@'localhost';

-- 授权
GRANT ALL PRIVILEGES ON *.* TO zhang3;
GRANT SELECT,INSERT,DELETE,UPDATE ON hntou_repair.* TO li4@localhost;
GRANT ALL PRIVILEGES ON hntou_repair.* TO zhang3;

-- 回收权限
REVOKE ALL PRIVILEGES ON hntou_repair.* FROM zhang3;
``` 