

##### one-to-one 

relationship refers to a situation where each row in one table is associated with one, and only one, row in another table. In mathematical terms, this is known as a function or a "surjection", where each element in the domain (the first table) maps to a unique element in the range (the second table).

##### one-to-many 
relationship refers to a situation where one row in one table is associated with multiple rows in another table. In mathematical terms, this can be thought of as a function where one element in the domain (the first table) maps to multiple elements in the range (the second table).

##### many-to-many 
relationship refers to a situation where multiple rows in one table are associated with multiple rows in another table. In mathematical terms, this can be thought of as a "relation" where multiple elements in the domain (the first table) map to multiple elements in the range (the second table). This type of relationship is often implemented in SQL by creating a separate "junction" table that connects the two tables.

![ss](https://ds055uzetaobb.cloudfront.net/brioche/uploads/EkswlzPrzb-examp.svg?width=1500)


##### DML "Data Manipulation Language"
used to manage data within a relational database. Examples of DML statements include SELECT, INSERT, UPDATE, and DELETE.

##### DDL "Data Definition Language" 
used to define the structure of a relational database. Examples of DDL statements include CREATE, ALTER, and DROP.


##### TRUNCATE
 used to remove all the data from a table, but it does not remove the table structure or any associated constraints or indexes. It is a faster option than DELETE for removing large amounts of data because it does not generate undo logs or write data to the transaction log. TRUNCATE only available for table and it's a DDL statement

##### DELETE 
used to remove specific rows from a table. It allows you to specify a WHERE clause to determine which rows should be deleted. DELETE also generates undo logs and writes data to the transaction log, which makes it slower than TRUNCATE for large amounts of data. DELETE is a DML statement

##### DROP
used to remove a table or other database object, such as a view or an index. When you drop a table, all the data and the table structure are permanently removed, and any associated constraints or indexes are also deleted. This operation is irreversible and it's a DDL statement


Index


