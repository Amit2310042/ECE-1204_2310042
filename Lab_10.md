<p align="center">
<img width="1873" height="706" alt="image" src="https://github.com/user-attachments/assets/ed265189-32cd-441a-b0f7-cc464d7563b6" />



## **Experiment No : 01**
## **Experiment Name :Find Maximum of Two Values.Create a generic function getMax(T a, T b) that returns the maximum of two values.**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
template <class T>
int get_max(T a, T b)
{
    if (a > b)
    {
        return a;
    }
    else
    {
        return b;
    }
}
int main()
{
    int i = 10, j = 23;
    cout << "Max value is " << get_max(i, j);
}
```
## **Output :**
<p align="center">




---------------------------



## **Experiment No : 02**
## **Experiment Name :Print Array Elements**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
template <class T>
void printArray(T arr[], int size)
{
    for (int i = 0; i < size; i++)
    {
        cout << arr[i] << " ";
    }
}
int main()
{
    cout << "Enter number of element" << endl;
    int n;
    cin >> n;
    cout << "Enter the elements" << endl;
    int prr[n];
    for (int i = 0; i < n; i++)
    {
        cin >> prr[i];
    }
    printArray(prr, n);
}
```
## **Output :**
<p align="center">
<img width="1855" height="527" alt="image" src="https://github.com/user-attachments/assets/14b40560-9cf0-44bf-bf79-599f614514eb" />



-------------------------


## **Experiment No : 03**
## **Experiment Name :Write a function template findMaxIndex(T arr[], int size) that returns the index of the maximum element in an array..**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
template <class T>
int find_Max(T arr[], int size)
{
    int ind = 0;
    int max_val = arr[0];
    for (int i = 0; i < size; i++)
    {
        if (arr[i] > max_val)
        {
            max_val = arr[i];
            ind = i;
        }
    }
    return ind;
}
int main()
{
    cout << "Enter number of element" << endl;
    int n;
    cin >> n;
    int prr[n];
    for (int i = 0; i < n; i++)
    {
        cin >> prr[i];
    }
    cout << "Max value index is " << find_Max(prr, n);
}

```
## **Output :**
<p align="center">
<img width="1827" height="527" alt="image" src="https://github.com/user-attachments/assets/15b8aa76-1779-48e4-aa0b-a04acc49cd0c" />




-----------------------




## **Experiment No : 04**
## **Experiment Name :Generic Function with Default Arguments.**
## **Submission Date :20 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
template <class T>
int multiply(T a, T b = 1)
{
    return a * b;
}
int main()
{
    int i = 10, j = 23;
    cout << "Multiply is : " << multiply(i);
}
```
## **Output :**
<p align="center">

<img width="1591" height="516" alt="image" src="https://github.com/user-attachments/assets/7f7ec003-24fb-4734-af4e-dce2bb18e019" />




------------------------



## **Experiment No : 05**
## **Experiment Name :Overloaded add() Function with Special Case.**
## **Submission Date : 20 August 2025**
---------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
template <class T1, class T2>
void add(T1 a, T2 b)
{
    cout << a + b << endl;
}
void add(const char *s1, const char *s2)
{
    cout << s1 << s2;
}

int main()
{
    add(5, 10);
    add("Hello,", "World!");
}

```
## **Output :**
<p align="center">
<img width="1585" height="525" alt="image" src="https://github.com/user-attachments/assets/a5c07cc5-8cfb-4aa7-80d6-66b2388dfade" />




----------------------


## **Experiment No : 06**
## **Experiment Name :Age Validation**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C
#include <bits/stdc++.h>
using namespace std;
void Age(int age)
{
    try
    {
        if (age < 0 || age > 150)
        {
            throw 1;
        }
        else
        {
            cout << "You age is :" << age << endl;
        }
    }
    catch (int i)
    {
        cout << "Invalid age entered" << endl;
    }
}
int main()
{
    cout << "Enter age " << endl;
    int a;
    cin >> a;
    Age(a);
}
```
## **Output :**
<p align="center">

<img width="1577" height="507" alt="image" src="https://github.com/user-attachments/assets/d19965de-62cf-442a-81e3-e113006ba0cd" />




-------------------------



## **Experiment No : 07**
## **Experiment Name :Student Marks Validation**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C

#include <bits/stdc++.h>
using namespace std;

class Invalid_Mark
{
public:
    string text;
    Invalid_Mark(string t) { text = t; }
};

int main()
{
    cout << "Enter marks of 5 subject.." << endl;
    int arr[5];
    for (int i = 0; i < 5; i++)
    {
        cin >> arr[i];
        try
        {
            if (arr[i] < 0 || arr[i] > 100)
            {
                throw Invalid_Mark("Invalid mark you entered");
            }
        }
        catch (Invalid_Mark e)
        {
            cout << e.text << endl;
        }
    }

    cout << "All mark is valid.Here is your mark.. " << endl;
    for (int i = 0; i < 5; i++)
    {
        cout << "Subject" << i + 1 << " " << arr[i] << endl;
    }
}


```
## **Output :**
<p align="center">
<img width="1582" height="885" alt="image" src="https://github.com/user-attachments/assets/ed91b19c-f39d-47f3-9592-0c98f77a6176" />


--------------------



## **Experiment No : 08**
## **Experiment Name :Nested Try-Catch Blocks.**
## **Submission Date : 20 August 2025**
----------

## **Code :**
```C
#include <iostream>
using namespace std;

int main()
{
    try
    {
        int num;

        cout << "Enter a number: ";
        cin >> num;

        if (cin.fail())
        {
            throw "Number Format Exception: Please enter numbers only!";
        }

        try
        {
            int divisor;
            cout << "Enter divisor: ";
            cin >> divisor;

            if (divisor == 0)
            {
                throw "Arithmetic Exception: Division by zero!";
            }

            int result = num / divisor;
            cout << "Result: " << result << endl;
        }
        catch (const char *msg)
        {
            cout << "Inner Catch  " << msg << endl;
        }
    }
    catch (const char *msg)
    {
        cout << "Outer Catch  " << msg << endl;
    }

        return 0;
}

```
## **Output :**
<p align="center">

<img width="1570" height="766" alt="image" src="https://github.com/user-attachments/assets/b231a5f6-780b-4c7d-9dae-dde7ccf07d98" />



--------------------






