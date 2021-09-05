Delegates

A Delegate is a class. When you create an instance of it, you pass in the function name (as a parameter for the delegate's constructor) to which this delegate will refer.

Delegates are just function pointers, That is, they hold references to functions.
Delegates allows to invoke a function by its reference. A delegate can be used to call multiple functions.
 
Every delegate has a signature. i.e it has a return type and takes some parameter.

There are 3 steps in defining and using delegates.

1)	Declaration
2)	Instantiation
3)	Invocation

 
Call a Function directly - No Delegate
using System;
 
namespace Akadia.NoDelegate
{
    public class MyClass
    {
        public void Process()
        {
            Console.WriteLine("Process() begin");
            Console.WriteLine("Process() end");
        }
    }
 
    public class Test
    {
        static void Main(string[] args)
        {
            MyClass myClass = new MyClass();
            myClass.Process();
        }
    }
}
 
The very basic Delegate 
using System;

namespace Akadia.BasicDelegate
{
    // Declaration
    public delegate void SimpleDelegate();

    class TestDelegate
    {
        public static void MyFunc()
        {
            Console.WriteLine("I was called by delegate ...");
        }

        public static void Main()
        {
            // Instantiation
            SimpleDelegate simpleDelegate = new SimpleDelegate(MyFunc);

            // Invocation
            simpleDelegate();
        }
    }
}
Note : Here Delegate Declaration, Instantiation and Invocation are located in same Class file.
simpleDelegate and MyFunc should have similar signatures

Here simpleDelegate refers to MyFunc, in other words, MyFunc is registered to simpleDelegate. If you call simpleDelegate, MyFunc will be invoked. 
 
Advance Delegate
Calling Static Functions (A function located inside same Class where delegate is instantiated)
using System;

namespace Akadia.SimpleDelegate
{
    // Delegate Specification
    public class MyClass
    {
        // Declare a delegate that takes a single string parameter
        // and has no return type.
        public delegate void LogHandler(string message);

        // The use of the delegate is just like calling a function directly,
        // though we need to add a check to see if the delegate is null
        // (that is, not pointing to a function) before calling the function.
        public void Process(LogHandler logHandler)
        {
            if (logHandler != null)
            {
                logHandler("Process() begin");
            }

            if (logHandler != null)
            {
                logHandler ("Process() end");
            }
        }
    }

    // Test Application to use the defined Delegate
    public class TestApplication
    {
        // Static Function: To which is used in the Delegate. To call the Process()
        // function, we need to declare a logging function: Logger() that matches
        // the signature of the delegate.
        static void Logger(string s)
        {
            Console.WriteLine(s);
        }

        static void Main(string[] args)
        {
            MyClass myClass = new MyClass();

            // Crate an instance of the delegate, pointing to the logging function.
            // This delegate will then be passed to the Process() function.
            MyClass.LogHandler myLogger = new MyClass.LogHandler(Logger);
            myClass.Process(myLogger);
        }
    }
}
 
 
 
Advance Delegate
Calling Member Functions (A function located in some other class than the class in which  Delegate is instantiated)
using System;
using System.IO;

namespace Akadia.SimpleDelegate
{
    // Delegate Specification
    public class MyClass
    {
        // Declare a delegate that takes a single string parameter
        // and has no return type.
        public delegate void LogHandler(string message);

        // The use of the delegate is just like calling a function directly,
        // though we need to add a check to see if the delegate is null
        // (that is, not pointing to a function) before calling the function.
        public void Process(LogHandler logHandler)
        {
            if (logHandler != null)
            {
                logHandler("Process() begin");
            }

            if (logHandler != null)
            {
                logHandler ("Process() end");
            }
        }
    }

    

    // The FileLogger class merely encapsulates the file I/O
    public class FileLogger
    {
        FileStream fileStream;
        StreamWriter streamWriter;

        // Constructor
        public FileLogger(string filename)
        {
            fileStream = new FileStream(filename, FileMode.Create);
            streamWriter = new StreamWriter(fileStream);
        }

        // Member Function which is used in the Delegate
        public void Logger(string s)
        {
            streamWriter.WriteLine(s);
        }

        public void Close()
        {
            streamWriter.Close();
            fileStream.Close();
        }
    }

