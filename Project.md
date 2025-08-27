## **Project No : 01**
## **Project Name :Supershop Management System**
## **Submission Date : 26 August 2025**
----------

## **Code :**
```C
#include <iostream>
#include <string>
#include <iomanip> // To use setprecision to display 2 digits after dot
#include <cstdio>  // To use sprintf function to display 2 digits after dot
#include <fstream> // For file handling operations
#include <ctime>   // For time and date functionality
using namespace std;

//Class Declarations
//Classes for Login System
class User;
class Manager_id;
class Customer_id;
class Admin;

//Classes for Item Management
class Product;
class Dairy;
class Fruits;
class Grocery;

//Classes for Employee Management
class Person;
class Manager;
class Employee;

//Classes for Order Management
class Customer;
class NewCustomer;
class RegularCustomer;
class VIPcustomer;

// Static variables for TotalOrders and TotalSoldAmount
static int TotalOrders = 0;
static double TotalSoldAmount = 0.0;

// Functions for getting and setting static values to File
void GetStaticValues();
void SetStaticValues();

//Class Definitions

// Login Part
class User
{
protected:
    string id;
    string password;
    int flag = 0;

public:
    User(string uid, string pass)
    {
        id = uid;
        password = pass;
    }
    bool authenticate(string uid, string pass);
    virtual void dashboard() = 0; // pure virtual
    int get_flag();
    void set_flag(int f);
};

bool User ::authenticate(string uid, string pass)
{
    return (id == uid && password == pass);
}

int User ::get_flag()
{
    return flag;
}

void User ::set_flag(int f)
{
    flag = f;
}

class Manager_id : virtual public User
{
    public:
        Manager_id(string uid, string pass) : User(uid, pass) {}
        void dashboard() override;
};

void Manager_id::dashboard()
{
    cout << "\n=== Manager Dashboard ===\n";
    flag = 1;
}

// Customer_id inherits virtually
class Customer_id : virtual public User
{
    public:
        Customer_id(string uid, string pass) : User(uid, pass) {}
        void dashboard() override;
};
void Customer_id::dashboard()
{
    cout << "\n=== Customer Dashboard ===\n";
    flag = 1;
}

// Admin now has only ONE copy of User
class Admin : public Manager_id, public Customer_id
{
public:
    Admin(string uid, string pass)
        : User(uid, pass), Manager_id(uid, pass), Customer_id(uid, pass) {}
    void dashboard() override;
};

void Admin ::dashboard()
{
    cout<< "\n=== Admin Dashboard ===\n";
    cout<< "1.Manage the Supershop.\n";
    cout<< "2.Order Something.\n";
    flag=1;
}


//Product Management Part
// Base class
class Product
{
    string SuperShopName = "Amader Bazar";
    string BranchName = "Rajshahi";
    int BranchCode = 1216;
    string Madein = "Bangladesh";

protected:
    string name;
    double price;
    int id;

public:
    int quantity;
    virtual void info();
    virtual void change_price(double discount);
    string getname();
    double getprice();
    int getid();
};

void Product ::info()
{
    cout<< name << " - " << price << " Tk" << endl;
    cout<< "Super Shop Name: " << SuperShopName << endl;
    cout<< "Made in: " << Madein << endl;
    cout<< "Branch Name: " << BranchName << endl;
    cout<< "Branch Code: " << BranchCode << endl;
}

void Product ::change_price(double discount)
{
    price = price - (discount / 100) * price;
}

string Product ::getname()
{
    return name;
}

double Product ::getprice()
{
    return price;
}
int Product ::getid()
{
    return id;
}

// Derived class
class Dairy : public Product
{
        string cornerType = "Dairy";

    public:
        Dairy(string name, double price, int quantity, int id);
        template <class T>
        friend void show(T items[]);
};

Dairy ::Dairy(string name, double price, int quantity, int id)
{
    this->name = name;
    this->price = price;
    this->quantity = quantity;
    this->id = id;
}

// Derived class
class Fruits : public Product
{
        string cornerType = "Fruits";

    public:
        Fruits(string name, double price, int quantity, int id);
        template <class T>
        friend void show(T items[]); // Generic type is Class
};

Fruits ::Fruits(string name, double price, int quantity, int id)
{
    this->name = name;
    this->price = price;
    this->quantity = quantity;
    this->id = id;
}

// Derived class
class Grocery : public Product
{
        string cornerType = "Grocery";

    public:
        Grocery(string name, double price, int quantity, int id);
        template <class T>
        friend void show(T items[]);
};

Grocery ::Grocery(string name, double price, int quantity, int id)
{
    this->name = name;
    this->price = price;
    this->quantity = quantity;
    this->id = id;
}

// Generic Friend Function Definition. 
template <class T>
void show(T items[])
{
    for (int i=0; i<5; i++)
    {
        cout<< items[i].id<<"\t"
            << items[i].name<<"\t"
            << items[i].price<<"\t\t"
            << items[i].quantity<<endl;
    }
}

// Function to save order to file
void SaveOrderToFile(string customerName, int customerId, string customerType,
                     string orderSummary, double totalCost, double discountAmount,
                     double finalAmount, double discountRate)
{
    try
    {
        // Get current time
        time_t now = time(0);
        char *timeString = ctime(&now);
        string orderTime = timeString;
        orderTime.pop_back();

        // Open file for writing (append mode)
        ofstream OrderFile("orders.txt", ios::app);
        if(OrderFile.is_open() == false)
        {
            throw string("Could not open orders file for writing!");
        }

        // Write order details to file
        OrderFile<< "========================================" << endl;
        OrderFile<< "ORDER RECORD" <<endl;
        OrderFile<< "Date & Time: " << orderTime<<endl;
        OrderFile<< "Customer Name: " << customerName<<endl;
        OrderFile<< "Customer ID: " << customerId <<endl;
        OrderFile<< "Customer Type: " << customerType <<endl;
        OrderFile<< "----------------------------------------" <<endl;
        OrderFile<< "Items Purchased:" <<endl;
        OrderFile<< orderSummary;
        OrderFile<< "----------------------------------------" <<endl;
        OrderFile<< "Subtotal: " << fixed<<setprecision(2)<<totalCost << " Tk"<<endl;
        if (discountRate > 0)
        {
            OrderFile << "Discount(" << discountRate << "%): -"<<fixed<<setprecision(2)<<discountAmount<<" Tk"<<endl;
        }
        OrderFile<< "Final Amount: " <<fixed<<setprecision(2)<<finalAmount<<" Tk"<<endl;
        OrderFile<< "========================================"<<endl<<endl;

        // Update stats
        TotalOrders++;
        TotalSoldAmount += finalAmount;
        SetStaticValues();

        OrderFile.close();
        cout<< "Order successfully saved to file!"<<endl;
    }
    catch (string e)
    {
        cout<<"Error saving order: "<<e<<endl;
    }
}

// Class Definition
class Customer
{
    protected:
        string name;
        int id;
        double discountRate;

    public:
        Customer(string n, int ID, double rate) : name(n), id(ID), discountRate(rate) {}

        // Getter methods to access object attributes
        double getDiscountRate() const { return discountRate; }
        double getDiscountRate(double totalCost) const // overloaded function for Regular and VIP Customer Added Discount
        {
            if (totalCost > 10000)
            {
                return discountRate + 5;
            }
            else
                return discountRate;
        }
        int getId() const { return id; }
        string getName() const { return name; }
};

class NewCustomer : public Customer
{
    public:
        NewCustomer(string n, int ID) : Customer(n, ID, 0) {}
};

class RegularCustomer : public Customer
{
    public:
        RegularCustomer(string n, int ID) : Customer(n, ID, 5) {}
};

class VIPcustomer : public Customer
{
    public:
        VIPcustomer(string n, int ID) : Customer(n, ID, 15) {}
};

// Salary Calculation
class Person
{
    protected:
        int id;
        string name;

    public:
        Person(int pid = 0, string pname = "") : id(pid), name(pname) {}
        virtual void display() {}; // this function will be override below. for run-time polymorphism
};

class Employee : public Person
{
    private:
        double hourlyRate;
        int workHours;

    public:
        Employee(int eid = 0, string ename = "", double rate = 0.0, int hours = 0)
            : Person(eid, ename), hourlyRate(rate), workHours(hours) {}

        void display() override
        {
            cout << "Employee - " << endl;

            cout << "ID :" << id << endl;
            cout << "name :" << name << endl;

            cout << "Hourly Rate: Tk :" << hourlyRate << endl;
            cout << "Work Hours: " << workHours << endl;
            cout << "Monthly Salary: Tk :" << calculateSalary() << endl;
        }

        double calculateSalary()
        {
            double salary = hourlyRate * workHours;
            if (workHours > 160)
            { // Assuming 160 hours is standard
                int overtime = workHours - 160;
                salary += (overtime * hourlyRate * 0.5); // 50% bonus for overtime
            }
            return salary;
        }

        void setWorkHours(int hours)
        {
            if (hours < 0 || hours > 744) // 31*24=744
                throw string("Invalid work hours.");
            workHours = hours;
        }

        friend class Manager; //to access name for employee &emp in the below
};

class Manager : public Person
{
    public:
        Manager(int aid = 0, string aname = "") : Person(aid, aname) {}

        void updateWorkHours(Employee &emp, int newHours)  //& use na korle change hoy na
        {
            emp.setWorkHours(newHours);
            cout << "[Manager] Updated work hours for " <<emp.name << " to " << newHours << " hours.\n";
        }

        void viewEmployeeDetails(Employee &emp) // receive by reference
        {
            cout << "[Manager View] ";
            emp.display();
        }
};



// Function to load stats from file into static variables
void GetStaticValues()
{
    ifstream file("static_varible.txt");
    if (file.is_open())
    {
        file>>TotalOrders>>TotalSoldAmount;
        file.close();
    }
}

// Function to save stats from static variables to file
void SetStaticValues()
{
    ofstream file("static_varible.txt");
    if (file.is_open())
    {
        file<<TotalOrders<<" "<<fixed<<setprecision(2)<<TotalSoldAmount<<endl;
        file.close();
    }
}

int main()
{
    // Load previously saved static values from file
    GetStaticValues();
    
    // Predefined accounts for login system
    Manager_id Manager_id("manager", "1234");
    Customer_id Customer_id("customer", "abcd");
    Admin super("super", "9999");


    // Product Declarations
    Dairy Ditems[5] = {
        Dairy("Milk  ", 80, 5, 101),
        Dairy("Cheese ", 270, 20, 102),
        Dairy("Butter", 370, 17, 103),
        Dairy("Ghee  ", 200, 19, 104),
        Dairy("Bread ", 50, 12, 105)};

    Fruits Fitems[5] = {
        Fruits("Apple  ", 250, 100, 201),
        Fruits("Banana ", 60, 45, 202),
        Fruits("Orange ", 220, 200, 203),
        Fruits("Mango  ", 100, 120, 204),
        Fruits("Tomato ", 80, 570, 205)};

    Grocery Gitems[5] = {
        Grocery("Rice   ", 60, 99, 301),
        Grocery("Sugar  ", 120, 83, 302),
        Grocery("Oil    ", 100, 42, 303),
        Grocery("Lentil ", 120, 120, 304),
        Grocery("Flour  ", 50, 18, 305)};


    // Customer Declarations
    NewCustomer ncustomer[3] = {
        NewCustomer("Fahad", 2310051),
        NewCustomer("Kahim", 1002),
        NewCustomer("Amena", 1003)};

    RegularCustomer rcustomer[3] = {
        RegularCustomer("Amit", 2310042),
        RegularCustomer("Ashraf", 2002),
        RegularCustomer("Rafi", 2003)};

    VIPcustomer vcustomer[3] = {
        VIPcustomer("Tanvir", 2310057),
        VIPcustomer("Shishir", 3002),
        VIPcustomer("Sharif", 3003)};

    while (1)
    {
        cout<< "\n=== Welcome To Amader Bazar Supershop ===\n";
        cout<< "Please login to use our services\n\n";
        string uid, pass;
        cout<< "Enter username: ";
        cin>> uid;
        if (uid == "0")
        {
            return 0;
        }
        else if(uid=="customer")
        {
            pass="abcd";
        }
        else{
        cout << "Enter password: ";
        cin >> pass;
        }

        if (Manager_id.authenticate(uid, pass))
        {
            cout << "Login successful (Manager_id)\n";
            Manager_id.dashboard();
        }

        else if (Customer_id.authenticate(uid, pass))
        {
            cout << "Login successful (Customer_id)\n";
            Customer_id.dashboard();
        }

        else if (super.authenticate(uid, pass))
        {
            cout<< "Login successful (Admin)\n";
            super.dashboard();
            cout<< "Enter your choice: ";
            int n;
            cin>> n;
            if (n == 1)
            {
                Manager_id.dashboard();
            }
            else if (n == 2)
            {
                Customer_id.dashboard();
            }
        }
        else
        {
            cout << "Invalid username or password!\n";
        }

        // Decide login id
        if (Manager_id.get_flag())
        {
            while (Manager_id.get_flag())
            {
                cout<< "1. View Product" << endl;
                cout<< "2. Update Stock" << endl;
                cout<< "3. Discount Offer" << endl;
                cout<< "4. Employee salary Calculation" << endl;
                cout<< "5. Write Message to Customers" << endl;
                cout<< "6. View All Orders" << endl;
                cout<< "Enter '0' for Logout" << endl;

                cout << "Enter: ";
                int num;
                cin >> num;

                
                if (num==1)  // Display All Items
                {
                    cout << "=== PRODUCTS BY CATEGORY ===" << endl;
                    cout << "\n\t--- Dairy Items ---" << endl;
                    cout << "ID\tName\tPrice(Tk)\tStock" << endl;
                    show(Ditems);
                    cout << "\n\t--- Fruit Items ---" << endl;
                    cout << "ID\tName\tPrice(Tk)\tStock" << endl;
                    show(Fitems);
                    cout << "\n\t--- Grocery Items ---" << endl;
                    cout << "ID\tName\tPrice(Tk)\tStock" << endl;
                    show(Gitems);
                }

                // Update Stock Quantity
                else if (num == 2)
                {
                    cout<< "Enter the id of product: ";
                    int code;
                    cin>> code;
                    cout<< "Enter the New Quantity: ";
                    int newQuantity;
                    cin>> newQuantity;
                    for (int i=0; i<5; i++)
                    {
                        if (Ditems[i].getid() == code)                    //cheking input id with Dairy Product
                        {
                            if (Ditems[i].quantity + newQuantity >= 0)
                            {
                                Ditems[i].quantity += newQuantity;
                                cout << "Stock Updated." << endl;          //Update Stock
                            }
                            else
                            {
                                cout << "Inavild Input!" << endl;
                            }
                        }

                        else if (Fitems[i].getid()==code)                   //cheking input id with Fresh Product
                        {
                            if (Fitems[i].quantity + newQuantity >= 0)
                            {
                                Fitems[i].quantity += newQuantity;             //Update Stock
                                cout << "Stock Updated." << endl;
                            }
                            else
                            {
                                cout << "Inavild Input!" << endl;
                            }
                        }

                        else if (Gitems[i].getid()==code)
                        {
                            if (Gitems[i].quantity + newQuantity >= 0)          //cheking input id with Grocery Product
                            {
                                Gitems[i].quantity += newQuantity;              //Update Stock
                                cout << "Stock Updated." << endl;
                            }                                                    
                            else
                            {
                                cout << "Inavild Input!" << endl;
                            }
                        }
                    }
                }

                // Update Discount Percent
                else if (num == 3)
                {
                    cout<< "Catagory of Products: " << endl;
                    cout<< "1.Dairy Products" << endl;
                    cout<< "2.Fruits Product" << endl;
                    cout<< "3.Grocery Products" << endl;
                    cout<< "In which catagory want to make dicount: ";
                    int cat;
                    double dis;
                    cin>> cat;
                    cout<<"How many percent?: ";
                    cin>> dis;
                    for (int i=0; i<5; i++)
                    {
                        if (cat == 1)
                        {
                            Ditems[i].change_price(dis);
                        }

                        else if (cat == 2)
                        {
                            Fitems[i].change_price(dis);
                        }

                        else if (cat == 3)
                        {
                            Gitems[i].change_price(dis);
                        }

                        else
                        {
                            cout<< "Invalid Input"<<endl;
                        }
                    }
                    if (cat==1 || cat==2 || cat==3)
                    {
                        cout<< "Price Updated."<<endl;
                    }
                }

                // Salary Calculation
                else if (num == 4)
                {
                    try
                    {
                        int n;
                        cout<< "Enter number of employees: ";
                        cin>>n;

                        if (n<=0)
                        {
                            throw string("Number of employees must be positive.");
                        }

                        Employee *employees = new Employee[n]; // dynamically creating array of object for employee

                        for (int i=0; i<n; i++)
                        {
                            int id, hours;
                            string name;
                            double rate;

                            cout<< "\nEnter details for Employee " << i + 1 << ":\n";
                            cout<< "ID: ";
                            cin>> id;
                            cin.ignore(); // Clears newline. if i dont use it name will skip to input
                            cout<< "Name: ";
                            getline(cin, name); // getline reads the entire line until a newline is found
                            cout<< "Hourly Rate: Tk";
                            cin>> rate;
                            cout<< "Work Hours: ";
                            cin>> hours;

                            if (name.empty())
                            {
                                throw string("Name cannot be empty.");
                            }
                            for (int j=0; j<name.size(); j++)
                            {
                                char c = name[j];
                                if (!((c >= 'A' && c <= 'Z') ||
                                      (c >= 'a' && c <= 'z') ||
                                      c == ' '))
                                {
                                    throw string("Name must contain only letters and spaces.");
                                }
                            }

                            if (rate<0)
                            {
                                throw string("Hourly rate cannot be negative.");
                            }
                            if (hours<0 || hours>744)
                            {
                                throw string("Working hour is invalid");
                            }

                            employees[i] = Employee(id, name, rate, hours);
                        }

                        Manager Manager(1, "Amit");

                        cout<< "\n--- Employee Details ---\n";
                        for (int i=0; i<n; ++i)
                        {
                            Manager.viewEmployeeDetails(employees[i]);
                        }

                        // Manager updates work hours
                        int index, newHours;
                        cout<< "\nEnter employee index to update work hours (0 to " << n - 1 << "): ";
                        cin>> index;
                        cout<< "Enter new work hours: ";
                        cin>> newHours;

                        if (index<0 || index>=n)
                        {
                            throw string("Invalid employee index.");
                        }

                        Manager.updateWorkHours(employees[index], newHours);
                        Manager.viewEmployeeDetails(employees[index]);

                        delete[] employees;
                    }
                    catch (string e)
                    {
                        cout<<"Error: "<<e<<endl;
                    }
                }

                // Send Message to Customer
                else if(num==5)
                {
                    try
                    {
                        cout<< "=== Write Message to Your Customers===\n";
                        cout<< "Enter your message: ";
                        cin.ignore();
                        string message;
                        getline(cin, message);

                        if (message.empty())
                        {
                            throw string("Message cannot be empty!");
                        }

                        // Get current time
                        time_t now=time(0);           // stores the seconds after 1970 in now
                        char *TimeString=ctime(&now); // converts seconds to human recongnizable format (Day Month Date Time Year)
                        string time=TimeString;       // ctime adds newline. We need to replace it with null character
                        time.pop_back();                // removes the new line added by ctime function

                        // Open file for writing (append mode)
                        ofstream file("messages.txt", ios::app);
                        if(file.is_open() == false)
                        {
                            throw string("Could not open file for writing!");
                        }

                        // Write time and message to file
                        file<<"Date & Time: " <<time<<endl;
                        file<<"Message: " <<message<<endl;
                        file<<"----------------------------------------" << endl;
                        file.close();

                        cout<< "Message successfully sent to customers" << endl;
                        cout<< "Time: " << time << endl;
                    }
                    catch (string e)
                    {
                        cout<<"Error: "<<e<<endl;
                    }
                }

                // Check Order History
                else if (num == 6)
                {
                    try
                    {
                        // Load stats from file into static variables
                        GetStaticValues();
                        cout<<"\n=== ALL ORDERS HISTORY ==="<<endl;

                        ifstream OrderFile("orders.txt");
                        if (OrderFile.is_open() == false)
                        {
                            throw string("Could not open orders file!");
                        }

                        string line;
                        bool ordersFound = false;

                        while(1)
                        {
                            if (!getline(OrderFile, line))
                                break;  // Exit when EOF or error occurs
                            
                            cout<<line<<endl;
                            ordersFound=true;
                        }

                        if (ordersFound==false)
                        {
                            cout<< "No orders available." << endl;
                        }
                        else
                        {
                            cout<< "\n--- SUMMARY ---" << endl;
                            cout<< "Total Number of Orders: " << TotalOrders << endl;
                            cout<< "Total Sold Amount: " << fixed << setprecision(2) << TotalSoldAmount << " Tk" << endl;
                        }

                        OrderFile.close();
                        cout << "=========================" << endl;
                    }
                    catch (string e)
                    {
                        cout<<"Error: "<<e<<endl;
                    }
                }

                // Logout
                else if (num==0)
                {
                    Manager_id.set_flag(0);
                }

                // No valid option given inside Stock Management
                else
                {
                    cout << "Invalid input";
                }
            }
        }

        // Customer ID
        while (Customer_id.get_flag())
        {
            try
            {
                cout<< "1. Order Processing"<<endl;
                cout<< "2. Inbox"<<endl;
                cout<< "'0' to logout"<<endl;
                cout<< "Enter your option: ";
                int choice;
                cin>>choice;
                if (choice<0 || choice>2)
                {
                    throw string("Invalid Choice!");
                }

                if (choice==1) // Order Processing
                {
                    cout << "Enter Customer Name: ";
                    string customer;
                    cin.ignore();
                    getline(cin, customer);

                    // Validate customer name
                    if (customer.empty())
                    {
                        throw string("Customer name cannot be empty!");
                    }

                    cout<<"Enter Customer ID: ";
                    int customerid;
                    cin>>customerid;


                    double TotalCost= 0;
                    string orderSummary= "";
                    char BuyMoreResponse= 'y';

                    while (BuyMoreResponse=='y' || BuyMoreResponse=='Y')
                    {
                        try
                        {
                            // Display All Products
                            cout<< "=== PRODUCTS BY CATEGORY ===" << endl;
                            cout<< "\n\t--- Dairy Items ---" << endl;
                            cout<< "ID\tName\tPrice(Tk)\tStock" << endl;
                            show(Ditems);
                            cout<< "\n\t--- Fruit Items ---" << endl;
                            cout<< "ID\tName\tPrice(Tk)\tStock" << endl;
                            show(Fitems);
                            cout<< "\n\t--- Grocery Items ---" << endl;
                            cout<< "ID\tName\tPrice(Tk)\tStock" << endl;
                            show(Gitems);

                            cout<< "Enter Product ID: ";
                            int productid;
                            cin>> productid;


                            cout<< "Enter Product Quantity: ";
                            int quantity;
                            cin>> quantity;

                            // Validate quantity input
                            if (quantity<=0)
                            {
                                throw string("Invalid quantity! Please enter a valid positive number.");
                            }

                            double cost=0;
                            string name;
                            int flag=0;

                            // Check Dairy items
                            for (int i=0; i<5; i++)
                            {
                                if (productid==Ditems[i].getid())
                                {
                                    name= Ditems[i].getname();
                                    if (Ditems[i].quantity >= quantity)
                                    {
                                        Ditems[i].quantity -= quantity;
                                        cost= quantity * Ditems[i].getprice();
                                        flag= 1;
                                    }
                                    else
                                    {
                                        throw string("Insufficient stock for " + name + "! Available: " + to_string(Ditems[i].quantity));
                                    }
                                    break;
                                }
                            }

                            // Check Fruits items
                            for (int i=0; i<5; i++)
                            {
                                if (productid==Fitems[i].getid())
                                {
                                    name= Fitems[i].getname();
                                    if (Fitems[i].quantity >= quantity)
                                    {
                                        Fitems[i].quantity -= quantity;
                                        cost= quantity * Fitems[i].getprice();
                                        flag= 1;
                                    }
                                    else
                                    {
                                        throw string("Insufficient stock for "+name+"! Available: " + to_string(Fitems[i].quantity));
                                    }
                                    break;
                                }
                            }

                            // Check Grocery items
                            for (int i=0; i<5; i++)
                            {
                                if (productid==Gitems[i].getid())
                                {
                                    name= Gitems[i].getname();
                                    if (Gitems[i].quantity >= quantity)
                                    {
                                        Gitems[i].quantity -= quantity;
                                        cost= quantity * Gitems[i].getprice();
                                        flag= 1;
                                    }
                                    else
                                    {
                                        throw string("Insufficient stock for "+name+"! Available: "+to_string(Gitems[i].quantity));
                                    }
                                    break;
                                }
                            }

                            if (flag==1 && cost>0)
                            {
                                TotalCost += cost;
                                char costStr[20];
                                sprintf(costStr, "%.2f", cost); //C-Style formating function (destination, format_string, value)
                                orderSummary += name + " x" +to_string(quantity)+ " = "+string(costStr)+" Tk\n";
                                cout<<"\nItem added to cart: "<<name<<" x"<<quantity << " = " << fixed<<setprecision(2)<<cost<<" Tk"<<endl;
                            }
                            else if (flag==0)
                            {
                                throw string("Product not found!");
                            }
                        }
                        catch (string e)
                        {
                            cout<< "Error: "<<e<<endl;
                            cout<< "Please try again with valid input." << endl;
                        }

                        cout<< "\nDo you want to buy more items? (y/n): ";
                        cin>> BuyMoreResponse;
                    }

                    // Final Order Summary
                    if (TotalCost>0)
                    {
                        // Determine customer type and discount rate using customer objects and their attributes
                        double discountRate= 0;
                        string customerType= "New Customer";

                        // Check if customer is a New Customer and get discount from object
                        for (int i = 0; i < 3; i++)
                        {
                            if (customerid==ncustomer[i].getId())
                            {
                                discountRate= ncustomer[i].getDiscountRate(TotalCost); // Get discount from NewCustomer object with total cost
                                customerType= "New Customer";
                                break;
                            }
                        }

                        // Check if customer is a Regular Customer and get discount from object
                        for (int i=0; i<3; i++)
                        {
                            if (customerid==rcustomer[i].getId())
                            {
                                discountRate= rcustomer[i].getDiscountRate(TotalCost); // Get discount for Regular Customer
                                customerType= "Regular Customer";
                                break;
                            }
                        }

                        // Check if customer is a VIP Customer and get discount from object
                        for (int i=0; i<3; i++)
                        {
                            if (customerid==vcustomer[i].getId())
                            {
                                discountRate= vcustomer[i].getDiscountRate(TotalCost); // Get discount for VIP customer
                                customerType= "VIP Customer";
                                break;
                            }
                        }

                        double discountAmount= (discountRate/100.0) * TotalCost; //uses double division not int division
                        double finalAmount= TotalCost - discountAmount;

                        cout<< "\n======= FINAL ORDER SUMMARY ======="<<endl;
                        cout<< "Customer: " << customer<<endl;
                        cout<< "Customer ID: " << customerid<<endl;
                        cout<< "Customer Type: " << customerType<<endl;
                        cout<< "Items purchased:"<<endl;
                        cout<< orderSummary;
                        cout<< "-----------------------------------" <<endl;
                        cout<< "Subtotal: " <<fixed<<setprecision(2)<<TotalCost<<" Tk"<<endl;
                        if (discountRate > 0)
                        {
                            cout<< "Discount (" << discountRate << "%): -"<<fixed << setprecision(2) << discountAmount << " Tk" << endl;
                        }
                        cout<< "Final Amount: " << fixed << setprecision(2)<<finalAmount << " Tk" << endl;
                        cout<< "===================================" << endl;

                        // Save order to file
                        SaveOrderToFile(customer, customerid, customerType, orderSummary,
                                        TotalCost, discountAmount, finalAmount, discountRate);
                    }
                    else
                    {
                        cout<< "No items were purchased."<<endl;
                    }
                }

                if (choice==2) // read messages
                {
                    try
                    {
                        cout<< "\n=== CUSTOMER INBOX ==="<<endl;

                        ifstream file("messages.txt");
                        if (file.is_open() == false)
                        {
                            throw string("Could not open messages file!");
                        }

                        string line;
                        bool msgFlag=false;

                        while(1)
                        {
                            if(!getline(file, line)) break;
                            cout<<line<<endl;
                            msgFlag = true;
                        }

                        if (msgFlag==false)
                        {
                            cout<<"No messages available."<<endl;
                        }

                        file.close();
                        cout<< "======================="<<endl;
                    }
                    catch (string e)
                    {
                        cout<< "Error: "<<e<<endl;
                    }
                }

                if (choice==0)
                {
                    Customer_id.set_flag(0);
                }
            }

            catch(string e)
            {
                cout<<"Error: "<<e<<endl;
                cout<<"Returning to main menu."<<endl;
            }
        }
    }
}
```

## **Output :**
<p align="center">

## **Discussion :**
<img width="1057" height="707" alt="image" src="https://github.com/user-attachments/assets/8ba55fa2-018a-4a48-8212-cfdca6fa060d" />
<img width="1506" height="511" alt="image" src="https://github.com/user-attachments/assets/bc9f5c12-ab95-4f02-9c7e-9eb660f2a573" />
<img width="1441" height="722" alt="image" src="https://github.com/user-attachments/assets/9eb6f0dd-7e65-43fd-972b-7d982010cdff" />
<img width="905" height="466" alt="image" src="https://github.com/user-attachments/assets/7c9668e3-626e-473a-a1c5-44726ba5b1ce" />
<img width="651" height="691" alt="image" src="https://github.com/user-attachments/assets/ed379712-e27f-4396-b779-dcf9abc189d2" />









