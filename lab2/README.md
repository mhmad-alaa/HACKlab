# **SQL server programming**

There are two types of variables 
```
├── Local    
└── Global 
```
---
## **Local**
```sql server
starts with @
example: @id, @name
```

### Declared as
```sql server
DECLARE @variable_name datatype
```

### Set value to it as 
```sql 
SET @name = "human", 
    @id = 2
-- or from table vlaues
select @EmpId = id from emp where dept_id=1
```

It's shown that we use **set** and **select** to assign values to variables, what is the differnece
<div align="center">
<img src="/media/malaa/HDD Files/colleage/third/sec_term/dbase/dblab/docs/set_select.png" width="500">
<img src="/media/malaa/HDD Files/colleage/third/sec_term/dbase/dblab/docs/set_select_2.png" width="500">
</div>

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
``` sql server
starts with @@
example: @@id, @@name
```

Declared and set values with
``` sql server
select [global_variable] as [value]
```

--- 
## **Loops and conditional statements**

