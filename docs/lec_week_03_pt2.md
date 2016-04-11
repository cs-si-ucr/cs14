Exceptions
============

An **exception** is a circumstance that a program was not designed to handle. They are useful for when you need your program to detect and handle errors that may occur during program execution.

Here's an example of code without error checking:

```cpp
#include <iostream>
using namespace std;

int main()
{
  //Get height input
  int height = 0;
  cout << "Enter your height (in inches): ";
  cin >> height;

  //Return converted height input
  int feet = height / 12;
  int inches = height % 12;
  cout << "Your height is equivalant to: " << feet << " feet " << inches << " inches!" << endl;

  return 0;
}
```


Now let's do some test with some edge cases and see what the program outputs:

```cpp
//Normal Input
Enter your height (in inches): 75
Your height is equivalant to: 6 feet 3 inches!

//Zero Input
Enter your height (in inches): 0
Your height is equivalant to: 0 feet 0 inches!

//Negative Input
Enter your height (in inches): -54
Your height is equivalant to: -4 feet -6 inches!    //<------- Oh no!
```


So what most of you have been doing to avoid this error is a good implementation of branches!

```cpp
#include <iostream>
using namespace std;

int main()
{
  //Get height input
  int height = 0;
  cout << "Enter your height (in inches): ";
  cin >> height;

  //If the height is less than 0, output error message and return
  if(height < 0)
  {
    cout << "Error! Invalid height!" << endl;
    return 0;
  }

  //Return converted height input
  int feet = height / 12;
  int inches = height % 12;
  cout << "Your height is equivalant to: " << feet << " feet " << inches << " inches!" << endl;

  return 0;
}
```

Now let's test this new code with the same input:

```cpp
//Normal Input
Enter your height (in inches): 75
Your height is equivalant to: 6 feet 3 inches!

//Zero Input
Enter your height (in inches): 0
Your height is equivalant to: 0 feet 0 inches!

//Negative Input
Enter your height (in inches): -54
Error! Invalid height!                //<----- Much better~
```


A more sophisticated way of handling these errors are **exception-handling constructs**. Using these constructs allows us to keep error-checking code separate from our main code.


```cpp
//Exception handling construct

//... means normal code
//...
try
{
  //...

  //If error detected
  throw objectOfExceptionType;

  //...

}
catch (exceptionType execptionObject)
{
  //Handle exception, e.g., print message
}
//...
```

Exception constructs have three parts:

* A `try` block surrounds normal code, which is exited immediately if a throw statement executes.
* A `throw` statement appears within a try block; if reached, execution jumps immediately to the end of the try block. The code is written so only error situations lead to reaching a throw. The throw statement provides an object of a particular type, such as an object of type "runtime_error", which is a class defined in the **stdexcept** library. The statement is said to throw an exception of the particular type. A throw statement's syntax is similar to a return statement.
* A `catch` clause immediately follows a try block; if the catch was reached due to an exception thrown of the catch clause's parameter type, the clause executes. The clause is said to catch the thrown exception. A catch block is called a **handler** because it handles an exception.



Here's the earlier program using exception-handling constructs. Notice that the normal code flow is not obscured by error-checking/handling if-else statements.

```cpp
#include <iostream>
#include <stdexcept>  //Exception class
using namespace std;

int main()
{
  //Get height input
  int height = 0;

  try
  {
    //Get input
    cout << "Enter your height (in inches): ";
    cin >> height;

    if(height < 0)
    {
      throw runtime_error("Error! Invalid height!");
    }

    //Return converted height input
    int feet = height / 12;
    int inches = height % 12;
    cout << "Your height is equivalant to: " << feet << " feet " << inches << " inches!" << endl;
  }
  catch(runtime_error &excpt)
  {
    //Print error message passed by throw statement
    cout << excpt.what() << endl;
  }

  return 0;
}
```
```cpp
Output:
//Normal Input
Enter your height (in inches): 75
Your height is equivalant to: 6 feet 3 inches!

//Zero Input
Enter your height (in inches): 0
Your height is equivalant to: 0 feet 0 inches!

//Negative Input
Enter your height (in inches): -54
Error! Invalid height!              

```

Exceptions with functions
-----------------

Now you may be thinking, why even use exceptions?


