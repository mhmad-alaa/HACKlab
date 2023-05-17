[Execution Link in online sql server compiler](https://onecompiler.com/sqlserver/3z8vryapu)


In this expample updates the value of a column due to some conditions and criteria, the point is the handling points and trasactinos, in the expample we needs to make, all updates done and if one update faile we need to undo the succeded ones, so we just but and use transactinos controllers to control or queriess to perform ACID properities.

```sql 
CREATE PROCEDURE transferMoney(@accountA CHAR(50), @accountB CHAR(50), @amount MONEY)
AS
  BEGIN 
    BEGIN TRANSACTION
    
      DECLARE @currentBalance MONEY
      SELECT @currentBalance = balance FROM account 
      WHERE account.accountNumber= @accountA;
      
      IF @currentBalance > @amount
      BEGIN
        UPDATE account
        SET account.balance = account.balance - @amount 
        WHERE account.accountNumber = @accountA;
        
        IF @@ERROR <> 0
        BEGIN
          PRINT 'Unexpected error occurred!'
        ROLLBACK
      End
      
      UPDATE account 
      SET account.balance = account.balance + @amount 
      WHERE account.accountNumber = @accountB;
      
      IF @@ERROR <> 0
      BEGIN
        PRINT 'Unexpected error occurred!'
      ROLLBACK

    End
  End
  
  COMMIT 
End
```

