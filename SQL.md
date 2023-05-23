# Normalization

Normalization is the process of organizing data in a database to eliminate redundancy and improve data integrity. It involves breaking down a larger table into smaller, more manageable tables and establishing relationships between them. There are several normal forms (NFs) that define specific criteria for data organization. Let's discuss the first three normal forms with examples and tables.

1. First Normal Form (1NF):
   - Each column in a table must contain atomic values (indivisible and non-repeating).
   - No repeating groups or arrays are allowed.

   Example:
   Consider a table that stores customer orders:
   
   | OrderID | CustomerName       | Items               |
   |---------|--------------------|---------------------|
   | 1       | John Doe           | Apples, Oranges      |
   | 2       | Jane Smith         | Grapes              |
   | 3       | Mary Johnson       | Apples, Bananas, Kiwis |

   The table violates 1NF because the "Items" column contains multiple values. To normalize it to 1NF, we split the repeating values into separate rows:

   | OrderID | CustomerName       | Item                |
   |---------|--------------------|---------------------|
   | 1       | John Doe           | Apples              |
   | 1       | John Doe           | Oranges             |
   | 2       | Jane Smith         | Grapes              |
   | 3       | Mary Johnson       | Apples              |
   | 3       | Mary Johnson       | Bananas             |
   | 3       | Mary Johnson       | Kiwis               |

2. Second Normal Form (2NF):
   - The table must be in 1NF.
   - All non-key attributes (columns) should depend on the entire primary key.

   Example:
   Consider a table that stores student course registrations:
   
   | StudentID | CourseID | CourseName       | Instructor      |
   |-----------|----------|-----------------|-----------------|
   | 1         | 101      | Math 101        | Prof. Johnson   |
   | 2         | 101      | Math 101        | Prof. Johnson   |
   | 1         | 201      | Physics 201     | Prof. Smith     |
   | 3         | 301      | Chemistry 301   | Prof. Anderson  |

   The table violates 2NF because the "CourseName" and "Instructor" columns depend on the partial key {StudentID, CourseID}. To normalize it to 2NF, we split the table into two:

   | StudentID | CourseID |
   |-----------|----------|
   | 1         | 101      |
   | 2         | 101      |
   | 1         | 201      |
   | 3         | 301      |
   
   | CourseID | CourseName       | Instructor      |
   |----------|-----------------|-----------------|
   | 101      | Math 101        | Prof. Johnson   |
   | 201      | Physics 201     | Prof. Smith     |
   | 301      | Chemistry 301   | Prof. Anderson  |

3. Third Normal Form (3NF):
   - The table must be in 2NF.
   - All non-key attributes should depend only on the primary key (no transitive dependencies).

   Example:
   Consider a table that stores employee information:
   
   | EmployeeID | Department   | ManagerID | ManagerName  |
   |------------|--------------|-----------|--------------|
   | 1          | Sales        | 3         | John Smith   |
   | 2          | Marketing    | 3         | John Smith

   |
   | 3          | Operations   | 4         | Jane Johnson |
   | 4          | HR           | NULL      | NULL         |

   The table violates 3NF because the "ManagerName" column depends on the non-key attribute "ManagerID" instead of the primary key "EmployeeID". To normalize it to 3NF, we split the table into two:

   | EmployeeID | Department   | ManagerID |
   |------------|--------------|-----------|
   | 1          | Sales        | 3         |
   | 2          | Marketing    | 3         |
   | 3          | Operations   | 4         |
   | 4          | HR           | NULL      |
   
   | EmployeeID | ManagerName  |
   |------------|--------------|
   | 1          | John Smith   |
   | 2          | John Smith   |
   | 3          | Jane Johnson |
   
These are the first three normal forms (1NF, 2NF, and 3NF). Normalization beyond 3NF involves higher normal forms such as Boyce-Codd Normal Form (BCNF), Fourth Normal Form (4NF), and Fifth Normal Form (5NF), which address more complex dependencies.
