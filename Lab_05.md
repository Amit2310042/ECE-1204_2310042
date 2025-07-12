<p align="center">
<img src="https://github.com/user-attachments/assets/2f13050e-5f59-4f3f-9d1a-e6c9513ebc16">


## **Experiment No : 01**
## **Experiment Name : **
## **Submission Date : 12 July 2025**
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
