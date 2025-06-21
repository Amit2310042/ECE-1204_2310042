<p align="center">
<img src="https://github.com/user-attachments/assets/2f13050e-5f59-4f3f-9d1a-e6c9513ebc16">


## **Experiment No : 01**
## **Experiment Name : Virtual**
## **Submission Date : 21 June 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Animal{
  public:
  virtual void makeSound(){
    cout<<"Animal sound"<<endl;

  }

};
class Dog:public Animal{
    void makeSound() override{
        cout<<"Dog sound"<<endl;
    }
};
class Cat:public Animal{
    void makeSound() override{
        cout<<"Cat sound"<<endl;
    }
};

int main(){
    Animal* a;
    Dog d;
    Cat c;
    a=&d;
    a->makeSound();
    a=&c;
    a->makeSound();
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/3328b99d-1211-4472-a28a-142a653add1b">


-----------------






## **Experiment No : 02**
## **Experiment Name : Virtual**
## **Submission Date : 21 June 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Person{
  public:
  virtual void showInfo(){
    cout<<"Person sound"<<endl;

  }

};
class Student:public Person{
    void showInfo() override{
        cout<<"Student sound"<<endl;
    }
};

void fun(Person p){
    p.showInfo();
}


int main(){
    Person p1;
    Student s1;
    
    fun(s1);
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/1b45b28b-b6d9-427e-9fa8-af29f9fb2322">


------------------

## **Code :**
```C
#include<iostream>
using namespace std;
class Person{
  public:
  virtual void showInfo(){
    cout<<"Person sound"<<endl;

  }

};
class Student:public Person{
    void showInfo() override{
        cout<<"Student sound"<<endl;
    }
};

void fun(Person *p){
    p->showInfo();
}


int main(){
    Person *p1;
    Student s1;
    p1=&s1;
    fun(p1);
}


```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/9cfbe7c9-45ec-40ac-8d9f-762cdd0e7e58">


--------------------------------



## **Experiment No : 03**
## **Experiment Name : Using array pointer**
## **Submission Date : 21 June 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Vehicle
{
public:
    virtual void start()
    {
        cout << "Vehicle sound" << endl;
    }
};
class Car : public Vehicle
{
    void start() override
    {
        cout << "Car sound" << endl;
    }
};
class Bike : public Vehicle
{
    void start() override
    {
        cout << "Bike sound" << endl;
    }
};

int main()
{
    Vehicle *arr[2];
    Car c;
    Bike b;
    arr[0] = &c;
    arr[1] = &b;
    for (int i = 0; i < 2; i++)
    {
        arr[i]->start();
    }
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/f106dbdd-636c-453c-8ae2-1568038a0439">
