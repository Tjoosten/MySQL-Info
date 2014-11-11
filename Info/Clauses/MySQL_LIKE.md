MySQL LIKE clause. 
====================

MySQL Like clause is used to search in a table for records. To understand LIKE clause, consider an employee_tbl table, which is having the following records:

```bash
mysql> SELECT * FROM employee_tbl;
+------+------+------------+--------------------+
| id   | name | work_date  | daily_typing_pages |
+------+------+------------+--------------------+
|    1 | John | 2007-01-24 |                250 |
|    2 | Ram  | 2007-05-27 |                220 |
|    3 | Jack | 2007-05-06 |                170 |
|    3 | Jack | 2007-04-06 |                100 |
|    4 | Jill | 2007-04-06 |                220 |
|    5 | Zara | 2007-06-06 |                300 |
|    5 | Zara | 2007-02-06 |                350 |
+------+------+------------+--------------------+
7 rows in set (0.00 sec)
```

### % Wildcard

The following SQL statement selects all customers with a name starting with the letter "Z":

```bash 
mysql> SELECT * FROM employee_tbl
    -> WHERE name LIKE 'Z%';
+----+------+------------+--------------------+
| id | name | work_date  | daily_typing_pages |
+----+------+------------+--------------------+
|  6 | Zara | 2007-06-06 |                300 |
|  7 | Zara | 2007-02-06 |                350 |
+----+------+------------+--------------------+
2 rows in set (0,00 sec)
```
