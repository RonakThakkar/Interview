# SQL Interview Questions

## General Questions

## Programming Questions

* Difference between DELETE and TRUNCATE
* Difference between Funcion and Stored Procedure
* Difference between Cluster and Non-Cluster Index
* What is the use of DBCC commands? - DBCC stands for database consistency checker. We use these commands to check the consistency of the databases, i.e., maintenance, validation task and status checks. 
* Can you give me some DBCC command options?(Database consistency check) - DBCC CHECKDB - Ensures that tables in the db and the indexes are correctly linked.and DBCC CHECKALLOC - To check that all pages in a db are correctly allocated. DBCC SQLPERF - It gives report on current usage of transaction log in percentage. DBCC CHECKFILEGROUP - Checks all tables file group for any damage.
* What is the difference between a HAVING CLAUSE and a WHERE CLAUSE? - Having Clause is basically used only with the GROUP BY function in a query. WHERE Clause is applied to each row before they are part of the GROUP BY function in a query
* Linked Server
* Types of Joins
* How do you troubleshoot SQL Server if its running very slow? - First check the processor and memory usage to see that processor is not above 80% utilization and memory not above 40-45% utilization then check the disk utilization using Performance Monitor, Secondly, use SQL Profiler to check for the users and current SQL activities and jobs running which might be a problem. Third would be to run UPDATE_STATISTICS command to update the indexes

Difference Between Function and Stored Procedure

| Function      | Stored Procedure |
| -----------    -----------       |
| A FUNCTION always returns a value using the return statement. | A PROCEDURE may return one or more values through parameters or may not return at all.

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

## Find Duplicate records in database

Users
Username	Firstname	Lastname	gender		address		phonenumber
ronak_beit	Ronak		Thakkar		M		Ahmedabad	123
ronak_beit	Ronak		Thakkar		M		Ahmedabad	234
payal_thakkar	Payal		Thakkar		F		Ahmedabad	123

Finding duplicate records
select * from Users group by *(Username, Firstname, Lastname, gender, address, phonenumber)
having count(*) > 1

Deleting duplicate records
Select * into Users_Temp from Users group by *(Username, Firstname, Lastname, gender, address, phonenumber)
having count(*) = 1
-- This will move unique records into Users_Temp table.

Drop Users Table
Rename Users_Temp table to Users

Products
ID	Name	Description	Price
1	Mouse	Mouse Desc	200
1	Mouse	Mouse Desc	200
