
Lab 3: Templates and Exceptions
===================================
[queue-slides]:https://d1b10bmlvqabco.cloudfront.net/attach/j129btc6ipp515/h7ks2ibk8jg6s3/j1hydurqd650/Queues.pdf "Miller's queue lecture slides"

Exercise 1- Circular int Queue
----------
For this exercise you will be implementing an array-based queue with circular functionality like the one in Professor Miller's [slides][queue-slides]. Implement the functionality in a class called 'Queue' and include the following functions:
```cpp
Queue();
void enqueue(int n);
void dequeue();
int getFirst();
int getLast();
};
```
When creating the underlying array, feel free to set a max size of the array like so:
`int arr[10]; // Max Queue size`


Exercise 1.1. Exceptions
----------
Using what you have learned about exceptions, throw an exception when the user tries to call the `enqueue(int n);`
function when the queue has hit its capacity (max size) or when the user tries to call `getFirst();` or `getLast();`
on an empty queue.

Exercise 2 - Iterators 
-----------
**Definition:** An iterator is any object that, pointing to some element in a range
of elements (such as an array or a container), 
has the ability to iterate through the elements of that range using a set of operators (with at least the 
increment `++` and dereference `*` operators). The most obvious form of iterator is a pointer: A pointer can 
point to elements in an array, and can iterate through them using the increment operator `++`. But other kinds 
of iterators are possible. For example, each container type (such as a list) has a specific iterator type designed 
to iterate through its elements. Notice that while a pointer is a form of iterator, not all iterators have the same 
functionality of pointers.
We will learn about the built-in iterator class for the C++ list class. You can think of this iterator as a super-powered
`Node* ptr` which will automatically switch to the next node if you call ptr++. You can even iterate backwards using `ptr--;`
Wow! Let's say you have a list called `myList`.
You can call public member functions: `myList.begin()` and `myList.end()`.` myList.begin()` will return an iterator that points to the 
list's `HEAD->next`. `myList.end();` returns an iterator that points to `TAIL`! Note: This iterator does NOT point to the last value in
your list!

Here is an example of how you print the first element in myList using an iterator:
```cpp
#include <iostream>
#include <list>
using namespace std;
int main()
{
    list<char> myList;
    myList.push_back('H');
    
    list<char>::iterator iter;
    iter = myList.begin();
    cout << *iter << endl;
    return 0;
}
```
Q1) What do you think is the output?
Q2) Can you find 2 errors in the following code?

```cpp
#include <iostream>
#include <list>
using namespace std;
int main()
{
    list<char> myList;
    myList.push_back('H');
    
    list<char>::iterator iter;
    iter = myList.end();
    cout << iter << endl;
    return 0;
}
```
And this is how you "iterate" (use this word!) through a list using a for loop and iterators:
```cpp
for (list<char>::iterator it = myList.begin(); it != myList.end(); ++it) {
        cout << ' ' << *it;
    }
```

Challenge1: Come up with code (just the main function) which will fill a list with integers 1 through 10.
    Then, use ITERATORS to print the list in reverse order, separated by spaces!
The list also have public member functions myList.remove(5). This automatically searches for the number
and removes it from the list. But there is a function myList.insert(iter, 2), which does not find a number
for you, you must find it with an iterator and then pass in the iterator. The insert function will then
insert the value passed in at the position where the iterator points to, moving everthing else over.
Challenge2) Write out only the lines of code needed to get the myList, that is already filled with
numbers 1 through 10, and insert a ZERO after the FIVE.




Exercise 3 - Queue with two Stacks
----------

Your task is to implement a class called `Queue` using two stacks `std::stack`.

Public Methods
```cpp
Queue(int c = 256) {cap = c; sz = 0}
void printAll()
void push_q(data_type t)
data_type pop_q() // removes and returns the top element
bool isEmpty() 
```

Private Data Fields
```cpp
stack<data_type> s1;
stack<data_type> s2;
unsigned sz;  // the number of elements currently being used in Queue
unsigned cap; // the size of Queue
```

Exercise 3.1 - Template Queue
----------

Take your completed queue class and create a queue template to allow your class to have members that use template parameters as types.
`Queue` should now become:
```cpp
template<typename T>
class Queue
{
	public:
	    // ...	
	private: 
        // ...
};
```
and `printAll()` should now become:
```cpp
template<typename T>
void Queue<T>::printAll()
{
    // ...
}
```
Exercise 3.2 - Exceptions
----------

Add an exception handler that throws a `runtime_error` object in the `pop_q()` and `push_q()` function that is caught and handled in the main program. 
Determine what conditions in `pop_q()` and `push_q` would cause an exception to be thrown.
When the exception is caught in the main program, print the error message passed by throw statement and continue the program. Do not terminate. 

`main` should look like the following:
```cpp
int main()
{
  	string s = "abcde";
    Queue<char> q(s.size());
    try 
    {
        // ...
    }
    catch ( ... )
    {
       // ...
    }
    
    return 0;
}
```

Example
----------
Exceptions are not implemented in this example.

```cpp
int main()
{
	string s = "abcde";
	Queue<char> q(s.size());
	for(unsigned i = 0; i < s.size(); ++i)
	{
		q.push_q(s.at(i));
	}
	q.printAll();

	for(unsigned i = 0; i < 3; ++i)
	{
		q.pop_q();
		q.printAll();
	}
	q.push_q('x');
	q.printAll();
	q.push_q('y');
	q.printAll();
    
    return 0;
}
```

Output (first element is the top element): 
```cpp
a b c d e 
b c d e 
c d e 
d e 
d e x 
d e x y 
```
