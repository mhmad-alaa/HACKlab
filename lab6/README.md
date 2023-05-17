# **Transaction Management**

### What is a Transaction?
Chunk of sql statments, needed to be grouped together for it's operations requirements, in other words we need these sql statments to be done or fail together.

{ set of sql statments have grouped characterestics } = transaction 

Scientifically, A transaction is a logical unit of work that contains one or more SQL statements. A
transaction is an atomic unit. So, all operations are guaranteed to succeed or fail as
one unit

--- 

### Transact-SQL statments in one transaction:
- Begin Transaction
- Rollback Transaction: to roll back the changes.
- Commit Transaction: to save the changes.
- Save Transaction: create points (savepoint) within groups of transactions in which to Rollback.

--- 

Transactional control commands are only used with the DML commands **INSERT, UPDATE** and **DELETE** only. They ***cannot*** be used while creating tables or dropping
them because these operations are **automatically committed** in the database.

---
Transaction Issues
- Concurrent execution of multiple transactions.
- Recovery after hardware failures and system crashes.


A transaction is characterized by four properties, often referred to as the **ACID** properties: atomicity, consistency, isolation, and durability.

- Atomicity
    - All operations done or nothing done.
- Consistency
    - No more than one changeable access acceptable to one resource at the same time.
- Isolation
    - Transaction can not affect data which currently affected by other transaction.
- Durability
    - No trasactions effect lose, in other words that's the 
    way of recovery to all logs to database, any successfull 
    transaction are kept, whatever happening to the system.
