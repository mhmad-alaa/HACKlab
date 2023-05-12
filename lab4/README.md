# **Triggers**

#### Triggers in sql server can be called *unscientifically* the **Background tasks** to sql operations.

#### Scientifically: A trigger is a special kind of a stored procedure that executes in response to certain action on the table like inserting, deleting or updating of data.
#### It is executed automatically. You can’t explicitly invoke triggers.
--- 

Simply, Triggers is some actions which occur within an operation to perform some tasks, mainly to help in security, maintainability of systems.

This *TRIGGER OPERATIONS* is like a check after insert or delete, a record for something that some user do something, 
or anything in this way. you can also say it's a 
**helper functions** to keep database system maintainable 
and secure as we can.

As we say triggers used to do some sql opertations in specific way to do specific tasks.

Triggers can be classified into two main types
- After Triggers (For Triggers)
- Instead Of Triggers
---

### After Triggers (For Triggers)
These triggers run after an **insert**, **update** or **delete** on a table.\
**They are not supported for views.**

#### AFTER TRIGGERS can be classified further into three types as:
- **AFTER** INSERT Trigger
- **AFTER** UPDATE Trigger
- **AFTER** DELETE Trigger

--- 
### Instead of Triggers
These can be used as an interceptor for anything that anyone tried to do on our table or view.\
If you define an Instead of trigger on a table for the
Delete operation, they try to delete rows, and they will not actually get deleted.

Unscientifically, it fake your sql query operations, 
it doesn't do what it suppose to do, so "instead of" the acctual operation it did another one.

#### INSTEAD OF TRIGGERS can be classified further into three types as:
- **INSTEAD OF** INSERT Trigger
- **INSTEAD OF** UPDATE Trigger
- **INSTEAD OF** DELETE Trigger
--- 

There are many other triggers like 
- Disabling trigger
    - used to disable a trigger temporarily in case of trubleshooting or data recovery
    ``` sql 
        DISABLE TRIGGER [trigger_name]
        ON [object_name | DATABASE | ALL SERVER]
    ```
- Enabling trigger
    - to enable a trigger so that the trigger can be fired whenever an event occurs
    ``` sql 
        ENABLE TRIGGER [trigger_name]
        ON [object_name | DATABASE | ALL SERVER]
    ```
- List all triggers
    ``` sql 
        SELECT
        *
        FROM
        sys.triggers
    ```
    