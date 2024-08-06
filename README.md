# Hands-on-Project-Working-with-Joins-in-PostgreSQL-Using-PgAdmin

In this hands-on project, I worked with Joins in PostgreSQL Using PgAdmin

# Software Used in this Lab

PgAdmin 4 (PostgreSQL 15)

# Database Used in this Lab

The database used in this lab is an internal database belonging to IBM; a sample HR database. This is an HR database schema that consists of 5 tables called EMPLOYEES, JOB_HISTORY, JOBS, DEPARTMENTS and LOCATIONS. Each table has a few rows of sample data. The following diagram shows the tables for the HR database:

![image](https://github.com/user-attachments/assets/067a7925-0c1d-4a68-a62f-6f9879919301)

# Objective

The objective of this project is to run through some SQL practice problems that will provide hands-on experience with the different kinds of join operations.

# Highlights

- How does a CROSS JOIN (also known as Cartesian Join) statement syntax look?

      SELECT column_name(s)
      FROM table1
      CROSS JOIN table2;

- How does an INNER JOIN statement syntax look?

      SELECT column_name(s)
      FROM table1
      INNER JOIN table2
      ON table1.column_name = table2.column_name;
      WHERE condition;

- How does a LEFT OUTER JOIN statement syntax look?

      SELECT column_name(s)
      FROM table1
      LEFT OUTER JOIN table2
      ON table1.column_name = table2.column_name
      WHERE condition;

- How does a RIGHT OUTER JOIN statement syntax look?

      SELECT column_name(s)
      FROM table1
      RIGHT OUTER JOIN table2
      ON table1.column_name = table2.column_name
      WHERE condition;

  - How does a FULL OUTER JOIN statement syntax look?

      SELECT column_name(s)
      FROM table1
      LEFT  OUTER JOIN table2
      ON table1.column_name = table2.column_name
      WHERE condition

      UNION

      SELECT column_name(s)
      FROM table1
      RIGHT  OUTER JOIN table2
      ON table1.column_name = table2.column_name
      WHERE condition

  - Union operator

The UNION operator is used to combine the result-set of two or more SELECT statements.

Every SELECT statement within UNION must have the same number of columns
The columns must also have similar data types
The columns in every SELECT statement must also be in the same order

      SELECT column_name(s) FROM table1
      UNION
      SELECT column_name(s) FROM table2;

- How does a SELF JOIN statement syntax look?

      SELECT column_name(s)
      FROM table1 T1, table1 T2
      WHERE condition;

# Task A: Creating tables using SQL scripts

The new database named "HR DB" was created in PgAdmin and the tables were created by executing the following scripts rather than create each table manually by typing the DDL commands in the SQL editor.

The HR_Database_Create_Tables_Script.sql is available here: https://drive.google.com/file/d/1DOUzVXi-jsWBHR6CLNhAFQYUXdPjKFf7/view?usp=sharing

I downloaded the script file to my computer and uploaded it on my query editor of the HR DB I have initially created.

![image](https://github.com/user-attachments/assets/ebfef8e5-dbae-400c-a72f-260e281a6c94)


# Task B: Loading data into tables

The datasets were downloaded and imported into the already created tables as CSV files.

Departments.csv - file is available here: https://drive.google.com/file/d/16srI4TCFh_O8VGfrhd3q-msbFp_472zu/view?usp=sharing

Employees.csv - file is available here: https://drive.google.com/file/d/1LLGie9dXrR9WiFYE7t0vyD0eVCRajRtI/view?usp=sharing

Jobs.csv - file is available here: https://drive.google.com/file/d/1qLTJiiOUfgZ9sk8RIFV_6PlSM66pjUTR/view?usp=sharing

Locations.csv - file is available here: https://drive.google.com/file/d/1WHQja5oaxKn7EqWB0sOSD1sHGZnagSBh/view?usp=sharing

JobsHistory.csv - file is available here: https://drive.google.com/file/d/1-IZUPqwPlkU3BdMV5EW2zZl0tg7jZs7C/view?usp=sharing

To load each table, the following steps were taken:

1. Right-click on each table and select Import tab.

2. ChoOse the csv file and click OK 

3. The dataset was loaded

4. The above steps were repeated to load the other 4 datasets   
   
# Task C: Exploring the Tables

In exploring the tables within the database, the table was selected to view "All Rows" 

1. Dapartment Table

   ![image](https://github.com/user-attachments/assets/f35245c5-9a25-4c18-a06a-333e9a4fadd8)

2. Employees Table

   ![image](https://github.com/user-attachments/assets/f83d2120-5fb2-486f-857b-9c27353832b2)

3. Jobs Table

   ![image](https://github.com/user-attachments/assets/a9e3931b-0fdd-4949-834c-4297808923d3)

4. Locations Table

   ![image](https://github.com/user-attachments/assets/f75e89be-93ec-4b7d-ac16-63b5368bd9e7)

5. JobsHistory Table

   ![image](https://github.com/user-attachments/assets/5bcc6784-ba60-4089-b2b9-21a45554683c)

# Task D: Solving problems with JOINS

-1. Select the names and job start dates of all employees who work for the department number 5.

To address this problem, I issued the following query:

            SELECT E.emp_id, E.f_name, E.l_name, JH.start_date 
            FROM employees AS E
            INNER JOIN job_history AS JH
            ON E.emp_id = JH.empl_id
            WHERE E.dep_id = '5'
            
![image](https://github.com/user-attachments/assets/ab095898-c8d0-4352-951c-53682741f4f9)

-2. Select the names, job start dates, and job titles of all employees who work for the department number 5.

To address this problem, I issued the following query:

            SELECT E.emp_id, E.f_name, E.l_name, JH.start_date, J.job_title 
            FROM employees AS E
            INNER JOIN job_history AS JH
            ON E.emp_id = JH.empL_id
            INNER JOIN jobs AS J
            ON JH.jobs_id = J.job_ident
            WHERE E.dep_id = '5'

![image](https://github.com/user-attachments/assets/b494ac47-2e39-499c-8a39-5594f2c8a8b3)

-3. Perform a Left Outer Join on the EMPLOYEES and DEPARTMENT tables and select employee id, last name, department id and department name for
all employees.

To address this problem, I issued the following query:

            SELECT E.emp_id, E.l_name, E.dep_id, D.dep_name 
            FROM employees AS E
            LEFT OUTER JOIN departments AS D
            ON E.dep_id = D.dept_id_dep

![image](https://github.com/user-attachments/assets/d3eedf41-893e-4dfc-8aab-3e225eb9cd94)      

-4. Re-write the previous query but limit the result set to include only the rows for employees born before 1980.

To address this problem, I issued the following query:

            SELECT E.emp_id, E.l_name, E.dep_id, D.dep_name 
            FROM employees AS E
            LEFT OUTER JOIN departments AS D
            ON E.dep_id = D.dept_id_dep
            WHERE EXTRACT(YEAR FROM E.b_date) < 1980;

![image](https://github.com/user-attachments/assets/3ca29ec9-33ba-4796-bbb3-9e216a7e024a)


-5. Re-write the previous query but have the result set include all the employees but department names for only the employees who were born before 1980.

To address this problem, I issued the following query:

            SELECT E.emp_id, E.l_name, E.dep_id
            FROM employees AS E
            LEFT OUTER JOIN departments AS D
            ON E.dep_id = D.dept_id_dep
            AND EXTRACT(YEAR FROM E.b_date) < 1980;

![image](https://github.com/user-attachments/assets/65c2de74-e44b-4323-abb8-a047440638ea)

-6. Perform a Full Join on the EMPLOYEES and DEPARTMENT tables and select the First name, Last name and Department name of all employees.

To address this problem, I issued the following query:

            SELECT E.f_name, E.l_name, E.dep_id, D.dep_name
            FROM employees AS E
            FULL JOIN departments AS D
            ON E.dep_id = D.dept_id_dep
            
![image](https://github.com/user-attachments/assets/23210a6a-393b-4c24-99ee-36b27c0a2437)
            
-7. Re-write the previous query but have the result set include all employee names but department id and department names only for male employees.

To address this problem, I issued the following query:

            SELECT E.f_name, E.l_name, E.dep_id, D.dep_name
            FROM employees AS E
            LEFT OUTER JOIN departments AS D 
            ON E.dep_id = D.dept_id_dep AND E.sex = 'M'

            UNION

            SELECT E.f_name, E.l_name, E.dep_id, D.dep_name
            FROM employees AS E
            RIGHT OUTER JOIN departments AS D 
            ON E.dep_id = D.dept_id_dep AND E.sex = 'M';

![image](https://github.com/user-attachments/assets/011d7dff-0344-4860-9825-619349919dec)



