# Lambda Expressions

```cpp
#include<iostream>
#include<string>
using namespace std;
 
void sum1(int a, int b)
{
    cout << "sum1 func : " << a + b << endl;
}
 
int main(void) {
 
    sum1(10, 20);
 
    [](int a, int b)
    {
        cout << "sum2 lambda : " << a + b << endl;
    }(30, 40);
 
    return 0;
}
```
