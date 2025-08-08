<p align="center">
<img width="1898" height="727" alt="image" src="https://github.com/user-attachments/assets/d09beb88-4674-4e16-8290-a540e9a7add6" />




## **Experiment No : 01**
## **Experiment Name :Create a simple calculator that performs binary (addition, subtraction, multiplication, division) and unary operations (prefix and postfix) using a class with three variables.**
## **Submission Date : 7 August 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Calculator
{
    int x, y, z;

public:
    Calculator() { x = y = z = 0; }
    Calculator(int i, int j, int k) { x = i, y = j, z = k; }
    Calculator operator+(Calculator ob);
    Calculator operator-(Calculator ob);
    Calculator operator*(Calculator ob);
    Calculator operator/(Calculator ob);
    Calculator operator++();
    Calculator operator--();
    Calculator operator++(int);
    Calculator operator--(int);
    Calculator operator+(int i);
    Calculator operator-(int i);
    Calculator operator=(Calculator ob);

    int operator==(Calculator ob);

    void show()
    {
        cout << "x" << " " << x << endl;
        cout << "y" << " " << y << endl;
        cout << "z" << " " << z << endl;
    }
};

Calculator Calculator::operator+(Calculator ob)
{
    Calculator temp;
    temp.x = x + ob.x;
    temp.y = y + ob.y;
    temp.z = z + ob.z;
    return temp;
}
Calculator Calculator::operator-(Calculator ob)
{
    Calculator temp;
    temp.x = x - ob.x;
    temp.y = y - ob.y;
    temp.z = z - ob.z;
    return temp;
}
Calculator Calculator::operator*(Calculator ob)
{
    Calculator temp;
    temp.x = x * ob.x;
    temp.y = y * ob.y;
    temp.z = z * ob.z;
    return temp;
}
Calculator Calculator::operator/(Calculator ob)
{
    Calculator temp;
    temp.x = x / ob.x;
    temp.y = y / ob.y;
    temp.z = z / ob.z;
    return temp;
}
Calculator Calculator::operator++()
{
    ++x;
    ++y;
    ++z;
    return *this;
}
Calculator Calculator::operator--()
{
    --x;
    --y;
    --z;
    return *this;
}
Calculator Calculator::operator++(int)
{
    x++;
    y++;
    z++;
    return *this;
}
Calculator Calculator::operator--(int)
{
    x--;
    y--;
    z--;
    return *this;
}
Calculator Calculator::operator+(int i)
{
    Calculator temp;
    temp.x = x + i;
    temp.y = y + i;
    temp.z = z + i;
    return temp;
}
Calculator Calculator::operator-(int i)
{
    Calculator temp;
    temp.x = x - i;
    temp.y = y - i;
    temp.z = z - i;
    return temp;
}
Calculator Calculator::operator=(Calculator ob)
{
    x = ob.x;
    y = ob.y;
    z = ob.z;
    return *this;
}
int Calculator::operator==(Calculator ob)
{
    return (x == ob.x) && (y == ob.y) && (z == ob.z);
}

