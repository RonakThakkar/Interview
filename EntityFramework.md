# Entity Framework

How to protect SQL Injection in entity framework - generate parameterized sql commands

How do you improve performance of query
* Fetch only needed fields
* Implement paging to fetch only few set of records
* Disable entity tracking

Eager Loading

* Eager loading is achieved using Include method.
* Left outer join query is created.
* Include can take string  / Lambda expressions. ctx.Students.Include(s => s.Departments)
* Load Multiple Entities - ctx.Students.Include("Department.Teachers")

How to implement CRUD operations on disconnected entities

How to add TenantId filter in each query executed agianst database

## Queries


### Get all employees in city=pune sort by employee name

**Query Syntax**

var employees = from emp in ctx.Employees
                where emp.city = "pune"
                orderby emp.FirstName, emp.LastName
                select emp;

**Method Syntax**

var employees = ctx.Employees.Where(emp => emp.City == "pune")
                             .OrderBy(emp => emp.FirstName)
                             .ThenBy(emp => emp.LastName);


### Extend above query and select only required fields.

**Query Syntax**

var employees = from emp in ctx.Employees
                where emp.city = "pune"
                select new { 
                  emp.FirstName, 
                  emp.LastName
                };

**Method Syntax**

var employees = ctx.Employees
                .Where(emp => emp.City == "pune")
                .Select(emp => {
                  emp.FirstName,
                  emp.LastName
                });


### Get employee count per city.

**Query Syntax**

var employeeCount = from emp in ctx.Employees
                    group emp by emp.City into cityGroup
                    select new { 
                      City = cityGroup.Key, 
                      EmployeeCount = cityGroup.Count()
                    };

**Method Syntax**

var employeeCount = ctx.Employees.GroupBy(q => q.City)
                    .Select(cityGroup => {
                      City = cityGroup.Key,
                      EmployeeCount = cityGroup.Count()
                    });
