# **Stored Procedure**

### Procedures in sql server can be called *unscientifically* the **sql functions**

### Scientifically is the set of logical group of SQL statements which are grouped to perform a specific task.

Procedures benefits:
- Simplify repeated tasks
- Run Faster
    - Stored procedures are cached on the server
- Reduce network traffic
- Help to provide security
    - Limit direct access to tables via defined roles in the database
- Errors can be handled in procedure code without being passed directly to client applications.
- Protecting against some SQL injection attacks.
- Stored procedures can be written once and accessed by many applications.
---

:warning:
 Important Note
 ```
  Proceddures processing if we can say it's not an iterative 
  process across it's requirements in the database system.

  That mean you need to create a table first and somehow 
  make the proceddures out of the transactions queries.

  That mean you can't use an online compiler which process 
  all in one file like a script.
 ``` 
--- 
### How to create or alter procedure!
``` sql server
create/alter procedure myproceddure @item1 int, @item2 nvarchar(100)
as
begin
insert into mytable (var1,var2)
values (@item1,@item2)
end
```

### How to drop the procedure from database!
``` sql
DROP PROCEDURE procedure_name;
```

:bell:
Important Note
```
There are differneces between procedures in many things like

- Default Parameter
    - you can specifiy a values as the default or not

- Optional Parameter – NULL Parameter
    - if you don't pass the value it set the default,
        the default may be null
- Output Parameter
    - it's the returned value from the procedure
    - it defined in the procedure parameters with <output>
        and with Execute code wiht <output> to 
- Return Values
    - it's mostly like the Output Parameter, 
        but they differ in some criterias witll shown.
```

|**Return Value** | **Output Parameters** |
|:--------|:-----------:|
| Only Integer Datatype | Any Datatype|
| Only one value returned | More than one value returned|
| Use to convy sucess to failure| Use to return values like id, name, count|
