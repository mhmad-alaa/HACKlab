# **SQL server programming**

There are two types of variables 
```
├── Local    
└── Global 
```
---
## **Local**
```sql
starts with @
example: @id, @name
```

### Declared as
```sql 
DECLARE @variable_name datatype
```

### Set value to it as 
```sql 
SET @name = "human", 
    @id = 2
-- or from table vlaues
set @EmpId = (select id from emp where id=20)
-- note that set allows only query returns one value, 
-- if it returned more it will be fail, unlike select 
-- which take the last value in this case
select @EmpId = id from emp where dept_id=1
```

Note
```md
You can declare anything as a variable, 
that mean you can declare tables also as a variable
```

Declare table datatype 
```sql
DECLARE @mytable table
(
 col1 int NOT NULL,
 col2 varchar(100)
)
```

We can insert values to @mytable variable 
```sql
insert into @mytable values (1,'ali'), (2,'kamal')
-- or from other table using select
insert into @mytable
select SSN, Fname from employee where DNO =10
```

And we can easily print table variable content 
```sql
select * from @mytable
```


--- 

## **Global**
