## **Experiment No : 01**
## **Experiment Name : OOP1.**
## **Submission Date : 22 May 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
using namespace std;
class Rectangle
{
private:
    int length;
    int width;

public:
    void info()
    {
        int area = length * width;
        cout << "area " << area << endl;
        int para = 2 * (length + width);
        cout << "para " << para;
    }
    void set(int l)
    {
        length = l;
    }
    int get()
    {
        return length;
    }
    void set1(int w)
    {
        width = w;
    }
    int get1()
    {
        return width;
    }
};
int main()
{
    Rectangle r1;
    r1.set(20);
    r1.set1(5);
    r1.get();
    r1.get1();
    r1.info();
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/de75a111-c29d-4451-8a5a-9c18dbe3ac48">



</p>


--------------------------



## **Experiment No : 02**
## **Experiment Name : OOP.**
## **Submission Date : 22 May 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class student
{
private:
    int a = 3;
    void fun1();

public:
    int b = 4;
    void fun2();

protected:
    int c = 5;
    void fun3();
};
void student::fun1()
{
    cout << "fun1" << endl;
}
void student::fun2()
{
    cout << "fun2" << endl;
}
void student::fun3()
{
    cout << "fun3" << endl;
}

int main()
{
    student s1;
    cout << s1.b;
    s1.fun1();
    s1.fun2();
    s1.fun3();
}
```
## **Output :**
<p align="center">
<img src="">



</p>

