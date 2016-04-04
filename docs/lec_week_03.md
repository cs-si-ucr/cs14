Lecture 3: Stacks and Queues
==============================




Stacks
------

Stacks are LIFO (last in, first out) data structures.
You've already encountered stacks before.
Recursion takes advantage of the function call stack.

Here's a small demo of how stacks work:
```cpp
#include <iostream>
#include <stack>

using namespace std;

int main() {
  stack<int> s;
  for(unsigned i = 0; i < 6; ++i) {
    cout << "Pushing i (" << i << ")" << endl;
    s.push(i);
  }

  while (!s.empty()) {
    cout << "Popping (" << s.top() << ")" << endl;
    s.pop();
  }

  if (s.empty()) cout << "stack is empty" << endl;

  return 0;
}
```

Try running that and see what is output.
Go ahead. I'll wait.

Were you surprised by the output?



Queues
------

>_The word queue is pronounced "Q" because all the other letters are waiting their turn..._

Queues are FIFO (first in, first out) data structures.
They're structured similarly to checkout lines at the grocery store;
Whoever gets in line first gets serviced first.

Here's a small demo of how queues work:

```cpp
#include <iostream>
#include <queue>

using namespace std;

int main() {
  queue<int> q;
  for(unsigned i = 0; i < 6; ++i) {
    cout << "Pushing i (" << i << ")" << endl;
    q.push(i);
  }

  while (!q.empty()) {
    cout << "Popping (" << q.front() << ")" << endl;
    q.pop();
  }

  if (q.empty()) cout << "queue is empty" << endl;

  return 0;
}
```

Run it!!