int main()
{

    cout << "WELCOME TO MY CALCULATOR" << endl;
    cout << "...The Calculator..." << endl;
    cout << "Select which operation you want to do-->\n\n";
    cout << "Press the corresponding number followed by enter key...\n\n";
    cout << "Addition(Two objects): 1\n";
    cout << "Subtraction(Two objects): 2\n";
    cout << "Multiplication: 3\n";
    cout << "Division: 4\n";
    cout << "Preincrement: 5\n";
    cout << "Postincrement: 6\n";
    cout << "Predecrement: 7\n";
    cout << "Postdecrement: 8\n";
    cout << "Addition(Object & Integer): 9\n";
    cout << "Subtraction(Object & integer): 10\n";
    cout << "Comparison: 11\n";
    cout << "Exit: 0\n";

    while (1)
    {
        int choice;
        cin >> choice;
        switch (choice)
        {
        case 1:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 + c2;
            c3.show();
            break;
        }
        case 2:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 - c2;
            c3.show();
            break;
        }
        case 3:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 * c2;
            c3.show();
            break;
        }
        case 4:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 / c2;
            c3.show();
            break;
        }
        case 5:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            ++c1;
            c1.show();
            break;
        }
        case 6:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            c1++;
            c1.show();
            break;
        }
        case 7:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            --c1;
            c1.show();
            break;
        }
        case 8:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            c1--;
            c1.show();
            break;
        }
        case 9:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;
            int n;
            cout << "Which number you want to add" << endl;
            cin >> n;
            Calculator c1(a, b, c);
            c1 = c1 + n;
            c1.show();
            break;
        }
        case 10:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;
            int n;
            cout << "Which number you want to substract" << endl;
            cin >> n;
            Calculator c1(a, b, c);
            c1 = c1 - n;
            c1.show();
            break;
        }

        case 11:
        {
            int a, b, c, d, e, f, p, q, r;
            cout << "Enter 3 num for obj_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for obj_2" << endl;
            cin >> d >> e >> f;

            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 + c2;
            c3++;
            c3 = c3 + 100;
            cout << "Enter 3 num for new_obj" << endl;
            cin >> p >> q >> r;
            Calculator c4(p, q, r);
            if (c4 == c3)
            {
                cout << "Equal" << endl;
            }
            else
            {
                cout << "Not equal" << endl;
            }
            break;
        }
        case 0:
        {
            cout << "Thanks" << endl;
            break;
        }
        default:
        {
            cout << "Invalid input" << endl;
            break;
        }
        }
    }
}
```
## **Output :**
<p align="center">
<img width="1236" height="1002" alt="image" src="https://github.com/user-attachments/assets/b3ea04e9-33f7-47e5-896f-13c9ffc8c5dd" />


--------------------------





## **Experiment No : 02**
## **Experiment Name :Abobe program using friend function**
## **Submission Date : 8 August 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Calculator
{
    int x, y, z;

public:
    Calculator() { x = y = z = 0; }
    Calculator(int i, int j, int k) { x = i, y = j, z = k; }
    friend Calculator operator+(Calculator ob1, Calculator ob2);
    friend Calculator operator-(Calculator ob1, Calculator ob2);
    friend Calculator operator*(Calculator ob1, Calculator ob2);
    friend Calculator operator/(Calculator ob1, Calculator ob2);
    friend Calculator operator++(Calculator &ob1);
    friend Calculator operator--(Calculator &ob1);
    friend Calculator operator++(Calculator &ob1, int);
    friend Calculator operator--(Calculator &ob1, int);
    friend Calculator operator+(Calculator &ob1, int i);
    friend Calculator operator-(Calculator &ob1, int i);
    friend int operator==(Calculator &ob1, Calculator &ob2);

    void show()
    {
        cout << "x" << " " << x << endl;
        cout << "y" << " " << y << endl;
        cout << "z" << " " << z << endl;
    }
};

Calculator operator+(Calculator ob1, Calculator ob2)
{
    Calculator temp;
    temp.x = ob1.x + ob2.x;
    temp.y = ob1.y + ob2.y;
    temp.z = ob1.z + ob2.z;
    return temp;
}
Calculator operator-(Calculator ob1, Calculator ob2)
{
    Calculator temp;
    temp.x = ob1.x - ob2.x;
    temp.y = ob1.y - ob2.y;
    temp.z = ob1.z - ob2.z;
    return temp;
}
Calculator operator*(Calculator ob1, Calculator ob2)
{
    Calculator temp;
    temp.x = ob1.x * ob2.x;
    temp.y = ob1.y * ob2.y;
    temp.z = ob1.z * ob2.z;
    return temp;
}
Calculator operator/(Calculator ob1, Calculator ob2)
{
    Calculator temp;
    temp.x = ob1.x / ob2.x;
    temp.y = ob1.y / ob2.y;
    temp.z = ob1.z / ob2.z;
    return temp;
}
Calculator operator++(Calculator &ob1)
{
    ++ob1.x;
    ++ob1.y;
    ++ob1.z;
    return ob1;
}
Calculator operator--(Calculator &ob1)
{
    --ob1.x;
    --ob1.y;
    --ob1.z;
    return ob1;
}
Calculator operator++(Calculator &ob1, int)
{
    ob1.x++;
    ob1.y++;
    ob1.z++;
    return ob1;
}
Calculator operator--(Calculator &ob1, int)
{
    ob1.x--;
    ob1.y--;
    ob1.z--;
    return ob1;
}
Calculator operator+(Calculator &ob1, int i)
{
    Calculator temp;
    temp.x = ob1.x + i;
    temp.y = ob1.y + i;
    temp.z = ob1.z + i;
    return temp;
}
Calculator operator-(Calculator &ob1, int i)
{
    Calculator temp;
    temp.x = ob1.x - i;
    temp.y = ob1.y - i;
    temp.z = ob1.z - i;
    return temp;
}

int operator==(Calculator &ob1, Calculator &ob2)
{
    return (ob1.x == ob2.x) && (ob1.y == ob2.y) && (ob1.z == ob2.z);
}

int main()
{

    cout << "WELCOME TO MY CALCULATOR" << endl;
    cout << "...The Calculator..." << endl;
    cout << "Select which operation you want to do-->\n\n";
    cout << "Press the corresponding number followed by enter key...\n\n";
    cout << "Addition(Two objects): 1\n";
    cout << "Subtraction(Two objects): 2\n";
    cout << "Multiplication: 3\n";
    cout << "Division: 4\n";
    cout << "Preincrement: 5\n";
    cout << "Postincrement: 6\n";
    cout << "Predecrement: 7\n";
    cout << "Postdecrement: 8\n";
    cout << "Addition(Object & Integer): 9\n";
    cout << "Subtraction(Object & integer): 10\n";
    cout << "Comparison: 11\n";
    cout << "Exit: 0\n";

    while (1)
    {
        int choice;
        cin >> choice;
        switch (choice)
        {
        case 1:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 + c2;
            c3.show();
            break;
        }
        case 2:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 - c2;
            c3.show();
            break;
        }
        case 3:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 * c2;
            c3.show();
            break;
        }
        case 4:
        {
            int a, b, c, d, e, f;
            cout << "Enter 3 num for ob_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for ob_2" << endl;
            cin >> d >> e >> f;
            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 / c2;
            c3.show();
            break;
        }
        case 5:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            ++c1;
            c1.show();
            break;
        }
        case 6:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            c1++;
            c1.show();
            break;
        }
        case 7:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            --c1;
            c1.show();
            break;
        }
        case 8:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;

            Calculator c1(a, b, c);
            c1--;
            c1.show();
            break;
        }
        case 9:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;
            int n;
            cout << "Which number you want to add" << endl;
            cin >> n;
            Calculator c1(a, b, c);
            c1 = c1 + n;
            c1.show();
            break;
        }
        case 10:
        {
            int a, b, c;
            cout << "Enter 3 num for obj" << endl;
            cin >> a >> b >> c;
            int n;
            cout << "Which number you want to substract" << endl;
            cin >> n;
            Calculator c1(a, b, c);
            c1 = c1 - n;
            c1.show();
            break;
        }

        case 11:
        {
            int a, b, c, d, e, f, p, q, r;
            cout << "Enter 3 num for obj_1" << endl;
            cin >> a >> b >> c;
            cout << "Enter 3 num for obj_2" << endl;
            cin >> d >> e >> f;

            Calculator c1(a, b, c), c2(d, e, f), c3;
            c3 = c1 + c2;
            c3++;
            c3 = c3 + 100;
            cout << "Enter 3 num for new_obj" << endl;
            cin >> p >> q >> r;
            Calculator c4(p, q, r);
            if (c4 == c3)
            {
                cout << "Equal" << endl;
            }
            else
            {
                cout << "Not equal" << endl;
            }
            break;
        }
        case 0:
        {
            cout << "Thanks" << endl;
            break;
        }
        default:
        {
            cout << "Invalid input" << endl;
            break;
        }
        }
    }
}
```
## **Output :**
<p align="center">
<img width="1622" height="1005" alt="image" src="https://github.com/user-attachments/assets/07eef09e-49e3-4ce4-9320-e93f72690f1b" />



