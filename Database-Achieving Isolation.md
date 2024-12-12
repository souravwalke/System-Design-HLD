**Isolation in Databases**

-------------------------------------------------------------------------------------------------------------------------------------------
**What is isolation in a Database?**

```Isolation means giving your girlfriend your undivided attention as if she's the only one in your world during that moment.``` 
    
Isolation ensures that each transaction is executed as if it’s the only one running in the system. Even if multiple transactions happen at the same time, they won’t interfere with each other. 

-------------------------------------------------------------------------------------------------------------------------------------------
**How is isolation achieved in Databases?**

Isolation is implemented using a combination of locking mechanisms, multi-versioning, and transaction scheduling.

**Pessimistic Locking**: The database locks specific rows, tables, or even the entire database while a transaction is working. Other transactions must    wait until the lock is released.

**Multiversion Concurrency Control (MVCC)**: Instead of locking the data, the database maintains multiple versions of data. Each concurrent transaction sees a consistent snapshot of the database based on when it started. Writes are made to a new version, and conflicts are resolved later.

**Serializable Isolation**: The database uses algorithms to schedule transactions in a way that ensures serializability.

------------------------------------------------------------------------------------------------------------------------------------------
**What is Two-Phase locking?**

Two-phase locking is a **protocol** used in databases to **ensure isolation** in transactions. It **guarantees serializability**. It consists of two phases, in the first phase (**growth phase**) the transaction acquires all the locks (shared & exclusive) it needs. Next, in the **shrinking phase**, the transaction starts releasing locks after execution. You can't release any locks in the growth phase and can't acquire any new locks in the shrinking phase. 

**Shared Locks (Read Locks)** - If a transaction only reads data, it uses shared locks.
**Exclusive Locks (Write Locks)** - If a transaction modifies data, it uses exclusive locks.
