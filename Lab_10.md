<p align="center">
<img width="1873" height="706" alt="image" src="https://github.com/user-attachments/assets/ed265189-32cd-441a-b0f7-cc464d7563b6" />



## **Experiment No : 01**
## **Experiment Name :Write a C++ program using constructor overloading.**
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Myclass
{
    int n;

public:
    Myclass()
    {
        n = 0;
        cout << n << endl;
    }
    Myclass(int x)
    {
        n = x;
        cout << n << endl;
    }
};
int main()
{
    Myclass o1;
    Myclass o2(100);
}
```
## **Output :**
<p align="center">
<img width="1647" height="531" alt="image" src="https://github.com/user-attachments/assets/f5a5d3af-d186-4f81-9294-3a72a3a6c8e4" />

