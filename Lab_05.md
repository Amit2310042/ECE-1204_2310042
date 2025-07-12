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




## **Experiment No : 01**
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
<img src="">

