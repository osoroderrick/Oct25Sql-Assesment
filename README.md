# Oct25Sql-Assesment
 ```
describe movies;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| Title     | varchar(20)  | NO   |     |         |       |
| Runtime   | int unsigned | NO   | PRI | 0       |       |
| Genre     | varchar(20)  | NO   |     |         |       |
| IMDBScore | decimal(2,1) | NO   |     | 9.9     |       |
| Rating    | varchar(5)   | NO   |     |         |       |
+-----------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

 INSERT INTO movies VALUES
    -> ('Black Panther',134,'Action',7.3,'PG-13'),
    ->
    -> ('Captain America',120,'Action',8.0,'PG-13');
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> insert into movies Values
    -> ('Howard the Duck',110,'Sci-Fi',4.6,'PG'),
    -> ('Lavalantula',83,'Horror',4.7,'TV-14'),
    -> ('Starship Troopers',129,'Sci-Fi',7.2,'PG-13'),
    -> ('Spaceballs',96,'Comedy',7.1,'PG'),
    -> ('Monsters Inc.',92,'Animation',8.1,'G');
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0



mysql> select * from movies;
+-------------------+---------+-----------+-----------+--------+
| Title             | Runtime | Genre     | IMDBScore | Rating |
+-------------------+---------+-----------+-----------+--------+
| Lavalantula       |      83 | Horror    |       4.7 | TV-14  |
| Monsters Inc.     |      92 | Animation |       8.1 | G      |
| Spaceballs        |      96 | Comedy    |       7.1 | PG     |
| Howard the Duck   |     110 | Sci-Fi    |       4.6 | PG     |
| Captain America   |     120 | Action    |       8.0 | PG-13  |
| Starship Troopers |     129 | Sci-Fi    |       7.2 | PG-13  |
| Black Panther     |     134 | Action    |       7.3 | PG-13  |
+-------------------+---------+-----------+-----------+--------+
7 rows in set (0.00 sec)


select * from movies WHERE Genre = 'Sci-Fi';
+-------------------+---------+--------+-----------+--------+
| Title             | Runtime | Genre  | IMDBScore | Rating |
+-------------------+---------+--------+-----------+--------+
| Howard the Duck   |     110 | Sci-Fi |       4.6 | PG     |
| Starship Troopers |     129 | Sci-Fi |       7.2 | PG-13  |
+-------------------+---------+--------+-----------+--------+
2 rows in set (0.00 sec)

select * from movies WHERE IMDBScore >= 6.5;
+-------------------+---------+-------------+-----------+--------+
| Title             | Runtime | Genre       | IMDBScore | Rating |
+-------------------+---------+-------------+-----------+--------+
| Black Panther     |     134 | Action      |       7.3 | PG-13  |
| Captain America   |     120 | Action      |       8.0 | PG-13  |
| Monsters Inc.     |      92 | Animation   |       8.1 | G      |
| Spaceballs        |      96 | Comedy      |       7.1 | PG     |
| Starship Troopers |     129 | Sci-Fi      |       7.2 | PG-13  |
| Waltz With Bashir |      90 | Documentary |       8.0 | R      |
+-------------------+---------+-------------+-----------+--------+
6 rows in set (0.00 sec)

 select * from movies WHERE Rating = 'G' OR Rating = 'PG' and Runtime < 100;
+---------------+---------+-----------+-----------+--------+
| Title         | Runtime | Genre     | IMDBScore | Rating |
+---------------+---------+-----------+-----------+--------+
| Monsters Inc. |      92 | Animation |       8.1 | G      |
| Spaceballs    |      96 | Comedy    |       7.1 | PG     |
+---------------+---------+-----------+-----------+--------+
2 rows in set (0.00 sec)

select AVG(Runtime) from movies WHERE Rating < 7.5 GROUP BY Genre;
+--------------+
| AVG(Runtime) |
+--------------+
|      83.0000 |
|      92.0000 |
|      96.0000 |
|     119.5000 |
|     127.0000 |
+--------------+
5 rows in set, 5 warnings (0.02 sec)

update movies
    -> set Rating = 'R'
    -> WHERE Title = 'Starship Troopers';
Query OK, 1 row affected (0.02 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-----------+-----------+--------+
| Title             | Runtime | Genre     | IMDBScore | Rating |
+-------------------+---------+-----------+-----------+--------+
| Lavalantula       |      83 | Horror    |       4.7 | TV-14  |
| Monsters Inc.     |      92 | Animation |       8.1 | G      |
| Spaceballs        |      96 | Comedy    |       7.1 | PG     |
| Howard the Duck   |     110 | Sci-Fi    |       4.6 | PG     |
| Captain America   |     120 | Action    |       8.0 | PG-13  |
| Starship Troopers |     129 | Sci-Fi    |       7.2 | R      |
| Black Panther     |     134 | Action    |       7.3 | PG-13  |
+-------------------+---------+-----------+-----------+--------+
7 rows in set (0.00 sec)

