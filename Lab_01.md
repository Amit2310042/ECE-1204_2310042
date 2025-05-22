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


--------------------


## **Experiment No : 03**
## **Experiment Name : OOP.**
## **Submission Date : 22 May 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
using namespace std;
// class car{
//     private:
//     string company;
//     string model;
//     int year;
//     public:
//     void set(string c,string m,int y){
//         company=c;
//         model=m;
//         year=y;
//         cout<<company<<endl<<model<<endl<<year;
//     }
// };
// int main(){
//     car c1;
//     string com,mod;
//     int ye;
//     cin>>com>>mod>>ye;
//     c1.set(com,mod,ye);
// }

// with constructor

class car
{
private:
    string company;
    string model;
    int year;

public:
    car(string c, string m, int y)  //using constructor...
    {
        company = c;
        model = m;
        year = y;
        cout << company << endl
             << model << endl
             << year;
    }
};
int main()
{
    string com, mod;
    int ye;
    cin >> com >> mod >> ye;
    car c1(com, mod, ye);
}

```
## **Output :**
<p align="center">
<img src="">



</p>


------------------------



## **Experiment No : 04**
## **Experiment Name : OOP.**
## **Submission Date : 22 May 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
using namespace std;
class employee
{
private:
    string name;
    int id;
    int salary;

public:
    void set()
    {
        cout << "name" << endl;
        cin >> name;
        cout << "id" << endl;
        cin >> id;
        cout << "salary";
        cin >> salary;
    }
    void get()
    {
        int n;
        int highest;
        int index = 0;
        cout << "Enter employee number" << endl;
        cin >> n;
        employee arr[n];
        for (int i = 0; i < n; i++)
        {
            arr[i].set();
        }
        highest = arr[0].salary;
        for (int i = 0; i < n; i++)
        {
            if (arr[i].salary > highest)
            {
                highest = arr[i].salary;
                index = i;
            }
        }
        cout << "highest salary " << highest << endl;
        cout << "person :" << arr[index].name <<endl<< arr[index].id <<endl<< arr[index].salary << endl;
    }
};
int main()
{
    employee obj;
    obj.get();
}
```
## **Output :**
<p align="center">
<img src="">



</p>


-----------------------



## **Experiment No : 05**
## **Experiment Name : OOP.**
## **Submission Date : 22 May 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
using namespace std;
class date
{
private:
    int day;
    int month;
    int year;

public:
    void set()
    {
        cout << "day" << endl;
        cin >> day;
        cout << "month" << endl;
        cin >> month;
        cout << "year";
        cin >> year;
        get();
    }
    void get()
    {
        int count = 0;
        if ((day >= 1 && day <= 31) && (month >= 1 && month <= 12))
        {
            count++;
        }
        if (month == 2)
        {
            if ((year % 4 == 0) && ((year % 100 != 0) || (year % 400 == 0)))
            {
                if (day >= 1 && day <= 29)
                {
                    count++;
                }
            }
            else
            {
                if (day >= 1 && day <= 28)
                {
                    count++;
                }
            }
        }
        if (month == 1 || month == 3 || month == 5 || month == 7 || month == 8 || month == 10 || month == 12)
        {
            if (day >= 1 && day <= 31)
            {
                count++;
            }
            else
            {
                if (day >= 1 && day <= 30)
                {
                    count++;
                }
            }
        }
        if (count == 2)
        {
            cout << "day" << day << endl;
            cout << "month" << month << endl;
            cout << "year" << year << endl;
        }
        else
        {
            cout << "Invalid" << endl;
        }
    }
};

int main()
{
    date obj;
    obj.set();
}
```
## **Output :**
<p align="center">
<img src="">



</p>

