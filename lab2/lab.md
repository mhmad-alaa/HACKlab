[Execution Link in online sql server editor](https://onecompiler.com/sqlserver/3z83jg7cn)

---
Create database and insert values
```sql server
CREATE TABLE EMPLOYEE (
  empId int,
  name varchar(100),
  dept varchar(50)
);

-- insert
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0001, 'Clark', 'Sales');
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0002, 'Dave', 'Accounting');
INSERT INTO EMPLOYEE(empId,name,dept) VALUES (0003, 'Ava', 'Sales');
```
### **Local** 
Declare a local variables without intialization
``` sql server
DECLARE @name VARCHAR(50), 
    @id INT;
```

Declare a local variable and intialize it
``` sql server
DECLARE @dept_name VARCHAR(50) = 'computer and systems'
```

Set value to declared variables above using **set** statment
``` sql server
set @name = "mhmad-alaa"
set @id = 22
set @dept_name = "cse"
set @dept_name = "cce"
```

Display the variables, what is the output!
``` sql server
print @name             -- mhmad-alaa
print @id               -- 22
print @dept_name        -- cce
```

:warning:
 Important Note
 ```
  local variables are just variables 
  its not affect table anyway or conflict with it 
  its just a variable carry data
 ``` 

Declare a local table variable and insert values
``` sql server
DECLARE @Student table
(
 id int NOT NULL,
 name varchar(100)
)

insert into @Student values
(1,'ali'),
(2,'kamal')
```

You can insert in table variabel using select
``` sql server
insert into @Student
select empId, name from EMPLOYEE where dept = 'Sales'
```


### **Global**
Everything about Global variables is that it's declared and assigned with values as in this example 

``` sql server
SELECT @@LANGUAGE as 'Engilsh'
print @@LANGUAGE
```



### **Loops and Conditional statments**

If-else 
``` sql server
BEGIN 
if (@id < 22) 
  print "ok it works";
else if (@id != 22)
  print "bruh take a rest";
else if (@id + 2 = 24)
  print "for what all of that!";
END;

```
While
``` sql server
while (@id <= 27) 
BEGIN
    set @id = @id + 1
    
    if (@id = 24) print @id
    else if (@id = 25) 
      BREAK; 
END
```

Delete all records starting from id = 1 to id =2
``` sql server
DECLARE @iterator int = 1

while (@iterator between 1 and 2) 
  BEGIN 
  -- specifiy the table and the action you want to do work
    Delete from EMPLOYEE  
    where empId = @iterator -- where / selcection statment
    
    set @iterator = @iterator + 1  -- increase counter 
  END
```

Update all the id's of the EMPLOYEE table with 1000, and stop when the max is less than 5000

``` sql server
while ((SELECT max(empId) from EMPLOYEE) < 20) 
  BEGIN
  -- these two lines update all the records of the table mantionned
    update EMPLOYEE  
    set empId = empId + 1000    
    
    SELECT "** debug star" -- to show how many iteration will occur
    SELECT max(empId) from EMPLOYEE
  END

```

--- 
### **Error Handling**

Try catch errors in sql server
``` sql server
BEGIN TRY
  SELECT 10/0 AS Result;
END TRY
BEGIN CATCH
  SELECT ERROR_MESSAGE() AS [Error Message]
   ,ERROR_LINE() AS ErrorLine
   ,ERROR_NUMBER() AS [Error Number]
END CATCH
```
