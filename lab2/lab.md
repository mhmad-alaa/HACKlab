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






[Execution Link](https://onecompiler.com/sqlserver/3z83jg7cn)