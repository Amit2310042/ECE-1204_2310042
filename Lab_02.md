## **Experiment No : 01**
## **Experiment Name : OOP1.**
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
<img src="https://github.com/user-attachments/assets/de75a111-c29d-4451-8a5a-9c18dbe3ac48">



</p>

