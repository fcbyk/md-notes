
## 创建存储过程
```sql
DELIMITER //
CREATE PROCEDURE avg_employee_salary ()
BEGIN
  SELECT AVG(salary) AS avg_salary FROM emps;
END //
DELIMITER ;
```

## 带参数的存储过程
```sql
DELIMITER //
CREATE PROCEDURE CountProc(IN sid INT, OUT num INT)
BEGIN
  SELECT COUNT(*) INTO num FROM fruits WHERE s_id = sid;
END //
DELIMITER ;
```

## 调用存储过程
```sql
CALL avg_employee_salary();
CALL CountProc(101, @num);
SELECT @num;
``` 