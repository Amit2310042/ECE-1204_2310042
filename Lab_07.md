
<p align="center">
<img width="1885" height="323" alt="image" src="https://github.com/user-attachments/assets/10d5eafe-92bb-4b26-b7af-02b7cb40e26e" />


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


--------------------------------

## **Experiment No : 02**
## **Experiment Name :Write a C++ class named Rectangle that demonstrates constructor overloading.**
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Rectangle
{
    int width, height;

public:
    Rectangle()
    {
        width = 1;
        height = 1;
        cout << "area is" << " " << width * height << endl;
    }
    Rectangle(int w, int h)
    {
        width = w;
        height = h;
        cout << "Area is" <<" "<< width * height << " " << endl;
    }
};
int main()
{
    Rectangle r1;
    Rectangle r2(10, 15);
}
```
## **Output :**
<p align="center">
<img width="1638" height="557" alt="image" src="https://github.com/user-attachments/assets/996c5c20-ea83-465e-b92c-ca13e5e76a74" />

--------------------------------



## **Experiment No : 03**
## **Experiment Name :Create a class Student that demonstrates constructor overloading with dynamic memory allocation..**
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include <iostream>
#include <cstring>
using namespace std;
class Student
{
    char *name;
    int age;

public:
    Student()
    {
        name = new char[50];
        strcpy(name, "Not set");
        age = 0;
    }
    Student(char *n, int a)
    {
        name = new char[strlen(n) + 1];
        strcpy(name, n);
        age = a;
    }
    void show()
    {
        cout << "name :" << name << endl;
        cout << "Age :" << age << endl;
    }
};
int main()
{
    Student s1, s2("Amit", 21);
    s1.show();
    s2.show();
}

```
## **Output :**
<p align="center">
<img width="1651" height="515" alt="image" src="https://github.com/user-attachments/assets/a5a61854-a45b-4deb-884c-ddcf89c2fb4a" />


------------------------


## **Experiment No : 04**
## **Experiment Name :Copy Constructor with Integer Pointer**
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Roy
{
    int *p;

public:
    Roy(int n)
    {
        p = new int;
        *p = n;
    }
    Roy(const Roy &ob)
    { // copy cons
        p = new int;
        *p = *(ob.p);
    }
    void get()
    {
        cout << "address : " << p << endl;
        cout << "Value : " << *p << endl;
    }
};
int main()
{
    Roy r(10);
    Roy r1 = r;

    r.get();
    r1.get();
}
```
## **Output :**
<p align="center">
<img width="1647" height="552" alt="image" src="https://github.com/user-attachments/assets/81cf2e5b-acc9-45d0-8fb6-3b10fd7ca6d1" />


------------------------------




## **Experiment No : 05**
## **Experiment Name :Copy Constructor with String Pointer.**
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include <iostream>
#include <cstring>
using namespace std;

class MyString
{
    char *str;

public:
    MyString(const char *input)
    {
        str = new char[strlen(input) + 1];
        strcpy(str, input);
    }

    MyString(const MyString &ob)
    {
        str = new char[strlen(ob.str) + 1];
        strcpy(str, ob.str);
    }

    void update(const char *up)
    {
        strcpy(str, up);
    }

    void show()
    {
        cout << str << endl;
    }
};

int main()
{
    MyString s1("Amit Roy");
    MyString s2 = s1;
    s1.update("roy");

    cout << "Updated s1: ";
    s1.show();

    cout << "Unaffected s2: ";
    s2.show();
    return 0;
}

```
## **Output :**
<p align="center">
<img width="1632" height="526" alt="image" src="https://github.com/user-attachments/assets/caadc0e1-e326-4b36-bfd5-d60f903c5430" />


