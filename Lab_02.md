<p align="center">
<img src="https://github.com/user-attachments/assets/2f13050e-5f59-4f3f-9d1a-e6c9513ebc16">


## **Experiment No : 01**
## **Experiment Name : Design a system for a company that has two types ofemployees: PermanentEmployee and ContractEmployee. The company also hasa HRDepartment that needs access to private data of all employees to calculate bonuses.**
## **Submission Date : 28 May 2025**
----------

## **Code :**
```C
#include<iostream>
#include<string>
using namespace std;
class Employee{
    public:
    string name;
    int id;
    double salary;
};

class PermanentEmployee:private Employee{
    int year;
    public:
 PermanentEmployee(string name,int id,double salary,int year);
 friend class HRDepartment;
};

class ContractEmployee:private Employee{
    int duration;
    public:
 ContractEmployee(string name,int id,double salary,int duration);
 friend class HRDepartment;
};

class HRDepartment{
    public:
    double pe_bonus(PermanentEmployee& par);
    double co_bonus(ContractEmployee& con);
   void display_par(PermanentEmployee& par);
   void display_con(ContractEmployee& con);
};

PermanentEmployee::PermanentEmployee(string name,int id,double salary,int year){
    this->name=name;
    this->id=id;
    this->salary=salary;
    this->year=year;
}
ContractEmployee::ContractEmployee(string name,int id,double salary,int duration){
    this->name=name;
    this->id=id;
    this->salary=salary;
    this->duration=duration;
}

double HRDepartment::pe_bonus(PermanentEmployee& par){
    return 0.1*par.salary + 1000*par.year;
}
double HRDepartment::co_bonus(ContractEmployee& con){
    return 0.05*con.salary;
}
void HRDepartment ::display_par(PermanentEmployee& par){
    cout<<"Bonus for Permanent Employee "<<par.name<<":"<<pe_bonus(par)<<endl;
}
void HRDepartment ::display_con(ContractEmployee& con){
    cout<<"Bonus for Permanent Employee "<<con.name<<":"<<co_bonus(con)<<endl;
}

int main(){
    PermanentEmployee p1("amit",2310042,150000,1);
    ContractEmployee c1("Rohan",2310045,190000,1);
    HRDepartment h1;
    h1.display_par(p1);
    h1.display_con(c1);


}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/4c078ac8-8703-497d-85eb-3a18d11e79e2">



</p>




--------------------------------------





## **Experiment No : 02**
## **Experiment Name : A company manages various projects. Each project is handled by a project manager and different types of team members: Developers and Testers.**
## **Submission Date : 28 May 2025**
----------

## **Code :**
```C
#include<iostream>
#include<string>
using namespace std;
class TeamMember{
    protected:
    // friend class promanager;
    string name;
    int id;
    float hourlyrate;
};
class Developer:public TeamMember{
    friend class promanager;
    int loc;
    public:
    Developer(string name,int id,float hourlyrate,int loc);
    
};
class Tester:public TeamMember{
    int bugs;
    public:
    Tester(string name,int id,float hourlyrate,int bugs);
    friend class promanager;

};
class promanager{
    public:
    double de_cost(Developer& dev);
    double te_cost(Tester& test);
    void display_de(Developer& dev);
    void display_te(Tester& test);
};

Developer::Developer(string name,int id,float hourlyrate,int loc){
    this->name=name;
    this->id=id;
    this->hourlyrate=hourlyrate;
    this->loc=loc;
}

Tester::Tester(string name,int id,float hourlyrate,int bugs){
    this->name=name;
    this->id=id;
    this->hourlyrate=hourlyrate;
    this->bugs=bugs;
}

double promanager::de_cost(Developer& dev){
    return (dev.hourlyrate *160) +(0.1*dev.loc);  
}
double promanager::te_cost(Tester& test){
    return (test.hourlyrate *160) +(50*test.bugs);  
}
void promanager::display_de(Developer& dev){
    cout<<"Cost for Developer"<<dev.name<<":"<<de_cost(dev)<<endl;
}
void promanager::display_te(Tester& test){
    cout<<"Cost for Tester"<<test.name<<":"<<te_cost(test)<<endl;
}
int main(){
    Developer d1("Amit",23100,20,5);
    Tester t1("Rohan",231002,25,6);
    promanager p1;
    p1.display_de(d1);
    p1.display_te(t1);

}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/a00e03da-aeb2-4742-ae79-3c96c939973d">



</p>




---------------------------------------------




## **Experiment No : 03**
## **Experiment Name : Find Prime Numbers Within a Range (Use class & object)**
## **Submission Date : 28 May 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class Prime{
    public:
    int a,b;
    void input(){
        cout<<"Input number for starting range:";
        cin>>a;
        cout<<"Input number for ending range:";
        cin>>b;
    }
    void dis_prime(){
        int n=0;
        for(int num=a;num<=b;num++){
            
             if(num==1){
                    num++;   //1 is not prime
                }
            int count=1;
            for(int i=2;i<=num/2;i++){
               
                if(num%i==0){
                    count=0;
                    break;
                }
            }
            if(count){
                n++;
                cout<< num<<" " ;
            }
        }
        cout<<endl<<"The total number of prime numbers in the range is:"<<n<<endl;
    }
};
int main(){
    Prime p1;
    p1.input();
    cout<<"The prime numbers in range are :"<<endl;
    p1.dis_prime();
}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/785d270a-8b16-40cd-8006-21e1805063a2">



</p>





-----------------------------------------------



## **Experiment No : 04**
## **Experiment Name : Find the Factorial of a Number (Use friend class)Write a program in C++ to find the factorial of a number.**
## **Submission Date : 28 May 2025**
----------

## **Code :**
```C
#include<iostream>
using namespace std;
class A{
    int n;
    public:
    A(int n){
        this->n=n;
    }      
    friend class B;
};
class B{
    public:
    int fact=1;
    void get(A&obj){
        for(int i=1;i<=obj.n;i++){
            fact=fact*i;
        }
        cout<<fact;
    }
};
int main(){
    int p;
    cout<<"Input a number to find the factorial:";
    cin>>p;
    A a1(p);
    B b1;
    
    cout<<"The factorial of the given number is:";
    b1.get(a1);
}
```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/b66901f9-9ee2-4aa6-b04c-0fe433315b3f">



</p>











----------------------------------------------




## **Experiment No : 05**
## **Experiment Name : Volume of a Cube (Use constructor)**
## **Submission Date : 28 May 2025**
----------

## **Code :**
```C
#include<iostream>
#include<cmath>
using namespace std;
class Cube{
    int side;
    public:
    Cube(int side){
        this->side=side;
        cout<<"The volume of the cube is :";
        cout<<pow(side,3);

    }
};
int main(){
    cout<<"Input the side of a cube :";
    int p;
    cin>>p;
    Cube c1(p);
}

```
## **Output :**
<p align="center">
<img src="https://github.com/user-attachments/assets/2d6cccdf-397c-4487-bfa7-ec697f232be0">



</p>

