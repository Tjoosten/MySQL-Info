MySQL Explain
=================

Despite our familiarity, SQL syntax is a dark art. The only person who understands SQL is that strange bloke with a beard and sandals who mutters to himself in the corner of your office. Everyone else uses the force and spends many frustrated hours looking aimlessly at broken SELECT queries.

MySQL provide a useful EXPLAIN command which can analyze your queries and detect potential performance issues:

- `EXPLAIN` describes how a `SELECT` will be processed including information about `JOINS`.
- `EXPLAIN EXTENDED` provides additional information and estimates the number of table rows that are filtered by the condition.

The command is simply added to the start of your query,

```sql
EXPLAIN SELECT * FROM employee_tbl;
```

The following output should be like: 

```bash 
+----+-------------+--------------+------+---------------+------+---------+------+------+-------+
| id | select_type | table        | type | possible_keys | key  | key_len | ref  | rows | Extra |
+----+-------------+--------------+------+---------------+------+---------+------+------+-------+
|  1 | SIMPLE      | empoyee_tbl  | ALL  | NULL          | NULL | NULL    | NULL |    4 |       |
+----+-------------+--------------+------+---------------+------+---------+------+------+-------+
```

Now what these columns mean?

- `id` =
