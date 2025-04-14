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
#include <semaphore.h>

using namespace std;

class Foo {
    sem_t semFirst, semSecond;

public:
    Foo() {
        sem_init(&semFirst, 0, 0);
        sem_init(&semSecond, 0, 0);
    }

    ~Foo() {
        sem_destroy(&semFirst);
        sem_destroy(&semSecond);
    }

    void first(function<void()> printFirst) {
        printFirst();
        sem_post(&semFirst);
    }

    void second(function<void()> printSecond) {
        sem_wait(&semFirst);
        printSecond();
        sem_post(&semSecond);
    }

    void third(function<void()> printThird) {
        sem_wait(&semSecond);
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
