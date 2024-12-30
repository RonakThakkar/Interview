# Best Practices

## Async Programming Model

### I/O VS CPU Bound
* For I/O-bound code, you await an operation that returns a Task or Task<T> inside of an async method
  * Making an API Calls
  * Doing a database operation
  * Uploading a file   
* For CPU-bound code, you await an operation that is started on a background thread with the Task.Run method.


### Multiple async calls

**Task.WhenAll**

https://dev.to/serhii_korol_ab7776c50dba/the-elegant-way-to-await-multiple-tasks-in-net-11pl
https://code-maze.com/csharp-execute-multiple-tasks-asynchronously/
https://www.roundthecode.com/dotnet-tutorials/how-to-use-csharp-async-await-api-calls-stop-blocking

**Task.WhenAny**

https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/start-multiple-async-tasks-and-process-them-as-they-complete


### Different Implementatin of async model
https://blog.stephencleary.com/2010/08/various-implementations-of-asynchronous.html

## Advanced .NET Pragramming
https://learn.microsoft.com/en-us/dotnet/navigate/advanced-programming/
