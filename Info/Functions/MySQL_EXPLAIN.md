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

#### Column explanation

| **Column**      | **Description**                   |
| --------------- | --------------------------------- |
| `id`            | The `SELECT` Identifier           |
| `select_type`   | The `SELECT` type                 |
| `table`         | The table for the output row      |
| `type`          | The `JOIN` type                   |
| `possible_keys` | The possible indexes to choose    |
| `key`           | The index actually chosen         |
| `key_len`       | The length of the chosen key      |
| `ref`           | The columns compared to the index |
| `rows`          | Estimate of rows to be examined   |
| `Extrea`        | Additional information            |

#### Log into a `.txt` file.
You can also log the output of the query to a textfile. Using this syntax. 

```bash 
mysql -u [dbuser] -p[dbpass] -e "[query]" > out.txt
```

- `[dbuser]` is the database user’s name
- `[dbpass]` is the password of the database. (there is no space between the -p and the password)
- `[query]`  is the SQL statement, e.g. `USE mydatabase; EXPLAIN SELECT * FROM mytable;`
