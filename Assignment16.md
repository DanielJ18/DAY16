
mysql> select first_name, last_name from student;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Eric       | Ephram    |
| Greg       | Gould     |
| Adam       | Ant       |
| Howard     | Hess      |
| Charles    | Caldwell  |
| James      | Joyce     |
| Doug       | Dumas     |
| Kevin      | Kraft     |
| Frank      | Fountain  |
| Brian      | Biggs     |
+------------+-----------+
10 rows in set (0.00 sec)



mysql> select *  from student where years_of_experience < 8;
+-----+------------+-----------+---------------------+------------+
| id  | first_name | last_name | years_of_experience | start_date |
+-----+------------+-----------+---------------------+------------+
| 100 | Eric       | Ephram    |                   2 | 2016-03-31 |
| 110 | Greg       | Gould     |                   6 | 2016-09-30 |
| 120 | Adam       | Ant       |                   5 | 2016-06-02 |
| 130 | Howard     | Hess      |                   1 | 2016-02-28 |
| 140 | Charles    | Caldwell  |                   7 | 2016-05-07 |
| 170 | Kevin      | Kraft     |                   3 | 2016-04-15 |
| 190 | Brian      | Biggs     |                   4 | 2015-12-25 |
+-----+------------+-----------+---------------------+------------+
7 rows in set (0.00 sec)


mysql> select last_name, start_date, id  from student
    -> order by last_name desc;
+-----------+------------+-----+
| last_name | start_date | id  |
+-----------+------------+-----+
| Kraft     | 2016-04-15 | 170 |
| Joyce     | 2016-08-27 | 150 |
| Hess      | 2016-02-28 | 130 |
| Gould     | 2016-09-30 | 110 |
| Fountain  | 2016-01-31 | 180 |
| Ephram    | 2016-03-31 | 100 |
| Dumas     | 2016-07-04 | 160 |
| Caldwell  | 2016-05-07 | 140 |
| Biggs     | 2015-12-25 | 190 |
| Ant       | 2016-06-02 | 120 |
+-----------+------------+-----+
10 rows in set (0.00 sec)


mysql> select *  from student where first_name in('Adam', 'James', 'Frank')
    -> order by last_name desc;
+-----+------------+-----------+---------------------+------------+
| id  | first_name | last_name | years_of_experience | start_date |
+-----+------------+-----------+---------------------+------------+
| 150 | James      | Joyce     |                   9 | 2016-08-27 |
| 180 | Frank      | Fountain  |                   8 | 2016-01-31 |
| 120 | Adam       | Ant       |                   5 | 2016-06-02 |
+-----+------------+-----------+---------------------+------------+
3 rows in set (0.00 sec)



mysql> select first_name, last_name, start_date from student
    -> where start_date between '2016-01-01' and '2016-06-30'
    -> order by start_date desc;
+------------+-----------+------------+
| first_name | last_name | start_date |
+------------+-----------+------------+
| Adam       | Ant       | 2016-06-02 |
| Charles    | Caldwell  | 2016-05-07 |
| Kevin      | Kraft     | 2016-04-15 |
| Eric       | Ephram    | 2016-03-31 |
| Howard     | Hess      | 2016-02-28 |
| Frank      | Fountain  | 2016-01-31 |
+------------+-----------+------------+
6 rows in set (0.00 sec)
| Tables_in_tiy |
+---------------+
| assignment    |
| student       |
+---------------+
2 rows in set (0.00 sec)

mysql> explain assignment;
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| id             | int(11)     | NO   | PRI | NULL    |       |
| student_id     | int(11)     | NO   | MUL | NULL    |       |
| assignment_nbr | int(11)     | NO   |     | NULL    |       |
| grade          | varchar(30) | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
4 rows in set (0.46 sec)

mysql> alter table assignment drop column grade;
Query OK, 0 rows affected (2.10 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> explain assignment;
+----------------+---------+------+-----+---------+-------+
| Field          | Type    | Null | Key | Default | Extra |
+----------------+---------+------+-----+---------+-------+
| id             | int(11) | NO   | PRI | NULL    |       |
| student_id     | int(11) | NO   | MUL | NULL    |       |
| assignment_nbr | int(11) | NO   |     | NULL    |       |
+----------------+---------+------+-----+---------+-------+
3 rows in set (0.05 sec)

mysql> alter table assignment add column grade_id int;
Query OK, 0 rows affected (0.65 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> explain assignment;
+----------------+---------+------+-----+---------+-------+
| Field          | Type    | Null | Key | Default | Extra |
+----------------+---------+------+-----+---------+-------+
| id             | int(11) | NO   | PRI | NULL    |       |
| student_id     | int(11) | NO   | MUL | NULL    |       |
| assignment_nbr | int(11) | NO   |     | NULL    |       |
| grade_id       | int(11) | YES  |     | NULL    |       |
+----------------+---------+------+-----+---------+-------+
4 rows in set (0.00 sec)
