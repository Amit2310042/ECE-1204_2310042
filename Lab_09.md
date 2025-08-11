## **Experiment No : 01**
## **Experiment Name :**Write a C++ program to implement a class called Shape with virtual member functions for calculating area and perimeter. Derive classes such as Circle, Rectangle, and Triangle from the Shape class and override virtual functions accordingly.(use pure virtual function)
## **Submission Date : 12 August 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Shape
{
public:
    virtual void get_area() = 0;
};
class Circle : public Shape
{
public:
    void get_area()
    {
        double r;
        cout << "Enter radius" << endl;
        cin >> r;
        cout << "Area of Circle " << 3.1416 * r * r << endl;
    }
};
class Rectangle : public Shape
{
public:
    void get_area()
    {
        double l, w;
        cout << "Enter length and width" << endl;
        cin >> l >> w;
        cout << "Area of Rectangle " << l * w << endl;
    }
};
class Triangle : public Shape
{
public:
    void get_area()
    {
        double h, b;
        cout << "Enter height and base" << endl;
        cin >> h >> b;
        cout << "Area of Triangle " << 0.5 * h * b << endl;
    }
};
int main()
{
    Circle c1;
    c1.get_area();
    Rectangle r1;
    r1.get_area();
    Triangle t1;
    t1.get_area();
}
```
## **Output :**
<p align="center">
<img width="1643" height="583" alt="image" src="https://github.com/user-attachments/assets/b5f84ebe-654c-4069-8967-d94b39f67598" />




---------------------------




## **Experiment No : 02**
## **Experiment Name :**Solve diamond shape problem (with and without virtual keyword).
## **Submission Date : 12 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
class A
{

public:
    int a;
    A() { a = 10; }
};
class B : virtual public A
{
public:
    B() { a = 25; }
};
class C : virtual public A
{
public:
    C() { a = 35; }
};
class D : public C, public B
{
public:
    D()
    {
    }
};
int main()
{
    D obj;
    cout << obj.a;
}

```
## **Output :**
<p align="center">
<img width="1626" height="472" alt="image" src="https://github.com/user-attachments/assets/19b46abc-d236-4da6-9e57-cfb1391c56a1" />



-----------------------------------------






## **Experiment No : 03**
## **Experiment Name :**Abstract Class with Constructor:
## **Submission Date : 12 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
class Employee
{
public:
    Employee() {};
    string name;
    double baseSalary;
    virtual double calculatePay() = 0;
    Employee(string n, double s)
    {
        name = n;
        baseSalary = s;
    }
};
class FullTimeEmployee : public Employee
{
public:
    FullTimeEmployee(string n, double s)
    {
        name = n;
        baseSalary = s;
    }

    double calculatePay()
    {
        cout << "Enter bonus" << endl;
        int b;
        cin >> b;
        return baseSalary + b;
    }
};
class PartTimeEmployee : public Employee
{
public:
    PartTimeEmployee(string n)
    {
        name = n;
        
    }

    double calculatePay()
    {
        cout << "Enter workhour and rate" << endl;
        int h, r;
        cin >> h >> r;
        return h * r;
    }
};
int main()
{
    cout<<"For Parttime Employee"<<endl;
    PartTimeEmployee p("AMIT");
    cout<<p.calculatePay()<<endl;

    cout<<"For Fulltime Employee"<<endl;
    FullTimeEmployee f("EMON", 300);
    cout << f.calculatePay()<<endl;
}

```
## **Output :**
<p align="center"
<img width="1667" height="455" alt="image" src="https://github.com/user-attachments/assets/eec07a2b-a207-4694-9d0c-473703d38dc6" />

-----------------------------------






## **Experiment No : 04**
## **Experiment Name :**Create an abstract class Device that has:A pure virtual function void start() A normal function void info() that prints “Generic device information” Derive Printer and Scanner from Device. In main(), call both start() and info() from derived class objects.
## **Submission Date : 12 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
class Device
{
public:
    virtual void start() = 0;
    void info()
    {
        cout << "Generic Device Information" << endl;
    }
};
class Printer : public Device
{
public:
    void start()
    {
        cout << "Printer printing" << endl;
    }
    void info()
    {
        cout << "printer" << endl;
    }
};
class Scanner : public Device
{
public:
    void start()
    {
        cout << "Scanner scanning" << endl;
    }
    void info()
    {
        cout << "scanner" << endl;
    }
};
int main()
{
    Printer p;
    p.start();
    p.info();

    Scanner s;
    s.start();
    s.info();
}

```
## **Output :**
<p align="center"
<img width="1650" height="448" alt="image" src="https://github.com/user-attachments/assets/6ec72b70-23ea-4d62-8132-25eeb239a0a2" />
