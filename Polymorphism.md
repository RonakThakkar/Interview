# Polymorphism

When a message can be processed in different ways is called polymorphism. Polymorphism means many forms.
  
Polymorphism is one of the fundamental concepts of OOP. 
  
Polymorphism provides following features:  
•	It allows you to invoke methods of derived class through base class reference during runtime. 
•	It has the ability for classes to provide different implementations of methods that are called through the same name.
Polymorphism is of two types:  
1.	Compile time polymorphism/Overloading
2.	Runtime polymorphism/Overriding
Compile Time Polymorphism 
  
Compile time polymorphism is method and operators overloading. It is also called early binding. 
  
In method overloading method performs the different task at the different input parameters. 
  
Runtime Time Polymorphism
  
Runtime time polymorphism is done using inheritance and virtual functions. Method overriding is called runtime polymorphism. It is also called late binding. 
  
When overriding a method, you change the behavior of the method for the derived class.  Overloading a method simply involves having another method with the same prototype. 
  
Caution: Don't confused method overloading with method overriding, they are different, unrelated concepts. But they sound similar. 
  
Method overloading has nothing to do with inheritance or virtual methods. 
  
Following are examples of methods having different overloads:
  
void area(int side); 
void area(int l, int b); 
void area(float radius); 
  
Practical example of Method Overloading (Compile Time Polymorphism) 
  
using System; 
  
namespace method_overloading 
{ 
    class Program 
    { 
        public class Print 
        { 
            
            public void display(string name) 
            { 
                Console.WriteLine("Your name is : " + name); 
            } 
  
            public void display(int age, float marks) 
            { 
                Console.WriteLine("Your age is : " + age); 
                Console.WriteLine("Your marks are :" + marks); 
            } 
        } 
        
        static void Main(string[] args) 
        { 
  
            Print obj = new Print(); 
            obj.display("George"); 
            obj.display(34, 76.50f); 
            Console.ReadLine(); 
        } 
    } 
} 


Real time example

public abstract class Asset
    {
        #region Abstract Property
        private bool _isLoaded;
        private int _securityID;

        #endregion

        #region Abstract Property

            /// <summary>
            /// Get/Set the boolean value indicating whether the security is loaded from DB or not.
            /// </summary>
            public bool IsLoaded
            {
                get
                {
                    return _isLoaded; 
                }
                internal set
                {
                    _isLoaded = value;
                }
            }


            /// <summary>
            /// Get Security ID.
            /// </summary>
            public int SecurityID
            {
                get { return _securityID; }
                internal set { _securityID = value; }
            }
        #endregion

        #region Abstract Methods
        /// <summary>
            /// Save the asset details
            /// </summary>
            /// <returns></returns>
            internal  abstract bool Save();
        #endregion

        #region Static Methods
        
            internal static Asset GetAsset(AppDataTypes.SecurityType type , int securityID)
            {
                try
                {
                    Asset asset = null;
                    switch (type)
                    {
                        case AppDataTypes.SecurityType.FixedIncome:
                            asset = new FixedIncome(securityID);
                            break;
                        case AppDataTypes.SecurityType.Equity:
                            asset = new Equity(securityID);
                            break;
                        case AppDataTypes.SecurityType.Warrant:
                            asset = new Warrant (securityID);
                            break;
                        case AppDataTypes.SecurityType.CashBalance:
                            break;
                    }
                    return asset;
                }
                catch (Exception ex)
                {
                    throw ex;
                }
            }
        #endregion

    }

