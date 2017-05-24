Inserstion Sort
---------------
Another type of sort called insertion sort sorts a list of elements as they are inserted into the array.
The values inserted are compared to each of the other values in the list until the correct posistion of 
the element is found.

For example, in the following image, the given array is sorted with insertion sort.

![alt-text](http://www.studytonight.com/data-structures/images/insertion-sort.png)

Firstly, the first value in the array, `5`, is inserted to an empty list, which is of course sorted.
Secondly, the next value in the array, `1`, is inserted. Since the list is not empty, the value being
inserted has to be compared to the other values in the list. Since 1 is less than 5 and this list is being
sorted in ascending order, the two values `1` and `5` have to be swapped. This process is repeated until the
list no longer has values to sort.

This sort runs in `O(n^2)` time, but has an `O(n)` best case.

**Excercises:**

* Given a list: `0,9,4,2,7,4`, perform insertion sort on the list, showing each step of the way.
* What would the lists look like when insertion sort runs in O(n^2) time? What about for O(n) time?

Quick Sort
----------

In Place and Stable Sorts
------------------------
A sorting algorithm can be described with two different classifiers: "in-place" and "stable".

A stable sorting algorithm is one that when comparing values that are equal, does not perform a swap.
That is to say that the sorting algorithm is more stable because the values in the list do not change
thier position if they are equal.

An inplace sorting algorithm is one that sorts the values of the list within the list itself. It does
not create another list to copy the values into, all the sorting is done within the list itself.
