Objects are the building blocks of OOP.
Object is an instance of a class.
Objects are commenly defined as Data structures that encapsulate behavior and data in a programmed unit. This leads to the concept of encapsulation.

Encapsulaiton
Consider class Math with 2 private variables a, b and a function CalculateSum which will sum value in variables a and b. Create an object of class Maths, Set value for variable a and b. Now funciton CalculateSum will automatically use this value of variable a and b to calcualte sum. You do not need to explicitly pass value for summation. This is what is encapsulation.

Data Hiding
Different objects of same class are unique. Consider 2 object of Math class. Value of x and y variable for both object can be different. Moreover value of this variables in one object will be hidden from other.


Inheritance
Leads to the concept of generelization and specilization
generelization - > abstract classess -> defines common state and behaviors.
specilization -> derived classess -> define special state and behaviors.

Common example
Webform : System.web.ui.page

Real world example: Ensure that only logged in user can access the web pages of applicaiton
Every WEb form class is derived from Base class. This base class will check for authentication of user. If not redirect to Login page.