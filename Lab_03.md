<p align="center">
<img src="https://github.com/user-attachments/assets/64dd93f4-ba02-44ce-9509-95bce4e846c1">


## **Experiment No : 01**
## **Experiment Name : Multilevel Inheritance with Access Specifiers**
## **Submission Date : 19 June 2025**
----------

## **Code :**
```C
#include<iostream>
#include<string>
using namespace std;

//Base class...

class A{
    int age;
    protected:
    int roll;
    public:
    string name;
    void set(){
        age=10;
        roll=23;
        name="Amit";
    }
};

//first derive class..

class B_public:public A{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }       
};

class B_protected:protected A{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }  
};

class B_private:private A{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }  
};


//second derive...

class C_public:public B_public{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }       
};

class C_pro:protected B_protected{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }       
};

class C_pri:private B_private{
    public:
    void show(){
        cout<<age<<endl;
        cout<<roll<<endl;
        cout<<name<<endl;
    }       
};

int main(){
    A a1;
    a1.set();

   B_public b1;
    b1.set();
    b1.show();

    C_public c1;
    c1.set();
    c1.show();

    B_protected bp;
    bp.set();
    bp.show();

    C_pro cp;
    cp.set();
    cp.show();

    B_private bpp;
    bpp.set();
    bpp.show();

    C_pri cpp;
    cpp.set();
    cpp.show();

}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/69562142-7029-42fd-a66f-d878a592c9c2">


## **Discussion :**
This code illustrate that how access specifier works in inheritance using private, protected, and public keywords in object-oriented programming,in C++.It explains what members of a class are accessible when that class is inherited using public, protected, or private inheritance.No matter the type of inheritance, a class can always access its own members.In public inheritance, public members stay public, protected stay protected, but private but private member is not accessible in first derived class.That is same as second derive class.In protected inheritance, both public and protected members of the base class become protected in the first derived class and again private members are not accessible.That is also same as second derive class.In private inheritance, everything public and protected members becomes private in the first derived class, and private members remain inaccessible as always.But in the second derive class all members remain inaccessible that time.

| Public Inheritance     | private | protected | public |
| ---------------------- | ------- | --------- | ------ |
| From own class         | yes     | yes       | yes    |
| From 1st derived class | no      | yes       | yes    |
| From 2nd derived class | no      | yes       | yes    |

| Protected Inheritance  | private | protected | public |
| ---------------------- | ------- | --------- | ------ |
| From own class         | yes     | yes       | yes    |
| From 1st derived class | no      | yes       | yes    |
| From 2nd derived class | no      | yes       | yes    |

| Private Inheritance    | private | protected | public |
| ---------------------- | ------- | --------- | ------ |
| From own class         | yes     | yes       | yes    |
| From 1st derived class | no      | yes       | yes    |
| From 2nd derived class | no      | no        | no     |

</p>

-----------------------------------------



## **Experiment No : 02**
## **Experiment Name :Constructors in Multilevel Inheritance**
## **Submission Date : 19 June 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
using namespace std;
class BaseClass
{
public:
    BaseClass(int x)
    {
        cout << "Base called " << x << endl;
    }
};
class Inter : public BaseClass
{
public:
    Inter(int x, int y) : BaseClass(x)
    {

        cout << "Inter called " << y << endl;
    }
};
class derive : public Inter
{
public:
    derive(int x, int y, int z) : Inter(x, y)
    {

        cout << "derive called " << z << endl;
    }
};
int main()
{
    derive d1(10, 20, 30);
}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/c8e301a8-4e43-4367-8bbc-1d3e35226289">



</p>


