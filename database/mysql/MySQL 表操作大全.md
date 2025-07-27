
## 建表
```sql
CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50),
    email VARCHAR(100),
    birthdate DATE
);

CREATE TABLE tb1(
  id INT,
  a INT,
  b INT,
  c INT GENERATED ALWAYS AS (a + b) VIRTUAL
);

CREATE TABLE Student(
    Sno CHAR(9) PRIMARY KEY,
    Sname CHAR(20) UNIQUE,
    Sex CHAR(2),
    Sage SMALLINT,
    Sdep CHAR(20)
);
```

## 插入数据
```sql
INSERT INTO tb1 (id, a, b) VALUES (1, 213, 23);
INSERT INTO Student VALUES
('201215121','李明','男',20,'CS'),
('201215122','刘晨','女',19,'CS'),
('201215123','王敏','女',18,'MA'),
('201215125','张立','男',19,'IS');
INSERT INTO users (username, email, birthdate) VALUES ('user1', 'user1@example.com', '2000-01-01');
INSERT INTO users (username, email, birthdate) VALUES ('user2', 'user2@example.com', '1995-05-15');
INSERT INTO users (username, email, birthdate) VALUES ('user3', 'user3@example.com', '1988-12-31');
```

## 更新数据
```sql
UPDATE users SET username = 'new_user1', email = 'new_user1@example.com' WHERE id = 1;
```

## 删除数据
```sql
DELETE FROM users WHERE id = 1;
```

## 修改表结构
```sql
ALTER TABLE users ADD age INT;
ALTER TABLE users MODIFY age VARCHAR(3);
ALTER TABLE users CHANGE email user_email VARCHAR(50);
ALTER TABLE users DROP COLUMN user_email;
```

## 表重命名、清空、删除
```sql
SELECT * FROM users;
SHOW CREATE TABLE users;
RENAME TABLE users TO hello_users;
TRUNCATE TABLE hello_users;
DROP TABLE IF EXISTS hello_users;
``` 