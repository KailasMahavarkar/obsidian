What is a Write Ahead Log?
Assume you have done a write operation, do you think it directly writes to main disk?? WRONG it never does!

Assume your change is only 1 byte, its overkill that db operation should happen for such a small change.
So we have a write-ahead log which contains "n" write operations

can we read data from WAL?
- its a bad idea, the work you want to do is enormous
- it can be done but its hard

WAL is ahead?
- it takes the page and reads it into memory 
- WAL is also called REDO WAL reason is we only wrote to log and now only WAL log knows the changes so logically a REDO of all operations needs to be done

what is checkpointing in terms of WAL?
- its a data intensive operation, SQL warns about it
- it basically is purge operation to remove old data from WAL

What is fsync(force sync)?
OS also has a file system cache just like WAL which stores info about multiple writes.
OS waits for these cache to fill and flush to disk

fsync disabled (default state) 
fsync enabled -> bypasses caching and Force Sync data

---
#wal #database-design #backend