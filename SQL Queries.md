Useful SQL Queries

Select * into tempdb.dbo.customers from northwind.dbo.customers
Servername.Databasename.Ownername.Objectname

Select top 5 * form northwind.dbo.employees order by employee_id

select * from tbm_device order by CAST(devicename_txt as int(2))
Note – When devicename_txt is varchar field.

Select * from master.dbo.sysobjects where type = ‘S’.
‘S’ – System Table.
‘U’ – User Table.
‘P’ – Stored Procedure
‘V’ – Views.
‘X’ – Extended stored procedures.

Select * from master.dbo.sysobjects where type=’P’ ans category=0.

Select * from master.dbo.sysindexes.

Select * from master.dbo.sysusers.

Retrieving Column Names of a table.
Syscolumns – related to table and view.
select * from master.dbo.syscolumns where id in(select id from master.dbo.sysobjects where type='u' and name = 'customers')

Query returns complete Stored procedure.
Syscomments -  related to view, trigger, stored procedure.
select text from intellichaiseworking.dbo.syscomments where id in(select id from intellichaiseworking.dbo.sysobjects where type='P' and category='0' and name='SP_Advmail')

using bcp we can store (transfert) this data into txt or excel file to front end.

Example.
Bcp “select * from employees”  queryout “c:\ronak.txt” –c –Spc-p3-162 –Usa –P

Note – sysobjects, sysindexes and all discussed above are related to Database. I.e exists 
different for different databases.
sysjobs and others related to jobs is single for a server.

Related to jobs.
select * from msdb.dbo.sysjobservers
select * from msdb.dbo.sysjobs
select * from msdb.dbo.sysjobschedules where job_id in(select job_id from msdb.dbo.sysjobs where name='SendWeatherMail')
select * from msdb.dbo.sysjobsteps where job_id in(select job_id from msdb.dbo.sysjobs where name='intellichaise database backup')

sysdatabase table resides in master database.
select * from master.dbo.sysdatabases.


useful system stored procedures
sp_databases
master.dbo.sp_tables
sp_columns employees
sp_help employees
msdb.dbo.sp_help_job
msdb.dbo.sp_helpindex
sp_executesql
sp_msgetversion
select @@version
sp_mshelpcolumns ‘authors
sp_msforeachdb
sp_msforeachtable
sp_mshelptype
sp_mstablespace ‘authors’
sp_who

master..xp_fixeddrives  or master.dbo.fixeddrives
master..xp_cmdshell 'dir c:\*.txt'
master..xp_fileexist 'c:\ronak.txt', @exists output
master..xp_dirtree ‘e:\ronak\
master..xp_availablemedia
master..xp_getnetname
master..xp_enumdsn
master..xp_enum_oledb_providers
master..xp_enumcodepages
master..enumerrorlogs.
master..xp_getnetname
master..readerrorlog
master..xp_subdirs
master..xp_regdeletekey
master..xp_regdeletevalue
master..xp_regwrite
master.xp_regread

Search openxml in sql help.

A Sample to use Stored Procedures 
USE pubs
GO
EXEC sp_columns_rowset 'authors'
GO
USE Master
GO
This will execute stored procedure in pubs database and return to master database.


bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c

EXEC master..xp_cmdshell 'bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c'

EXEC master..xp_cmdshell 'bcp "select * from tb_defaults" queryout c:\ronaktest1.xls /Usa /P /F1  /t"|" /m10 /c





Useful SQL Queries

Select * into tempdb.dbo.customers from northwind.dbo.customers
Servername.Databasename.Ownername.Objectname

Select top 5 * form northwind.dbo.employees order by employee_id

select * from tbm_device order by CAST(devicename_txt as int(2))
Note – When devicename_txt is varchar field.

Select * from master.dbo.sysobjects where type = ‘S’.
‘S’ – System Table.
‘U’ – User Table.
‘P’ – Stored Procedure
‘V’ – Views.
‘X’ – Extended stored procedures.

Select * from master.dbo.sysobjects where type=’P’ ans category=0.

Select * from master.dbo.sysindexes.

Select * from master.dbo.sysusers.

Retrieving Column Names of a table.
Syscolumns – related to table and view.
select * from master.dbo.syscolumns where id in(select id from master.dbo.sysobjects where type='u' and name = 'customers')

Query returns complete Stored procedure.
Syscomments -  related to view, trigger, stored procedure.
select text from intellichaiseworking.dbo.syscomments where id in(select id from intellichaiseworking.dbo.sysobjects where type='P' and category='0' and name='SP_Advmail')

using bcp we can store (transfert) this data into txt or excel file to front end.

Example.
Bcp “select * from employees”  queryout “c:\ronak.txt” –c –Spc-p3-162 –Usa –P

Note – sysobjects, sysindexes and all discussed above are related to Database. I.e exists 
different for different databases.
sysjobs and others related to jobs is single for a server.

Related to jobs.
select * from msdb.dbo.sysjobservers
select * from msdb.dbo.sysjobs
select * from msdb.dbo.sysjobschedules where job_id in(select job_id from msdb.dbo.sysjobs where name='SendWeatherMail')
select * from msdb.dbo.sysjobsteps where job_id in(select job_id from msdb.dbo.sysjobs where name='intellichaise database backup')

sysdatabase table resides in master database.
select * from master.dbo.sysdatabases.


