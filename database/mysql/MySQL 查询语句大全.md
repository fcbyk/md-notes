
## 建表与插入示例
```sql
CREATE DATABASE IF NOT EXISTS student_db;
USE select_db;
CREATE TABLE IF NOT EXISTS stu (
    id INT AUTO_INCREMENT PRIMARY KEY,
    sname VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    math DECIMAL(5,2) DEFAULT NULL, 
    english DECIMAL(5,2) DEFAULT NULL, 
    sex ENUM('M', 'F') DEFAULT 'M'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO stu (sname, age, math, english, sex) VALUES
('张三', 19, 85.5, 90.0, 'M'),
('李四', 21, 78.0, 88.5, 'F'),
('王五', 22, 92.0, 75.0, 'M'),
('赵六', 20, 67.5, 80.0, 'F'),
('周七', 23, 88.0, 82.5, 'M');
```

## 基本查询
```sql
SELECT * FROM stu;
SELECT sname, age FROM stu;
SELECT sname, math AS 数学成绩, english AS 英文成绩 FROM stu;
```

## 条件查询
```sql
SELECT * FROM stu WHERE age > 20;
SELECT * FROM stu WHERE age >= 20 AND age <= 30;
SELECT * FROM stu WHERE hire_date BETWEEN '1998-09-01' AND '1999-09-01';
SELECT * FROM stu WHERE age = 18 OR age = 20 OR age = 22;
SELECT * FROM stu WHERE age IN (18, 20, 22);
SELECT * FROM stu WHERE english IS NULL;
SELECT * FROM stu WHERE english IS NOT NULL;
SELECT * FROM stu WHERE sname LIKE '马%';
SELECT * FROM stu WHERE sname LIKE '%德%';
```

## 排序
```sql
SELECT * FROM stu ORDER BY age;
SELECT * FROM stu ORDER BY math DESC;
SELECT * FROM stu ORDER BY math DESC, english ASC;
```

## 聚合函数
```sql
SELECT COUNT(id) FROM stu;
SELECT MAX(math) FROM stu;
SELECT MIN(math) FROM stu;
```

## 分组与分组条件
```sql
SELECT sex, AVG(math) FROM stu GROUP BY sex;
SELECT sex, AVG(math), COUNT(*) FROM stu GROUP BY sex;
SELECT sex, AVG(math), COUNT(*) FROM stu WHERE math > 70 GROUP BY sex HAVING COUNT(*) > 2;
```

## 分页
```sql
SELECT * FROM stu LIMIT 0, 3;
SELECT * FROM stu LIMIT 1, 3;
``` 