MySQL COUNT 
==============
MySQL COUNT function is the simplest function and very useful in counting the number of records, which are expected to be returned by a SELECT statement.

To understand COUNT function, consider an employee_tbl table, which is having the following records:

```sql
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
Now, suppose based on the above table you want to count total number of rows in this table, then you can do it as follows:

```sql
mysql>SELECT COUNT(*) FROM employee_tbl ;
+----------+
| COUNT(*) |
+----------+
|        7 |
+----------+
1 row in set (0.01 sec)
```
Similarly, if you want to count the number of records for Zara, then it can be done as follows:
```sql
mysql>SELECT COUNT(*) FROM employee_tbl
    -> WHERE name="Zara";
+----------+
| COUNT(*) |
+----------+
|        2 |
+----------+
1 row in set (0.04 sec)
```
