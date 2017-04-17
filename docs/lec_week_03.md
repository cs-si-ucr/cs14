Big-O Time Complexity
==============================

For the following functions give the nearest Big-O time complexity.

Problem 1
---------

```cpp
int f1(const std::vector<int>& v) {
    int result = 0;
    for (int i = 0; i < v.size(); ++i) {
        for (int j = v.size(); j >= 0; j -= 2) {
            result += v.at(i) * j;
        }
    }
    return result;
}
```

Problem 2
---------

```cpp
void f2(std::list<int>& l, int n) {
    for (int i = 0; i < n; ++i) {
        l.remove(i);
    }
}
```

Problem 3
---------

```cpp
void f3(int n, int m, int r) {
    for (int i = 0; i < n; ++i) {
        for (int j = m; m > 0; m /= 2) {
            while (r > 0) {
                std::cout << r << std::endl;
                --r;
            }
        }
    }
}
```

Problem 4
---------

```cpp
void f4(std::vector<int>& v) {
    for (std::vector<int>::iterator itr = v.begin(); itr != v.end(); ++itr) {
        std::random_shuffle(itr, v.end());
        for (auto itr2 = v.begin(); itr2 != v.end(); ++itr2) {
            std::cout << *itr2 << ' ';
        }
        std::cout << std::endl;
    }
    std::sort(v.begin(), v.end());
}
```


Problem 5 
---------

```cpp
void f5(std::stack<int>& s) {
    if (s.empty()) return;
    std::stack<int> temp;
    int min;
    for (int i = 0; i < s.size(); ++i) {
        min = s.top();
        s.pop();
        for(int j = i; j < s.size(); ++j) {
            if (s.top() < min) {
                temp.push(min);
                min = s.top();
            }
            else temp.push(s.top());
            s.pop();
        }i
        s.push(min);
        while(!temp.empty()) {
            s.push(temp.top());
            temp.pop();
        }
    }
}
```

Problem 6 
---------

For this problem just give the Big-O time complexity for `f6`

Bonus: What is the Big-O space complexity for `f6`?

```cpp


void f6(std::queue<int>& q) {
    if (q.size() <= 1) return;
    std::queue<int> left;
    std::queue<int> right;
    for (int i = 0; i < q.size() / 2; ++i) {
        left.push(q.front());
        q.pop();
    }
    while(!q.empty()) {
        right.push(q.front());
        q.pop();
    }
    f6(left);
    f6(right);
    q = f7(left, right);
}

std::queue<int> f7(std::queue<int>& left, std::queue<int>& right){
    std::queue<int> result;
    while(!left.empty() && !right.empty()) {
        if (left.front() > right.front()) {
            resulti.push(right.front());
            right.pop();
        }
        else {
            result.push(left.front());
            left.pop();
        }
    }
    while(!left.empty()) {
        result.push(left.front());
        left.pop();
    }
    while(!right.empty()) {
        result.push(right.front());
        right.pop();
    }
    return result;
}
```
