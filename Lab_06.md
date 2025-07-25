
<p align="center">
<img src="https://github.com/user-attachments/assets/7a87bb59-4ba0-4dfc-ad90-e0eb1ca416cf">


## **Experiment No : 01**
## **Experiment Name : Create a class Student with attributes name, roll, and marks. Initialize an array of 5 studentsand write a program to input and display the data for all students.**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Student{
    
    string name;
    int roll;
    int marks;
    public:
    void set(string n,int r,int m){
        name=n;
        roll=r;
        marks=m;
    }
    void display(){
        cout<<name<<endl;
        cout<<roll<<endl;
        cout<<marks<<endl;
    }
};
int main(){
    Student s[5];
    int i;
    for(i=0;i<5;i++){
        string ch;
        cin>>ch;
        int r,m;
        cin>>r>>m;
        s[i].set(ch,r,m);
    }
    for(i=0;i<5;i++){
        s[i].display();
    }
}
```
## **Output :**
<p align="center">
<img width="1648" height="692" alt="image" src="https://github.com/user-attachments/assets/1092683d-44ab-467f-8942-c07f460287af" />
