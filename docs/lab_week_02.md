Lab 2: The Standard Template Library
===================================
[std-vector]:http://en.cppreference.com/w/cpp/container/vector "cppreference for std::vector"
[std-list]:http://en.cppreference.com/w/cpp/container/list "cppreference for std::list"
[std-swap]:http://en.cppreference.com/w/cpp/algorithm/swap "cppreference for std::swap"
[std-sort]:http://en.cppreference.com/w/cpp/algorithm/sort "cppreference for std::sort"
[STL-beautiful]:http://www.bfilipek.com/2014/12/top-5-beautiful-c-std-algorithms.html "Cool examples that showcase use of the STL"
[iterator-categories]:http://en.cppreference.com/w/cpp/iterator#Iterator_categories
[Vec-iterator-Image]:http://upload.cppreference.com/mwiki/images/1/1b/range-begin-end.svg
[std-copy_if]:http://en.cppreference.com/w/cpp/algorithm/copy  "cppreference for std::copy_if"
[cpp-compare]:http://en.cppreference.com/w/cpp/concept/Compare "cppreference for the C++ concept of an object of type Compare"
[std-distance]:http://en.cppreference.com/w/cpp/iterator/distance "cppreference for std::distance"
[std-inplace_merge]:http://en.cppreference.com/w/cpp/algorithm/inplace_merge "cppreference for std::inplace_merge"

[STL-video]:https://channel9.msdn.com/Series/C9-Lectures-Stephan-T-Lavavej-Standard-Template-Library-STL-/C9-Lectures-Introduction-to-STL-with-Stephan-T-Lavavej  "Lecture that introduces STL"


The Standard Template Library, or the **STL** for short, is
a library that provides many reusable (or generic) algorithms and data structures that programmers would otherwise have to reimplement themselves.

Some of these algorithms range from simple algorithms such
as [`std::swap`][std-swap] to the more complex [`std::sort`][std-sort].

The motivation for learning and mastering the STL is to write [code that is clear and concise][STL-beautiful].

Iterators
---------
Probably the most important and inescapable concept in the
STL is the types we call iterators.

Iterators are used to generalize the iterator over an STL container (or your own containers that implement iterators).

