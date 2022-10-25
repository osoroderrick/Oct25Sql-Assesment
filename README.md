# Oct25Sql-Assesment
 ```
 create table movies(
    -> Title varchar(20) NOT NULL DEFAULT '',
    -> Runtime int unsigned NOT NULL DEFAULT 0,
    -> Genre varchar(20) NOT NULL DEFAULT '',
    -> IMDBScore decimal(2,1) NOT NULL DEFAULT 9.9,
    -> Rating varchar(5) NOT NULL DEFAULT '',
    -> PRIMARY KEY (Title)
    -> );
Query OK, 0 rows affected (0.09 sec)

mysql> describe movies;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| Title     | varchar(20)  | NO   | PRI |         |       |
| Runtime   | int unsigned | NO   |     | 0       |       |
| Genre     | varchar(20)  | NO   |     |         |       |
| IMDBScore | decimal(2,1) | NO   |     | 9.9     |       |
| Rating    | varchar(5)   | NO   |     |         |       |
+-----------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

INSERT INTO movies VALUES
    -> ('Howard the Duck',110,'Sci-Fi',4.6,'PG'),
    -> ('Lavalantula',83,'Horror',4.7,'TV-14'),
    -> ('Starship Troopers',129,'Sci-Fi',7.2,'PG-13'),
    -> ('Waltz With Bashir',90,'Documentary',8.0,'R'),
    -> ('Spaceballs',96,'Comedy',7.1,'PG'),
    -> ('Monsters Inc.',92,'Animation',8.1,'G');
Query OK, 6 rows affected (0.01 sec)
Records: 6  Duplicates: 0  Warnings: 0

INSERT INTO movies VALUES
    -> ('Black Panther',134,'Action',7.3,'PG-13'),
    -> ('Captain America',120,'Action',8.0,'PG-13');
Query OK, 2 rows affected (0.02 sec)
Records: 2  Duplicates: 0  Warnings: 0


select * from movies WHERE Genre = 'Sci-Fi';
+-------------------+---------+--------+-----------+--------+
| Title             | Runtime | Genre  | IMDBScore | Rating |
+-------------------+---------+--------+-----------+--------+
| Howard the Duck   |     110 | Sci-Fi |       4.6 | PG     |
| Starship Troopers |     129 | Sci-Fi |       7.2 | PG-13  |
+-------------------+---------+--------+-----------+--------+
2 rows in set (0.00 sec)

