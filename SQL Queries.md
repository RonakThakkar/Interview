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
