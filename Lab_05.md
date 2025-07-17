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
class Box{
    double length,width,height;
    public:
    inline Box(double l,double w,double h){
        length=l;
        width=w;
        height=h;
    }
    inline double volume(){
        return length*width*height;
    }
};
inline void compareVolume(Box o1,Box o2){
    if(o1.volume()>o2.volume()){
        cout<<"Box 1 has a larger volume"<<endl;
    }
    else{
        cout<<"Box 2 has a larger volume"<<endl;
    }
}
int main(){
    Box b(10,5,6);
    Box c(12,2,3);
    cout<<"Volume of Box 1:"<<b.volume()<<endl;
    cout<<"Volume of Box 2:"<<c.volume()<<endl;
    compareVolume(b,c);
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/da23bf46-1a43-48a3-8130-b26908042c39">

-----------------------------




## **Experiment No : 02**
## **Experiment Name : **
## **Submission Date : 12 July 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Stack
{
    char arr[10];
    int tos;
    public:
    Stack(){
        tos=0;
    }
    void push(char ch){
        if(tos==10){
            cout<<"stack is full"<<endl;
        }
        else{
            arr[tos]=ch;
            tos++;
        }
    }
    char pop(){
        if(tos==0){
            cout<<"stack is empty"<<endl;
        }
        else{
            
            tos--;
            return arr[tos];
        }
    }
};
int main(){
    Stack s1,s2;
    s1.push('a');
    s1.push('b');
    s1.push('c');
    s2=s1;
    cout<<"1st stack"<<endl;
    cout<<s1.pop()<<endl;
    cout<<s1.pop()<<endl;
    cout<<s1.pop()<<endl;
    cout<<"2nd stack"<<endl;
    cout<<s2.pop()<<endl;
    cout<<s2.pop()<<endl;
    cout<<s2.pop()<<endl;
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/4fd4fcea-5c36-4f91-85ee-623e6590f483">



-------------------------------------





## **Experiment No : 03**
## **Experiment Name : **
## **Submission Date : 12 July 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Person
{
    public:
      string name;
    int age;
    string city;
    Person(string name,int age,string city){
        this->name=name;
        this->age=age;
        this->city=city;
    }
    void show(){
        cout<<"Name :"<<name<<endl;
        cout<<"age :"<<age<<endl;
        cout<<"city :"<<city<<endl;
    }
};
//pass by value
void update_per_info(Person p){
    string c;
    int a;
    cout<<"Update age"<<endl;
    cin>>a;
    p.age=a;
    cout<<"Update city"<<endl;
    cin>>c;
    p.city=c;
}

//pass by reference
void update_per_info(Person* p){
    string c;
    int a;
    cout<<"Update age"<<endl;
    cin>>a;
    p->age=a;
    cout<<"Update city"<<endl;
    cin>>c;
    p->city=c;
}
int main(){
    Person o1("Amit",22,"Sreemangal");
    cout<<"Before fun call"<<endl;
    o1.show();

    cout<<"call by value"<<endl;
    update_per_info(o1);
    o1.show();

    cout<<"call by ref"<<endl;
    update_per_info(&o1);
    o1.show();

}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/0ec46f97-2e12-4fae-b874-fd7f58e4c463">


---------------------------------



## **Experiment No : 04**
## **Experiment Name : **
## **Submission Date : 12 July 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Person{
    string name;
    int age;
    public:
    void set(string name,int age){
        this->name=name;
        this->age=age;
    }
    void get(){
        cout<<"Name:"<<name<<endl;
        cout<<"age"<<age<<endl;
    }
};
int main(){
    Person*p=new Person;
    cout<<"Dynamically created object"<<endl;
    p->set("amit",22);
    p->get();
    
    Person*p1=new Person[3];
    cout<<"Dynamically created aray of object"<<endl;
    for(int i=0;i<3;i++){
        cout<<"Enter info of"<<i<<"person"<<endl;
        string n;
        int a;
        cout<<"enter name"<<endl;
        cin>>n;
        cout<<"enter age"<<endl;
        cin>>a;
        p1[i].set(n,a);

    }

    for(int i=0;i<3;i++){
        cout<<"info of"<<i<<"person"<<endl;
        p1[i].get();

    }
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/ac75c23d-bc30-4930-8f13-ec77a4fdc0bb">


----------------------------




## **Experiment No : 05**
## **Experiment Name : **
## **Submission Date : 17 July 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Stack
{
    char arr[10];
    int tos;
    public:
    Stack(){
        tos=0;
    }
    void push(char ch){
        if(tos==10){
            cout<<"stack is full"<<endl;
        }
        else{
            arr[tos]=ch;
            tos++;
        }
    }
    char pop(){
        if(tos==0){
            cout<<"stack is empty"<<endl;
        }
        else{
            
            tos--;
            return arr[tos];
        }
    }
};
int main(){
    Stack*s1=new Stack;
    s1->push('a');
    s1->push('b');
    s1->push('c');
    cout<<s1->pop()<<endl;
    cout<<s1->pop()<<endl;
    cout<<s1->pop()<<endl;
    
}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/bada737c-3a4e-4423-bb68-145b48181077">

------------------------

## **Code :**
```C
#include<iostream>
using namespace std;
class Queue
{
    char arr[10];
    int start,end;
    public:
    Queue(){
        start=0,end=0;
    }
    void push(char ch){
        if(end==10){
            cout<<"Queue is full"<<endl;
        }
        else{
            arr[end]=ch;
            end++;
        }
    }
    char pop(){
        if(start==end){
            cout<<"stack is empty"<<endl;
        }
        else{
            char ch=arr[start];
            start++;
            return ch;
        }
    }
};
int main(){
    Queue* q=new Queue;
    q->push('1');
    q->push('2');
    q->push('3');
    cout<<q->pop();
    cout<<q->pop();
    cout<<q->pop();
    
}

```
## **Output :**
<p align="center">
<img src="">
