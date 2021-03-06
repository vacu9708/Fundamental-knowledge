### Example table1
|id|student_name|email|grade|
|---|---|---|---|
|1|John|qwe@gmail.com|90|
|2|Paul|asd@gmail.com|80|
|3|Katherine|zxc@gmail.com|70|
|4|Ana|wer@gmail.com|70|

### Example table2
|id|student_name|email|grade|
|---|---|---|---|
|1|Smith|sdf@gmail.com|90|
|2|Maria|xcv@gmail.com|90|
|3|Ana|ert@gmail.com|80|

### SQL to create example tables
~~~sql
use first_database;

create table if not exists students1(
    id INT(99) primary key AUTO_INCREMENT comment 'ID',
    student_name varchar(99) not null comment 'student_name',
    email varchar(99) not null comment 'email',
    grade INT(99) not null comment 'grade'
);
create table if not exists students2(
    id INT(99) primary key AUTO_INCREMENT comment 'ID',
    student_name varchar(99) not null comment 'student_name',
    email varchar(99) not null comment 'email',
    grade INT(99) not null comment 'grade'
);

INSERT INTO students1(student_name, email, grade) VALUES('John', 'qwe@gmail.com', '90');
INSERT INTO students1(student_name, email, grade) VALUES('Paul', 'asd@gmail.com', '80');
INSERT INTO students1(student_name, email, grade) VALUES('Katherine', 'zxc@gmail.com', '70');
INSERT INTO students1(student_name, email, grade) VALUES('Andrea', 'wer@gmail.com', '70');

INSERT INTO students2(student_name, email, grade) VALUES('Smith', 'sdf@gmail.com', '90');
INSERT INTO students2(student_name, email, grade) VALUES('Maria', 'xcv@gmail.com', '90');
INSERT INTO students2(student_name, email, grade) VALUES('Ana', 'ert@gmail.com', '80');
~~~

The **database key** is an attribute or a group of attributes that can uniquely identify each record in a table.<br>

* **Candidate key** : one or more keys that can uniquely identify rows in a table
Ex) id, email. student_name cannot be a candidate key because there may be a duplication.
* **Primary key** : a key selected among candidate keys
* **Super key** : a subset of keys that can uniquely identify rows in a table and has one or more unnecessary attributes
Ex) id + studnet_name
* **Alternate key** : remaining keys after excluding the primary key

# JOIN
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.
## INNER JOIN
The INNER JOIN is the most common and default JOIN clause. It returns rows that have matching values in both tables

![image](https://user-images.githubusercontent.com/67142421/177883594-b714df59-1b5b-4a9e-9e91-76fbfa5aaafe.png)

**Both make the same result**
~~~sql
SELECT students1.student_name, students2.student_name, students1.grade
FROM students1, students2 WHERE students1.grade = students2.grade;
~~~
~~~sql
SELECT students1.student_name, students2.student_name, students1.grade
FROM students1 INNER JOIN students2 ON students1.grade = students2.grade;
~~~
### Output
![image](https://user-images.githubusercontent.com/67142421/177880242-75572761-ee2c-4c4a-98d1-0970905ffeb5.png)

## LEFT JOIN
The LEFT JOIN returns all rows from the left table and the matching rows from the right table. It returns NULL for no matching rows in the right table.

![image](https://user-images.githubusercontent.com/67142421/177880429-7f2cd5a9-a9ed-42ad-8049-50ea628dede2.png)

~~~sql
SELECT students1.student_name, students2.student_name, students1.grade
FROM students1 LEFT JOIN students2 ON students1.grade = students2.grade;
~~~~

### Output
![image](https://user-images.githubusercontent.com/67142421/177883665-33dc874d-0ca8-47eb-9c6e-83642080dc41.png)

Both make the same result.
~~~sql
SELECT *
FROM students1 CROSS JOIN students2;
~~~
~~~sql
SELECT *
FROM students1, students2;
~~~
