[Execution Link in online sql server compiler](https://onecompiler.com/sqlserver/3z8uxm6hc)

--- 

Create database and insert values
``` sql 
CREATE TABLE EMPLOYEE (
  empId int,
  name varchar(100),
  dept varchar(50)
);

-- insert
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0001, 'Clark', 'Sales');
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0002, 'Dave', 'Accounting');
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0003, 'Ava', 'Sales');

-- fetch 
SELECT * FROM EMPLOYEE;
```
---

### System defined scalar function


Function take one parameter, do operation, return the edited value 
```sql 
SELECT UPPER('assdlDs')
SELECT LOWER('SSSSAAAdsLL')
SELECT ROUND(22.22335, 2)
SELECT ABS(-2332)
```
--- 
### System defined aggregate function 

Function operates in many values and return a single value after doing an  operation like sum the all values
```sql 
SELECT SUM(empId) FROM EMPLOYEE
SELECT AVG(empId) FROM EMPLOYEE
SELECT MAX(empId) FROM EMPLOYEE
SELECT MIN(empId) FROM EMPLOYEE
SELECT COUNT(empId) FROM EMPLOYEE
```

--- 
### User-defined scalar function

Function take many or one or zero parameters and return a single value after doing some operations to the parameters like join the names in the example 

```sql 
-- !note that it wouldn't work with the online compiler it needs more tools 

CREATE FUNCTION getFullName ( @firstname varchar(50), @lastname varchar(50) )
RETURNS varchar(100)
AS
  BEGIN
    RETURN (SELECT @firstname + ' ' + @lastname)
  END

SELECT getFullName('mhmad', 'alaa')
```

Zero parameters user-defined scalar function
```sql
CREATE FUNCTION getSumMath()
RETURNS INT
AS 
  BEGIN 
    RETURN (SELECT 23 + 22)
  END
  
SELECT getSumMath()
```

Function to return the mane of employee with his user-defined
```sql
CREATE FUNCTION getName(@id INT)
RETURNS VARCHAR(100)
AS 
  BEGIN 
    RETURN (SELECT name FROM EMPLOYEE WHERE empId = @id)
  END
  
  
SELECT getName(12)
```
--- 
### User-defined Inline Table-Valued FUNCTION

Function returns table-variable 

Function to return all employees in cse department
```sql
CREATE FUNCTION getEmployees(@department INT)
RETURNS TABLE    -- as shown the return type is table 
AS 
  RETURN (SELECT * FROM EMPLOYEE WHERE dept = @department) -- there isn't a BEGIN, END
  
  
SELECT * FROM getEmployees('CSE') -- that will iterate over the returned table 
```
--- 
### User-defined Multi-Statment Table-Valued FUNCTION

For symplecity: this FUNCTION just RETURNS a (table-variable)\
Or in general and with scientific way it returns a result set of combined data with scalar functions
```sql
CREATE FUNCTION getCopyOfEMPLOYEE()
-- how the returned table-variable structure look like 
RETURNS @EMP (emp_id INT, emp_name VARCHAR(100), emp_dept VARCHAR(100)) TABLE   
AS
  BEGIN
    -- do some operations on @EMP table-variable, like insert values or update it
    INSERT INTO @EMP SELECT e.empId, e.name, e.dept FROM EMPLOYEE e;
    
    UPDATE @EMP SET emp_name = 'mhmad-alaa' WHERE emp_id = 2;
  END


-- that call the function and display all values in returned table-variable
SELECT * from getCopyOfEMPLOYEE() 
```
