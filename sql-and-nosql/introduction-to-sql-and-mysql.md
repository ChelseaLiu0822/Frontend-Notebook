# Introduction to SQL and MySQL

SQL (Structured Query Language) is used to connect and interact with relational databases. MySQL is one of the most popular RDBMS (Relational Database Management Systems).

***

### Core SQL Operations

#### Table Creation and Insertion

* `CREATE TABLE` is used to define a table schema.
* `INSERT INTO` is used to add data to the table.

```sql
CREATE TABLE department (
  dept_id INT PRIMARY KEY,
  dept_name VARCHAR(50),
  dept_desc TEXT
);

CREATE TABLE employee (
  emp_id INT AUTO_INCREMENT PRIMARY KEY,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  dept_id INT,
  FOREIGN KEY (dept_id) REFERENCES department(dept_id)
);
```

***

#### SELECT Queries

* `SELECT * FROM table` retrieves all rows.
* Use `WHERE` clause to filter specific rows.

```sql
SELECT * FROM employee WHERE dept_id = 2;
```

***

### Referential Integrity & Foreign Keys

* A `FOREIGN KEY` ensures that a column value in one table must match a `PRIMARY KEY` value in another.
* Attempting to insert a `dept_id` in `employee` table that doesn't exist in the `department` table will raise an error.
* Deleting a department that has associated employees will fail due to referential integrity.

***

### JOIN Operations

Used to fetch data from multiple tables.

#### INNER JOIN

```sql
SELECT e.first_name, d.dept_name
FROM employee e
JOIN department d ON e.dept_id = d.dept_id;
```

* Only returns rows with matching `dept_id` in both tables.

#### LEFT JOIN

```sql
SELECT e.first_name, d.dept_name
FROM employee e
LEFT JOIN department d ON e.dept_id = d.dept_id;
```

* Returns all employees, even if they have no matching department.

#### RIGHT JOIN

```sql
SELECT e.first_name, d.dept_name
FROM employee e
RIGHT JOIN department d ON e.dept_id = d.dept_id;
```

* Returns all departments, even those with no employees.

#### FULL OUTER JOIN (not directly supported in MySQL)

* Emulated using `UNION` of `LEFT JOIN` and `RIGHT JOIN`.

***

### Venn Diagram Summary of JOIN Types

* **INNER JOIN**: Only overlapping rows.
* **LEFT JOIN**: All left table rows + matched right rows.
* **RIGHT JOIN**: All right table rows + matched left rows.
* **FULL OUTER JOIN**: All rows from both, matched where possible.

***

### UNION and UNION ALL

* `UNION` removes duplicates.
* `UNION ALL` includes duplicates.

```sql
SELECT dept_id FROM employee
UNION
SELECT dept_id FROM department;

SELECT dept_id FROM employee
UNION ALL
SELECT dept_id FROM department;
```

**Important Notes:**

* Both queries must have the same number and order of columns.

***

### Aggregation with GROUP BY

#### Example: Count Employees by Department

```sql
SELECT dept_id, COUNT(emp_id) AS employee_count
FROM employee
GROUP BY dept_id;
```

#### Replace `dept_id` with `dept_name`

```sql
SELECT d.dept_name, COUNT(e.emp_id) AS employee_count
FROM employee e
JOIN department d ON e.dept_id = d.dept_id
GROUP BY d.dept_name;
```

***

### Practical Exercises (In-Class)

**Task 1: Show employee last name and department description**

```sql
SELECT e.last_name, d.dept_desc
FROM employee e
JOIN department d ON e.dept_id = d.dept_id;
```

**Task 2: Group employee count by department name**

```sql
SELECT d.dept_name, COUNT(e.emp_id) AS employee_count
FROM employee e
JOIN department d ON e.dept_id = d.dept_id
GROUP BY d.dept_name;
```

***

### ALTER TABLE

Modify table structure post-creation.

#### Add a Column

```sql
ALTER TABLE employee ADD email VARCHAR(100);
```

#### Drop a Column

```sql
ALTER TABLE employee DROP COLUMN email;
```

#### Modify Column Type

```sql
ALTER TABLE employee MODIFY email VARCHAR(150);
```

***

### UPDATE Queries

Change existing row values.

```sql
UPDATE employee
SET last_name = 'Smith'
WHERE emp_id = 3;
```

**Caution:** Omitting `WHERE` updates all rows!
