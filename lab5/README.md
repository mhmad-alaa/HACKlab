# **Functions**

Function is a database object in SQL Server. Basically it is a set of SQL statements that accepts only input parameters, perform actions and return the result.

Function can return only single value or a table. We can’t use function to Insert, update and delete records in the database table.

Types of Functions
- System Defined Function
    - Scalar 
    - Aggregate 
- User Defined Function 
    - Scalar 
    - Inline Table-valued 
    - Multi Statment Table-valued 
--- 

### Differences between Inline Table-Valued Function and Multi Statement TableValued Function
1. In an inline table valued function, the RETURNS clause cannot contain the structure of the table, whereas with the multi-statement table valued function, we specify
the structure of the table that gets returned.
2. Inline table valued function cannot have BEGIN and END block, whereas the multistatement function can have.
3. Inline table valued functions are better for performance, than multi-statement table valued functions. If the given task can be achieved using an inline table valued function, always prefer to use them, over multi-statement table valued function.

--- 
### Differences between Stored Procedures and Functions

<div align="center">
<img src="/docs/sprocedure_fun.png" width="750">
</div>