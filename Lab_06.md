
<p align="center">
<img width="1885" height="323" alt="image" src="https://github.com/user-attachments/assets/10d5eafe-92bb-4b26-b7af-02b7cb40e26e" />


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


-------------------



## **Experiment No : 02**
## **Experiment Name : Create a class Book with a function display(). Create a pointer to a Book object and call display() using that pointer. Allocate memory dynamically..**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Book{
    public:
    void display(){
        cout<<"Book"<<endl;
    }
};
int main()
{
    Book *p=new Book;
    p->display();
}
```
## **Output :**
<p align="center">
<img width="1642" height="478" alt="image" src="https://github.com/user-attachments/assets/d1bffd3e-d937-40f2-8947-3b6098162ba3" />


--------------------------



## **Experiment No : 03**
## **Experiment Name : Create a class Rectangle with private members length and breadth. Use the this pointer to differentiate between local and member variables in the constructor.**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Rectangle{
    int length,breadth;
    public:
    Rectangle(int length,int breadth){
        this->length=length;
        this->breadth=breadth;
    }
    void dis(){
        cout<<"length"<<length<<endl;
        cout<<"breadth"<<breadth;

    }
};
int main(){
    Rectangle r(5,6);
    r.dis();

}
```
## **Output :**
<p align="center">
<img width="1652" height="466" alt="image" src="https://github.com/user-attachments/assets/5a58c9a0-ac0f-4c73-95d6-a95816058bea" />


---------------------------




## **Experiment No : 04**
## **Experiment Name : Create a program to dynamically allocate memory for an array of 10 integers, input values, calculate their sum, and deallocate memory properly using delete..**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
int main()
{
    int sum = 0;
    int *arr = new int[10];
    for (int i = 0; i < 10; i++)
    {
        cin >> arr[i];
        sum = sum + arr[i];
    }
    cout << sum << endl;
    delete[] arr;
}

```
## **Output :**
<p align="center">
<img width="1650" height="531" alt="image" src="https://github.com/user-attachments/assets/475d2240-4458-419e-bd4a-8ecb8101c268" />


----------------------------



## **Experiment No : 05**
## **Experiment Name : Create a class Employee that has a constructor and destructor. Dynamically allocate an object of this class and verify constructor and destructor execution using new and delete.**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Employee
{
public:
    Employee()
    {
        cout << "CONS" << endl;
    }
    ~Employee()
    {
        cout << "Des" << endl;
    }
};
int main()
{
    Employee *p = new Employee;
    delete p;
    return 0;
}
```
## **Output :**
<p align="center">
<img width="1638" height="505" alt="image" src="https://github.com/user-attachments/assets/d041525f-f660-4b02-aefb-9f488d36341c" />


------------------------------




## **Experiment No : 06**
## **Experiment Name : Write a function that takes an integer by reference and increments its value by 1. Show that the original value is changed outside the function.**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
void f(int &x){
    x++;
}
int main(){
    int a=10;
    f(a);
    cout<<a;
}
```
## **Output :**
<p align="center">
<img width="1606" height="511" alt="image" src="https://github.com/user-attachments/assets/0600f761-48de-4c59-8047-cb298b3b4d28" />



------------------------------



## **Experiment No : 07**
## **Experiment Name :Create a class Account with balance. Write a function that accepts an object of Account by reference and adds money to the balance..**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Account
{
public:
    Account(int n) { balance = n; }
    double balance;
};
void add(Account &ob)
{
    ob.balance = ob.balance + 500;
    cout << ob.balance << endl;
}
int main()
{
    Account a1(500);
    add(a1);
}
```
## **Output :**
<p align="center">
<img width="1628" height="503" alt="image" src="https://github.com/user-attachments/assets/a766588a-b545-4fef-901a-ca6c40d4a0d4" />



-------------------------------

## **Experiment No : 09**
## **Experiment Name :Create a function swapValues(int &a, int &b) that swaps two integers using references. Then create a function sortDescending(int &x, int &y, int &z) that uses swapValues() to sort the three integers in descending order using only reference passing..**
## **Submission Date : 25 july 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
void swap(int &a,int &b);
void des(int &x,int &y,int &z);
int main(){
    int x=10,y=20,z=30;
    des(x,y,z);
    cout<<x<<endl;
     cout<<y<<endl;
      cout<<z<<endl;
}
void swap(int &a,int &b){
    int t=b;
    b=a;
    a=t;
}
void des(int &x,int &y,int &z){
    if(x<y){
        swap(x,y);
    }
    if(x<z){
        swap(x,z);
    }
    if(y<z){
        swap(y,z);
    }
}
```
## **Output :**
<p align="center">
<img width="1630" height="517" alt="image" src="https://github.com/user-attachments/assets/c4019ebe-9b33-406f-8f8d-2435e0739c68" />



-------------------------------------


## **Experiment No : 10**
## **Experiment Name :Create a class BankAccount with accountNumber and balance. Write a function transfer(BankAccount &from, BankAccount &to, float amount) that transfers money from one account to another using only reference parameters, and ensure the from account has enough balance.**
----------

## **Code :**
```C
#include <iostream>
using namespace std;
class Bank
{
public:
    int accNum;
    Bank(int ac, double bal)
    {
        accNum = ac;
        balance = bal;
    }
    double balance;
};
void transfer(Bank &from, Bank &to, double amount)
{
    if (from.balance >= amount)
    {
        to.balance += amount;
        from.balance -= amount;
    }
    else
    {
        cout << "Not enough" << endl;
    }
}
int main()
{
    Bank a(231, 1000), b(123, 0);
    transfer(a, b, 500);
    cout << a.balance << endl;
}
```
## **Output :**
<p align="center">
<img width="1663" height="551" alt="image" src="https://github.com/user-attachments/assets/63392479-a791-4001-a7fb-6660d0035475" />
