SQL Server Interview Questions

1.	What is normalization? - Well a relational database is basically composed of tables that contain related data. So the Process of organizing this data into tables is actually referred to as normalization. 
2.	What is a Stored Procedure? - Its nothing but a set of T-SQL statements combined to perform a single task of several tasks. Its basically like a Macro so when you invoke the Stored procedure, you actually run a set of statements. 
3.	Can you give an example of Stored Procedure? - sp_helpdb , sp_who2, sp_renamedb are a set of system defined stored procedures. We can also have user defined stored procedures which can be called in similar way. 
4.	What is a trigger? - Triggers are basically used to implement business rules. Triggers is also similar to stored procedures. The difference is that it can be activated when data is added or edited or deleted from a table in a database. 
5.	What is a view? - If we have several tables in a db and we want to view only specific columns from specific tables we can go for views. It would also suffice the needs of security some times allowing specfic users to see only specific columns based on the permission that we can configure on the view. Views also reduce the effort that is required for writing queries to access specific columns every time. 
6.	What is an Index? - When queries are run against a db, an index on that db basically helps in the way the data is sorted to process the query for faster and data retrievals are much faster when we have an index. 
7.	What are the types of indexes available with SQL Server? - There are basically two types of indexes that we use with the SQL Server. Clustered and the Non-Clustered. 
8.	What is the basic difference between clustered and a non-clustered index? - The difference is that, Clustered index is unique for any given table and we can have only one clustered index on a table. The leaf level of a clustered index is the actual data and the data is resorted in case of clustered index. Whereas in case of non-clustered index the leaf level is actually a pointer to the data in rows so we can have as many non-clustered indexes as we can on the db. 
9.	What are cursors? - Well cursors help us to do an operation on a set of data that we retreive by commands such as Select columns from table. For example : If we have duplicate records in a table we can remove it by declaring a cursor which would check the records during retreival one by one and remove rows which have duplicate values. 
10.	When do we use the UPDATE_STATISTICS command? - This command is basically used when we do a large processing of data. If we do a large amount of deletions any modification or Bulk Copy into the tables, we need to basically update the indexes to take these changes into account. UPDATE_STATISTICS updates the indexes on these tables accordingly. 
11.	Which TCP/IP port does SQL Server run on? - SQL Server runs on port 1433 but we can also change it for better security. 
12.	From where can you change the default port? - From the Network Utility TCP/IP properties –> Port number.both on client and the server. 
13.	Can you tell me the difference between DELETE & TRUNCATE commands? - Delete command removes the rows from a table based on the condition that we provide with a WHERE clause. Truncate will actually remove all the rows from a table and there will be no data in the table after we run the truncate command. 
14.	Can we use Truncate command on a table which is referenced by FOREIGN KEY? - No. We cannot use Truncate command on a table with Foreign Key because of referential integrity. 
15.	What is the use of DBCC commands? - DBCC stands for database consistency checker. We use these commands to check the consistency of the databases, i.e., maintenance, validation task and status checks. 
16.	Can you give me some DBCC command options?(Database consistency check) - DBCC CHECKDB - Ensures that tables in the db and the indexes are correctly linked.and DBCC CHECKALLOC - To check that all pages in a db are correctly allocated. DBCC SQLPERF - It gives report on current usage of transaction log in percentage. DBCC CHECKFILEGROUP - Checks all tables file group for any damage. 
17.	What command do we use to rename a db? - sp_renamedb ‘oldname’ , ‘newname’ 
18.	Well sometimes sp_reanmedb may not work you know because if some one is using the db it will not accept this command so what do you think you can do in such cases? - In such cases we can first bring to db to single user using sp_dboptions and then we can rename that db and then we can rerun the sp_dboptions command to remove the single user mode. 
19.	What is the difference between a HAVING CLAUSE and a WHERE CLAUSE? - Having Clause is basically used only with the GROUP BY function in a query. WHERE Clause is applied to each row before they are part of the GROUP BY function in a query. 
20.	What do you mean by COLLATION? - Collation is basically the sort order. There are three types of sort order Dictionary case sensitive, Dictonary - case insensitive and Binary. 
21.	What is a Join in SQL Server? - Join actually puts data from two or more tables into a single result set. 
22.	Can you explain the types of Joins that we can have with Sql Server? - There are three types of joins: Inner Join, Outer Join, Cross Join 
23.	When do you use SQL Profiler? - SQL Profiler utility allows us to basically track connections to the SQL Server and also determine activities such as which SQL Scripts are running, failed jobs etc.. 
24.	What is a Linked Server? - Linked Servers is a concept in SQL Server by which we can add other SQL Server to a Group and query both the SQL Server dbs using T-SQL Statements. 
25.	Can you link only other SQL Servers or any database servers such as Oracle? - We can link any server provided we have the OLE-DB provider from Microsoft to allow a link. For Oracle we have a OLE-DB provider for oracle that microsoft provides to add it as a linked server to the sql server group. 
26.	Which stored procedure will you be running to add a linked server? - sp_addlinkedserver, sp_addlinkedsrvlogin 
27.	What are the OS services that the SQL Server installation adds? - MS SQL SERVER SERVICE, SQL AGENT SERVICE, DTC (Distribution transac co-ordinator) 
28.	Can you explain the role of each service? - SQL SERVER - is for running the databases SQL AGENT - is for automation such as Jobs, DB Maintanance, Backups DTC - Is for linking and connecting to other SQL Servers 
29.	How do you troubleshoot SQL Server if its running very slow? - First check the processor and memory usage to see that processor is not above 80% utilization and memory not above 40-45% utilization then check the disk utilization using Performance Monitor, Secondly, use SQL Profiler to check for the users and current SQL activities and jobs running which might be a problem. Third would be to run UPDATE_STATISTICS command to update the indexes 
30.	Lets say due to N/W or Security issues client is not able to connect to server or vice versa. How do you troubleshoot? - First I will look to ensure that port settings are proper on server and client Network utility for connections. ODBC is properly configured at client end for connection ——Makepipe & readpipe are utilities to check for connection. Makepipe is run on Server and readpipe on client to check for any connection issues. 
31.	What are the authentication modes in SQL Server? - Windows mode and mixed mode (SQL & Windows). 
32.	Where do you think the users names and passwords will be stored in sql server? - They get stored in master db in the sysxlogins table. 
33.	What is log shipping? Can we do logshipping with SQL Server 7.0 - Logshipping is a new feature of SQL Server 2000. We should have two SQL Server - Enterprise Editions. From Enterprise Manager we can configure the logshipping. In logshipping the transactional log file from one server is automatically updated into the backup database on the other server. If one server fails, the other server will have the same db and we can use this as the DR (disaster recovery) plan. 
34.	Let us say the SQL Server crashed and you are rebuilding the databases including the master database what procedure to you follow? - For restoring the master db we have to stop the SQL Server first and then from command line we can type SQLSERVER –m which will basically bring it into the maintenance mode after which we can restore the master db. 
35.	Let us say master db itself has no backup. Now you have to rebuild the db so what kind of action do you take? - (I am not sure- but I think we have a command to do it). 
36.	What is BCP? When do we use it? - BulkCopy is a tool used to copy huge amount of data from tables and views. But it won’t copy the structures of the same. 
37.	What should we do to copy the tables, schema and views from one SQL Server to another? - We have to write some DTS packages for it. 
38.	What are the different types of joins and what dies each do? 
39.	What are the four main query statements? 
40.	What is a sub-query? When would you use one? 
41.	What is a NOLOCK? 
42.	What are three SQL keywords used to change or set someone’s permissions? 
43.	What is the difference between HAVING clause and the WHERE clause? 
44.	What is referential integrity? What are the advantages of it? 
45.	What is database normalization? 
46.	Which command using Query Analyzer will give you the version of SQL server and operating system? 
47.	Using query analyzer, name 3 ways you can get an accurate count of the number of records in a table? 
48.	What is the purpose of using COLLATE in a query? 
49.	What is a trigger? 
50.	What is one of the first things you would do to increase performance of a query? For example, a boss tells you that “a query that ran yesterday took 30 seconds, but today it takes 6 minutes” 
51.	What is an execution plan? When would you use it? How would you view the execution plan? 
52.	What is the STUFF function and how does it differ from the REPLACE function? 
53.	What does it mean to have quoted_identifier on? What are the implications of having it off? 
54.	What are the different types of replication? How are they used? 
55.	What is the difference between a local and a global variable? 
56.	What is the difference between a Local temporary table and a Global temporary table? How is each one used? 
57.	What are cursors? Name four types of cursors and when each one would be applied? 
58.	What is the purpose of UPDATE STATISTICS? 
59.	How do you use DBCC statements to monitor various aspects of a SQL server installation? 
60.	How do you load large data to the SQL server database? 
61.	How do you check the performance of a query and how do you optimize it? 
62.	How do SQL server 2000 and XML linked? Can XML be used to access data? 
63.	What is SQL server agent? 
64.	What is referential integrity and how is it achieved? 
65.	What is indexing? 
66.	What is normalization and what are the different forms of normalizations? 
67.	Difference between server.transfer and server.execute method? 
68.	What id de-normalization and when do you do it? 
69.	What is better - 2nd Normal form or 3rd normal form? Why? 
70.	Can we rewrite subqueries into simple select statements or with joins? Example? 
71.	What is a function? Give some example? 
72.	What is a stored procedure? 
73.	Difference between Function and Procedure-in general? 
74.	Difference between Function and Stored Procedure? 
75.	Can a stored procedure call another stored procedure. If yes what level and can it be controlled? 
76.	Can a stored procedure call itself(recursive). If yes what level and can it be controlled.? 
77.	How do you find the number of rows in a table? 
78.	Difference between Cluster and Non-cluster index? 
79.	What is a table called, if it does not have neither Cluster nor Non-cluster Index? 
80.	Explain DBMS, RDBMS? 
81.	Explain basic SQL queries with SELECT from where Order By, Group By-Having? 
82.	Explain the basic concepts of SQL server architecture? 
83.	Explain couple pf features of SQL server 
84.	Scalability, Availability, Integration with internet, etc.)? 
85.	Explain fundamentals of Data ware housing & OLAP? 
86.	Explain the new features of SQL server 2000? 
87.	How do we upgrade from SQL Server 6.5 to 7.0 and 7.0 to 2000? 
88.	What is data integrity? Explain constraints? 
89.	Explain some DBCC commands? 
90.	Explain sp_configure commands, set commands? 
91.	Explain what are db_options used for? 
92.	What is the basic functions for master, msdb, tempdb databases? 
93.	What is a job? 
94.	What are tasks? 
95.	What are primary keys and foreign keys? 
96.	How would you Update the rows which are divisible by 10, given a set of numbers in column? 
97.	If a stored procedure is taking a table data type, how it looks? 
98.	How m-m relationships are implemented? 
99.	How do you know which index a table is using? 
100.	How will oyu test the stored procedure taking two parameters namely first name and last name returning full name? 
101.	How do you find the error, how can you know the number of rows effected by last SQL statement? 
102.	How can you get @@error and @@rowcount at the same time? 
103.	What are sub-queries? Give example? In which case sub-queries are not feasible? 
104.	What are the type of joins? When do we use Outer and Self joins? 
105.	Which virtual table does a trigger use? 
106.	How do you measure the performance of a stored procedure? 
107.	Questions regarding Raiseerror? 
108.	Questions on identity? 
109.	If there is failure during updation of certain rows, what will be the state? 

