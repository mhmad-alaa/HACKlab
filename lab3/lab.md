[Execution Link in online sql server compiler](https://onecompiler.com/sqlserver/3z88wsjdh)

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
```

Create and Execute procedure
``` sql 
create procedure insertValues @id int, @name varchar(100), @dept varchar(50)
as
begin 
  insert into EMPLOYEE(empId,name,dept) values (@id, @name, @dept)
end

Execute insertValues 99, 'ali ya ali', 'cse';
```

Drop Procedure
``` sql 
DROP PROCEDURE insertValues;
```

Alter Procedure\
same as create but create ~ alter
``` sql 
alter procedure insertValues @id int, @name varchar(100), @dept varchar(50)
as
begin 
  insert into EMPLOYEE(empId,name,dept) values (@id, @name, @dept)
end

Execute insertValues 99, 'ali ya ali', 'cse';
```



Default Parameter\
here i specifiy the 'cis' department as the default department if i don't enter one
``` sql 
create procedure insertValues @id int, @name varchar(100), @dept varchar(50) = 'cis'
as
begin 
  insert into EMPLOYEE(empId,name,dept) values (@id, @name, @dept)
end

Execute insertValues 99, 'ali ya ali';
```

Optional Parameter - Null Parameter\
it's a Default Parameter but the default value is null
and by defination the Optional Parameter must allow nulls 

``` sql 
create procedure insertValues @id int, @name varchar(100), @dept varchar(50) = null
as
begin 
  insert into EMPLOYEE(empId,name,dept) values (@id, @name, @dept)
end

Execute insertValues 99, 'ali ya ali';
``` 

Output Parameter\
again we say _unscientifically_ it's in programming languages (passing by reference)

``` sql 
create procedure insertValues @id int, @name varchar(100), @dept varchar(50), @ans int output
as
begin 
  select @ans = @id + 20 + (count(*) from EMPLOYEE where empId = @id) -- just do operations
end

declare @department
Execute insertValues 99, 'ali ya ali', @ans output; -- now the value of @department is

print @department -- will output the summation of the above statment operations
```

Return values
``` sql 
create procedure insertValues @id int, @name varchar(100), @dept varchar(50)
as
begin 
  return @id * 2 + 10 -- just operations or any values
end


-- hence that the ouput will be a value i need to store it in varaiable or print it 

declare @result 
@result = Execute insertValues 99, 'ali ya ali', 'cse'; -- store the return value

print @result
```