-----------------------



## **Experiment No : 03**
## **Experiment Name :**Write necessary code for the following formula. ob1=ob2=ob3=ob4
## **Submission Date : 29 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class cord
{
    int x,y;
    public:
    cord(){x=y=0;}
    cord(int i,int j){x=i;y=j;}
    cord operator=(cord ob);
    void get(){
        cout<<x<<" "<<y<<endl;
    }
};
cord cord::operator=(cord ob){
    x=ob.x;
    y=ob.y;
    return *this;
    // cord temp;
    // temp.x=ob.x;
    // temp.y=ob.y;
    
    // return temp;
}
int main(){
    cord ob2(10,20),ob3(30,40),ob4(50,60),ob1;
    ob1=ob2=ob3=ob4;
    ob1.get();
}
```
## **Output :**
<p align="center">
<img width="1647" height="335" alt="image" src="https://github.com/user-attachments/assets/65161d48-861b-45f6-889a-0cc8337fa49c" />


---------------------------







## **Experiment No : 04**
## **Experiment Name :**Write a program that overloades the increment operator of a class via memeber function and overloads the decrement operator via a friend function .
## **Submission Date : 8 August 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Roy
{
    int a,b,c;
    public:
    Roy(){a=b=c=0;}
    Roy(int i,int j,int k){a=i;b=j;c=k;}
    Roy operator++();
    friend Roy operator--(Roy &obj);
    void show(){
        cout<<"Val_a :"<<" "<<a<<endl;
        cout<<"Val_b :"<<" "<<b<<endl;
        cout<<"Val_c :"<<" "<<c<<endl;
    }
};
Roy Roy::operator++(){
    ++a;
    ++b;
    ++c;
    return *this;
}
Roy operator--(Roy &obj){
    --obj.a;
    --obj.b;
    --obj.c;
    return obj;
}

int main()
{
    Roy r1(2,3,4);
    ++r1;
    r1.show();

    --r1;
    r1.show();

    return 0;
}
```
## **Output :**
<p align="center">
<img width="1897" height="591" alt="image" src="https://github.com/user-attachments/assets/ebbd9460-2a56-4802-9b96-8438b4e9a774" />


