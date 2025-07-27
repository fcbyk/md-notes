
## 常见约束类型
- **NOT NULL**：非空约束
- **UNIQUE**：唯一约束
- **PRIMARY KEY**：主键约束
- **DEFAULT**：默认值
- **CHECK**：检查约束（MySQL 8.0+）
- **AUTO_INCREMENT**：自增
- **FOREIGN KEY**：外键约束

## 建表时添加约束
```sql
CREATE TABLE table_name (
  col1 CHAR NOT NULL,           -- 非空
  col2 INT UNIQUE KEY,          -- 唯一
  col3 INT PRIMARY KEY,         -- 主键
  col4 CHAR DEFAULT '默认值',    -- 默认值
  col5 INT CHECK (col5 > 0),    -- 检查
  col6 INT AUTO_INCREMENT       -- 自增
);

-- 复合主键、唯一、外键
CREATE TABLE table_name (
  col1 INT,
  col2 INT,
  col3 CHAR(10),
  PRIMARY KEY (col1, col2),
  UNIQUE (col3),
  FOREIGN KEY (col2) REFERENCES another_table(another_column)
);
```

## 修改表添加/删除约束
```sql
-- 添加主键、唯一
ALTER TABLE table_name ADD PRIMARY KEY (col1, col2);
ALTER TABLE table_name ADD UNIQUE (col3);
ALTER TABLE table_name ALTER col3 SET DEFAULT '默认值';

-- 删除主键、外键
ALTER TABLE table_name DROP PRIMARY KEY;
ALTER TABLE orders DROP FOREIGN KEY fk_customer_id;
```

## 查询表约束
```sql
SELECT * FROM information_schema.table_constraints
WHERE table_name = '表名称';
``` 