useful system stored procedures
sp_databases
master.dbo.sp_tables
sp_columns employees
sp_help employees
msdb.dbo.sp_help_job
msdb.dbo.sp_helpindex
sp_executesql
sp_msgetversion
select @@version
sp_mshelpcolumns ‘authors
sp_msforeachdb
sp_msforeachtable
sp_mshelptype
sp_mstablespace ‘authors’
sp_who

master..xp_fixeddrives  or master.dbo.fixeddrives
master..xp_cmdshell 'dir c:\*.txt'
master..xp_fileexist 'c:\ronak.txt', @exists output
master..xp_dirtree ‘e:\ronak\
master..xp_availablemedia
master..xp_getnetname
master..xp_enumdsn
master..xp_enum_oledb_providers
master..xp_enumcodepages
master..enumerrorlogs.
master..xp_getnetname
master..readerrorlog
master..xp_subdirs
master..xp_regdeletekey
master..xp_regdeletevalue
master..xp_regwrite
master.xp_regread

Search openxml in sql help.








A Sample to use Stored Procedures 
USE pubs
GO
EXEC sp_columns_rowset 'authors'
GO
USE Master
GO
This will execute stored procedure in pubs database and return to master database.


bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c

EXEC master..xp_cmdshell 'bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c'

EXEC master..xp_cmdshell 'bcp "select * from tb_defaults" queryout c:\ronaktest1.xls /Usa /P /F1  /t"|" /m10 /c



select * from dup_authors group by au_lname, au_fname, city, state having count(*) > 1

select * into #BackUpTableAuthors from dup_authors 
select * into dup_authors from #BackUpTableAuthors

select * from #BackUpTableAuthors
select * from #holding 



-- Trunctae and Copy
select distinct * into #holding from dup_authors
truncate table dup_authors
insert into dup_authors select * from #holding
drop table #holding




-- Raname and Copy

-- Rename Table
sp_rename 'dup_authors', 'temp_dup_authors'

-- Select distinct records from original temporary table and create a new table with original table name
select distinct *
into dup_authors
from temp_dup_authors

-- drop temporary table
drop table temp_dup_authors
select * from dup_authors


-- Set Rowcount for duplicate records to 1 and delete duplicate record.
set rowcount 1
delete from dup_authors where au_lname = 'thakkar'
set rowcount 0


-- Move distinct duplicate records to temporay table, delete and copy 
select * into dup_authors_HoldValues from dup_authors group by au_lname, au_fname, city, state having count(*) > 1
delete dup_authors from dup_authors, dup_authors_HoldValues where dup_authors.au_lname = dup_authors_HoldValues.au_lname and dup_authors.au_fname = dup_authors_HoldValues.au_fname
insert into dup_authors select * from dup_authors_HoldValues
drop table dup_authors_HoldValues


select * from EmployeeSalary
-- With ID Generated Column
-- Getting first records from table
select top 1 * from EmployeeSalary

-- Getting Last records from table
select top 1 * from EmployeeSalary order by ID DESC
select top 1 * from EmployeeSalary WHERE ID = (SELECT COUNT(*) FROM EmployeeSalary )
select top 1 * from EmployeeSalary WHERE ID = (SELECT MAX(ID) FROM EmployeeSalary )

-- Getting second last record.
select top 1 * from EmployeeSalary where ID <> (SELECT MAX(ID) FROM EmployeeSalary) order by ID desc

-- Getting Nth record last record

select top 1 * from dup_authors_temp where id not in (select top (n-1) * from dup_authors order by id desc) order by id desc

select top 1 * from (select top n * from dup_authors order by id desc)

select top n * into #temp from dup_authors order by id desc
select top 1 * from #temp order by id asc

n=3
select top 1 * from dup_authors where ID not in ( select top 2 ID from dup_authors order by ID desc ) order by ID desc

select top 1 * from (select top 3 * from dup_authors order by id desc)

-- Nice way -- 
select top 3 * into #Temp1 from dup_authors order by id desc
select top 1 * from #Temp1 order by id asc

-- One Way
select top 3 * into #Temp1 from EmployeeSalary
select top 2 * into #Temp2 from EmployeeSalary
select * from #Temp1 T1 where not exists (select 1 from #Temp2 T2 where T1.name = T2.name)

-- Other Way
select * from (select top 3 * from EmployeeSalary) T1 where not exists (select 1 from (select top 2 * from EmployeeSalary) T2 where T1.name = T2.name)



-- Highest salary
Select * from EmployeeSalary where salary = (Select max(Salary) from EmployeeSalary)

-- Second Highest salary
Select top 1 * from EmployeeSalary where salary != (Select max(Salary) from EmployeeSalary) order by salary desc

DECLARE @NumberVar int
SET @NumberVar = 2
Select * From EmployeeSalary E1 Where
    (@NumberVar-1) = (Select Count(Distinct(E2.Salary)) From EmployeeSalary E2 Where
		E2.Salary > E1.Salary)

-- Hint to use Database and Table name as variable.
DECLARE @SQL VARCHAR(1000)
DECLARE @db VARCHAR(50)
SET @db = 'NSS_DATABASE'
DECLARE @table VARCHAR(50)
SET @table = 'GLOBALID'
SET @SQL = 'SELECT * FROM ' + @db + '.dbo.' + @table
EXEC(@SQL)


bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c

EXEC master..xp_cmdshell 'bcp "select * from IntelliChaiseWorking..TBM_Report" queryout "c:\ronaktest.xls" /Spc-p3-162 /Usa /P /F1 /c'

EXEC master..xp_cmdshell 'bcp "select * from tb_defaults" queryout c:\ronaktest1.xls /Usa /P /F1  /t"|" /m10 /c

