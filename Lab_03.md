<p align="center">
<img src="https://github.com/user-attachments/assets/2f13050e-5f59-4f3f-9d1a-e6c9513ebc16">


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
<img src="">



</p>

