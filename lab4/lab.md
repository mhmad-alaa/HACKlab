[Execution Link in online sql server compiler](https://onecompiler.com/sqlserver/3z8d6rm8s)

--- 

Create database and insert values

``` sql 
-- create
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
GO
```

--- 

### AFTER TRIGGERS
Insert into table EmployeeAudit after deletion from table Employee

``` sql 
-- the example shows (we can say log actions record table) to the deletion actions happening

create trigger tr_emp_forDelete 
  on EMPLOYEE
  after delete
  as
  begin
    declare @id int
    select @id = empId from deleted
    insert into EmployeeAudit
    values('new employee deleted of id '+cast(@id as varchar(5))+'at time' + cast(getDate() as varchar(20)))
  end

-- As you see from the above example the trigger created "ON" the table 
-- and done "AFTER" some operation done as "delete" or "insert" 
```

Insert like (log record) to EmployeeAudit table  after inserting data to the EMPLOYEE table

```sql 
create trigger tr_emp_forInsert
  on EMPLOYEE
  after insert
  as
  begin
    -- declare @id int -- commented here because we declared before in the above example
    select @id = empId from inserted
    insert into EmployeeAudit
    values ('new employee inserted of id '+ cast (@id as varchar(5)))
  end
```

--- 

### Instead of Triggers

Trigger that prevent deletion from table EMPLOYEE
``` sql 
create trigger tr_emp_InsteadUpdate
  on EMPLOYEE
  instead of delete
  as
  begin
    select 'deletion not allowed!'
  end
```

Trigger that prevent you to delete, insert and update from table EMPLOYEE
``` sql 
create trigger tr_emp_Instead
  on catalog
  instead of delete, update, insert
  as
  begin
    select 'deletion, insertion or update Not Allowed'
  end
```
