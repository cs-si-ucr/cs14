Lab 3: Templates and Exceptions
===================================

Exercise 1 - Queue with two Stacks
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

Exercise 1.1 - Template Queue
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
Exercise 1.2 - Exceptions
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
