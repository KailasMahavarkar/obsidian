
In order to efficiently find the value for a particular key in the database, we need a different data structure: an index.

#### This is an important trade-off in storage systems: `well-chosen indexes speed up read queries, but every index slows down writes(Any kind of index usually slows down writes, because the index also needs to be updated every time data is written).` 


> For this reason, databases don’t usually index everything by default, but require you—the application developer or database administrator—to choose indexes manually, using your knowledge of the application’s typical query patterns. 
