---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Example

```cpp
#include <iostream>
#include <thread>
#include <functional>
#include <mutex>

using namespace std;

class Foo {
    mutex mtxFirst, mtxSecond;

public:
    Foo() {}

    void first(function<void()> printFirst) {
        printFirst();
        mtxFirst.unlock();
    }

    void second(function<void()> printSecond) {
        mtxFirst.lock();
        printSecond();
        mtxSecond.unlock();
    }

    void third(function<void()> printThird) {
        mtxSecond.lock();
        printThird();
    }
};

int main() {
    Foo foo;

    thread t1([&]() {
        foo.first([]() {
            cout << "first";
        });
    });

    thread t2([&]() {
        foo.second([]() {
            cout << "second";
        });
    });

    thread t3([&]() {
        foo.third([]() {
            cout << "third";
        });
    });

    t1.join();
    t2.join();
    t3.join();

    return 0;
}

```