![alt text](http://i.imgur.com/A62vCJ8.jpg?fb)


Well, the power of exceptions becomes clearer when used within a function. If an exception is thrown within a function and not caught within that function, then the function is immediately exited and the calling function is checked for a handler, and so on up the function call hierarchy.

Here's an expanded program where we utilize functions with execptions:

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

void getHeight(int & feet, int & inches)
{
   int height = 0; // User defined weight

   // Get user data
   cout << "Enter height (in inches): ";
   cin >> height;

   // Error checking, non-negative weight
   if (height < 0)
   {
      throw runtime_error("Error! Invalid height!");
   }

   //Calculate conversions
   feet = height / 12;
   inches = height % 12;

   return;
}

void getWeight(double & kilograms)
{
  int weight; // User defined weight

  //Get user Data
  cout << "Enter weight (in pounds): ";
  cin >> weight;

  if (weight < 0)
  {
      throw runtime_error("Error! Invalid weight!");
  }

  //Calculate conversions
  kilograms = weight / 0.453592;

  return;
}

int main()
{
  int feet, inches = 0;
  double kilograms = 0;

  try
  {
      //Get user data
      getHeight(feet, inches);
      getWeight(kilograms);

      cout << "Your height is equivalant to: " << feet << " feet " << inches << " inches!" << endl
           << "Your weight is equivalant to: " << kilograms << " kilograms!" << endl;
  }
  catch (runtime_error & excpt)
  {
      cout << excpt.what() << endl;
      cout << "Cannot compute info." << endl;
  }

  return 0;
}
```

In the code above we added a part to take in the user's weight. We then separated the user input into two different functions, each throwing their own exception. Now let's look at the code output:

```cpp
//Valid input
Enter height (in inches): 75
Enter weight (in pounds): 150
Your height is equivalant to: 6 feet 3 inches!
Your weight is equivalant to: 330.694 kilograms!

//Invalid height
Enter height (in inches): -55
Error! Invalid height!
Cannot compute info.

//Invalid weight
Enter height (in inches): 75
Enter weight (in pounds): -100
Error! Invalid weight!
Cannot compute info.
```


Multiple Exceptions
-----------------------------

>> But wait....there's more!...


Multiple handlers (i.e., catch expressions) can be chained; each one with a different parameter type. Only the handler whose argument type matches the type of the exception specified in the throw statement is executed.


```cpp
Exception handling using multiple handlers:

...
try
{
  ...
  throw objectOfExceptionType1;
  ...
  throw objectOfExceptionType2;
  ...
  throw objectOfExceptionType3;
  ...
}
catch (excptType1 & exceptObj1)
{
  //Handle type1
}
catch (excptType2 & exceptObj2)
{
  //Handle type2
}
catch (...)
{
  //Default handler. Catches all other objects (e.g. type3)
}
...//Execution continues
```

One thing to note is that if exceptObj2 is a subclass of exceptObj1, then objectOfExceptionType2 will always be caught by the first catch exception. A _**common error**_ is to place a catch block intended to handle exceptions of a base class before catch blocks intended to handle exceptions of a derived class, preventing the latter from ever executing.


Here's an example of using multiple handles. Note that exceptions can also be nested!

```cpp
#include <iostream>
#include <vector>
#include <stdexcept>
using namespace std;

int main()
{
  vector<int> v(10);
  int input = 0;
  int secondInput = 0;
  int thirdInput = 0;

  try
  {
      //Try getting a positive number. If a negative number is entered,
      //it will throw an exception but still continue to the code after the catch
      try
      {
        cout << "Enter a positive number: ";
        cin >> input;

        if(input < 0)
        {
          throw logic_error("input variable is invalid!");
        }
      }
      catch (logic_error & excpt)
      {
          cout << "Logic error!: " << excpt.what() << endl;
      }

      //Get negative number from user
      cout << "Enter a negative number: ";
      cin >> secondInput;

      if(secondInput > 0)
      {
        throw runtime_error("Second input is not a negative number!");
      }

      //Get 0 from user
      cout << "Enter 0: ";
      cin >> thirdInput;

      if(thirdInput != 0)
      {
        throw -1;
      }

      //Attempt to access an out-of-range index
      cout << v.at(20) << endl; //This will throw an out-of-range exception

  }
  catch (out_of_range & excpt)
  {
      cout << "Out of range error!: " << excpt.what() << endl;
  }
  catch (runtime_error & excpt)
  {
      cout << "Runtime error!: " << excpt.what() << endl;
  }
  catch (...)
  {
      cout << "Non-zero error!: User did not input a 0!" << endl;
  }

  return 0;
}
```

```cpp
Output:
//Valid inputs
Enter a positive number: 1
Enter a negative number: -1
Enter 0: 0
Out of range error!: vector::_M_range_check

//Invalid first input
Enter a positive number: -1
Logic error!: input variable is invalid!    //<---- Note that the program still continues
Enter a negative number: -1
Enter 0: 0
Out of range error!: vector::_M_range_check

//Invalid second input
Enter a positive number: 1
Enter a negative number: 1
Runtime error!: Second input is not a negative number!

//Invalid third input
Enter a positive number: 1
Enter a negative number: -1
Enter 0: 9999
Non-zero error!: User did not input a 0!
```