    // Main() is modified so that the delegate points to the Logger()
    // function on the fl instance of a FileLogger. When this delegate
    // is invoked from Process(), the member function is called and
    // the string is logged to the appropriate file.
    public class TestApplication
    {
        static void Main(string[] args)
        {
            FileLogger fl = new FileLogger("process.log");

            MyClass myClass = new MyClass();

            // Crate an instance of the delegate, pointing to the Logger()
            // function on the fl instance of a FileLogger.
            MyClass.LogHandler myLogger = new MyClass.LogHandler(fl.Logger);
            myClass.Process(myLogger);
            fl.Close();
        }
    }
}
 
Multicasting
using System;
using System.IO;

namespace Akadia.SimpleDelegate
{
    // Delegate Specification
    public class MyClass
    {
        // Declare a delegate that takes a single string parameter
        // and has no return type.
        public delegate void LogHandler(string message);

        // The use of the delegate is just like calling a function directly,
        // though we need to add a check to see if the delegate is null
        // (that is, not pointing to a function) before calling the function.
        public void Process(LogHandler logHandler)
        {
            if (logHandler != null)
            {
                logHandler("Process() begin");
            }

            if (logHandler != null)
            {
                logHandler ("Process() end");
            }
        }
    }

    
 
    // The FileLogger class merely encapsulates the file I/O
    public class FileLogger
    {
        FileStream fileStream;
        StreamWriter streamWriter;

        // Constructor
        public FileLogger(string filename)
        {
            fileStream = new FileStream(filename, FileMode.Create);
            streamWriter = new StreamWriter(fileStream);
        }

        // Member Function which is used in the Delegate
        public void Logger(string s)
        {
            streamWriter.WriteLine(s);
        }

        public void Close()
        {
            streamWriter.Close();
            fileStream.Close();
        }
    }

    // Test Application which calls both Delegates
    public class TestApplication
    {
        // Static Function which is used in the Delegate
        static void Logger(string s)
        {
            Console.WriteLine(s);
        }

        static void Main(string[] args)
        {
            FileLogger fl = new FileLogger("process.log");

            MyClass myClass = new MyClass();

            // Crate an instance of the delegates, pointing to the static
            // Logger() function defined in the TestApplication class and
            // then to member function on the fl instance of a FileLogger.
            MyClass.LogHandler myLogger = null;
            myLogger += new MyClass.LogHandler(Logger);
            myLogger += new MyClass.LogHandler(fl.Logger);

            myClass.Process(myLogger);
            fl.Close();
        }
    }
}
 
Simple Event
namespace Akadia.SimpleEvent
{
    /* ========= Publisher of the Event ============== */
    public class MyClass
    {
        // Define a delegate named LogHandler, which will encapsulate
        // any method that takes a string as the parameter and 
        returns no value
        public delegate void LogHandler(string message);
 
        // Define an Event based on the above Delegate
        public event LogHandler Log;
 
        // Instead of having the Process() function take a delegate
        // as a parameter, we've declared a Log event. Call the                                   
        Event,
        // using the OnXXXX Method, where XXXX is the name of the 
        Event.
        public void Process()
        {
            OnLog("Process() begin");
            OnLog("Process() end");
        }
 
        // By Default, create an OnXXXX Method, to call the Event
        protected void OnLog(string message)
        {
            if (Log != null)
            {
                Log(message);
            }
        }
    }
 
    // The FileLogger class merely encapsulates the file I/O
    public class FileLogger
    {
        FileStream fileStream;
        StreamWriter streamWriter;
 
        // Constructor
        public FileLogger(string filename)
        {
            fileStream = new FileStream(filename, FileMode.Create);
            streamWriter = new StreamWriter(fileStream);
        }
 
        // Member Function which is used in the Delegate
        public void Logger(string s)
        {
            streamWriter.WriteLine(s);
        }
 
        public void Close()
        {
            streamWriter.Close();
            fileStream.Close();
        }
    }
 
    /* ========= Subscriber of the Event ============== */
    // It's now easier and cleaner to merely add instances
    // of the delegate to the event, instead of having to
    // manage things ourselves
    public class TestApplication
    {
        static void Logger(string s)
        {
            Console.WriteLine(s);
        }
 
        static void Main(string[] args)
        {
            FileLogger fl = new FileLogger("process.log");
            MyClass myClass = new MyClass();
 
            // Subscribe the Functions Logger and fl.Logger
            myClass.Log += new MyClass.LogHandler(Logger);
            myClass.Log += new MyClass.LogHandler(fl.Logger);

            // The Event will now be triggered in the Process() Method
            myClass.Process();
 
            fl.Close();
        }
    }
}