The easiest way to think about iterators is to think of them as fancy pointers (again, this conceptual model works for 80% of use cases - it's not entirely correct).

*"Enough talk, show me the code!"* Here's how you can iterate through a vector using iterators!
```cpp
vector<int> vec {1, 2, 3};
vector<int>::iterator vec_iterator = vec.begin();

// go through the vector until we hit vec.end()
while(vec_iterator != vec.end()) {
    cout << *vec_iterator << ' ';
    vec_iterator++; //move the iterator up one
}
// Outputs "1 2 3 "
```
Note the `vec.begin()` and `vec.end()` calls in the above
code block. Both of these return an iterator to different
positions in the vector container. Both also return an
iterator of type `vector<int>::iterator`.

`vec.begin()` returns an iterator to beginning of `vec`. However, `vec.end()` returns an iterator to the element **one past** the last element.

This is pictured below (image from en.cppreference.com)
![vector::begin and vector::end diagram][Vec-iterator-Image]


A lot of algorithms in the STL, including `std::sort`
expect iterators as arguments. [(and usually specific types of iterators)][iterator-categories]

One of the function prototypes for [`std::sort`][std-sort] looks
something like this:
```cpp
template<typename RandomIt>
void sort(Iterator first, Iterator last);
```
As long as we provide the sort function valid iterators, it will sort
the elements within the range [first, last).

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
int main() {
    vector<int> vec {42, 8, 3};

    // sort all of the elements in vec in ascending order
    sort(vec.begin(), vec.end());

    /*
        We can use auto to omit the type
        on the left-hand side in C++11!

        Also, this is a way to iterate through a
        vector using iterators with a for-loop!
    */
    for(auto vec_iter = vec.begin(); vec_iter != vec.end(); vec_iter++){
        cout << *vec_iter << ' ';
    }
}
```
`
**Try it yourself - before compiling guess what the above program outputs.**


That's cool and all, but what if we want to sort the
container in descending order: function objects come
to the rescue!

Function Objects
----------------
Back in CS12, you learned that you can **overload**
special operators while defining classes. The prototype
of a method of a rational number class which overloads the
`+` operator may look like this (assume the `gcd` function is defined):

```cpp
bool operator+(const Rational & other) {
    int new_denom = gcd(this -> denom, other.denom);
    int this_multipler = new_denom/(this -> denom);
    int other_multipler = new_denom/(other.denom);
    int new_numer = this_multipler  * this -> numer +
                    other_multipler * other.numer;
    return Rational(new_numer, new_denom);
}
```
You can also overload the function call operator by
defining a function with the function name `operator()`.

e.g.
```cpp
#include <iostream>
using namespace std;

class Counter {
    public:
        Counter() :count(0) {}
        Counter(int count) : count(count) {}
        void operator() () {
            ++count;
        }
        int get_count() {
            return count;
        }
    private:
        int count;
};
int main() {
    Counter count;
    count();
    count();
    cout << count.get_count() << endl;
}
```
**Try it yourself - before compiling guess what the above program outputs.**


Overloading the function call operator automatically makes the
class a "function object". This becomes useful in a number of
STL algorithms. Some of the algorithms include [`std::sort`][std-sort]
and [`std::copy_if`][std-copy_if]. The most common types of
function objects that these algorithms accept as input are
[comparison function objects][cpp-compare] which return
true if the first argument is *considered* less than the second and
a unary predicate which returns true if it satisfies some condition.

```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <list>
using namespace std;

class SortGreater {
    public:
        bool operator() (const int & a, const int & b ) const {
            return a > b;
        }
};

class IsEven {
    public:
        bool operator() (const int & x) const {
            return x % 2 == 0;
        }
};

int main() {
    vector<int> from_vector {1, 2, 3, 4};
    list<int> to_list(2);

    sort(from_vector.begin(), from_vector.end(), SortGreater());
    for (int elem : from_vector) {
        cout << elem << ' ';
    }
    cout << endl;

    copy_if(from_vector.begin(), from_vector.end(), to_list.begin(), IsEven());

    for (int elem : to_list) {
        cout << elem << ' ';
    }
}
```
**Try it yourself - before compiling guess what the above program outputs.**

Exercise 1 - Reverse Polish Notation
----------
**Reverse Polish notation (RPN)** is a mathematical notation in which every operator follows all of its operands. It is also known as postfix notation and does not need any parentheses as long as each operator has a fixed number of operands.


In reverse Polish notation the operators follow their operands; for instance, to add 3 and 4, one would write "3 4 +" rather than "3 + 4". If there are multiple operations, the operator is given immediately after its second operand; so the expression written "3 − 4 + 5" in conventional notation would be written "3 4 − 5 +" in RPN: 4 is first subtracted from 3, then 5 added to it.


An advantage of RPN is that it removes the need for parentheses that are required by infix. While "3 − 4 * 5" can also be written "3 − (4 * 5)", that means something quite different from "(3 − 4) * 5". In postfix, the former could be written "3 4 5 * −", which unambiguously means "3 (4 5 * ) −" which reduces to "3 20 −"; the latter could be written "3 4 − 5 * " (or 5 3 4 − * , if keeping similar formatting), which unambiguously means "(3 4 −) 5 * ".


Your task is to implement a reverse polish notation calculator that reads in an equation and calculates the result.

Example:

* Input: 5 1 2 + 4 * + 3 -
* Output: 14

For this exercise, implement the calculator using your choice of list.

Cool References
---------------
[Standard Template Library Video Series by Stephan T. Lavaej at Microsoft][STL-video]
