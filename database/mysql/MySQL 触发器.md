## 触发器简介
- 触发器是与表相关的数据库对象，在表的 INSERT、UPDATE 或 DELETE 操作时自动执行。

## 创建触发器
```sql
DELIMITER //
CREATE TRIGGER before_insert
BEFORE INSERT ON test_trigger
FOR EACH ROW
BEGIN
  INSERT INTO test_trigger_log (t_log) VALUES('before_insert');
END //
DELIMITER ;
```

## 触发器示例：薪资检查
```sql
DELIMITER //
CREATE TRIGGER salary_check_trigger
BEFORE INSERT ON employees FOR EACH ROW
BEGIN
  DECLARE mgrsalary DOUBLE;
  SELECT salary INTO mgrsalary FROM employees WHERE employee_id = NEW.manager_id;
  IF NEW.salary > mgrsalary THEN
    SIGNAL SQLSTATE 'HY000' SET MESSAGE_TEXT = '薪资高于领导薪资错误';
  END IF;
END //
DELIMITER ;
```

## 触发器管理
```sql
SHOW TRIGGERS;
SHOW CREATE TRIGGER 触发器名;
SELECT * FROM information_schema.TRIGGERS;
DROP TRIGGER IF EXISTS 触发器名称;
``` 