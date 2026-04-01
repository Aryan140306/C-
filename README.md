# C-
## Struct
Help us to create a user defined datatype of different sizes.\
We can not give value to any variable in structure \
we can make array of variable length eg(char ch[6])\
Indexing starts from zero .


## Size of different data types
int-2 byte\
float-4 byte\
char- 1 byte\
pointer variable-2 byte

## Nested Structure 
we can call a struct in another struct 

## Use of different symbols
### *
  eg( * a  ) value in a , (int* a) this means a is pointer variable 
### &
  eg(&b) means address of b
### →
 eg(p→a) means *p.a
### ++
only moves 1 byte at once\
++ before a variable will do incriment defore the operation or initialisation and ++ after the variable will be initisized after gaining the value 
### -- 
works similar to ++ and it's function is to decrease 1 byte 
### P+=1 is equal to P= P+1


## How to assign value to variables defined in struct
* we can not assign value directly in struct so we write valued in(let struct b)\
*eg- struct b s1={abc,1 , 1.3 etc.}\
*in {}write valued according to data type defined in struct

## Output of different data type 
For output of any datatype we use 
### %S for output in string
eg- print(%s, P[0]i)
### %d for integer (int)
eg- print(%d, P[0]i)
### %c for char
eg- print(%c, P[0]i)
## Pointer
Pointer will move with the size of struct at once\
for eg if struct is if size 6 so pointer will move from 1000 to 1006 and then to 1012
## Alias name 
We can name our struct as a single variable by using →type def\
eg→ type def struct S1 {\
                char a\
                int b\
                }t;\
now we can call struct S1 by just writing t
## Void
It's return type can be any data type\
eg→Void f1(t,s) for any function f1 
 
## Call by Value
in this we pass struct variable in function call\
By that we work locally on struct and do not change our global struct 
## Call by Refrence 
in this we pass address of struct while function call\
by this we will make changes in global struct by bringing change in address
 
## Associativity
Operators with the same precedence are evaluated based on their associativity. Unary operators (++, * , &) have right-to-left associativity, while the binary multiplication operator (*) has left-to-right associativity. 
## size of
this function is used to know size of struct or an element inside struct
eg- print(%d,size of(s[0]))
# C++ questions
## Use Case : Student Record System with Classes and Objects

Scenario: You need to develop a student record management system for a college. The system should allow the addition of student records, modification, and display of records, as well as calculations like average grades.

Tasks:

Class Design: Create a Student class with data members like roll_number, name, and marks. Implement a constructor to initialize student records when an object is created and a destructor to clean up resources if needed. Include methods like addStudent(), modifyStudent(), displayStudent(), and calculateAverage(). Use overloaded constructors to initialize students with different data (e.g., full info vs just roll number).

Approach:

Class and objects: Use a class to represent the student, encapsulating the details of each student. Inheritance: You could extend this to have subclasses like GraduateStudent or UndergraduateStudent, which inherit from Student and add more specialized data. Polymorphism: Use method overloading for various operations like addStudent() (with different types of arguments).

#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Student {
private:
    int rollno;
    string name;
    vector<float> marks;

public:
    // Default constructor
    Student() {
        rollno = 0;
        name = "Unknown";
    }

    // Constructor with roll number, name, and marks
    Student(int r, string n, vector<float> m) {
        rollno = r;
        name = n;
        marks = m;
    }

    // Constructor with roll number only
    Student(int r) {
        rollno = r;
        name = "Not Assigned";
    }

    // Destructor
    ~Student() {
        cout << "Destructor called for roll no: " << rollno << endl;
    }

    // Method to add student details
    void addStudent() {
        cout << "Enter student details (roll no, name, number of subjects): ";
        int subjects;
        cin >> rollno >> name >> subjects;
        marks.clear();
        cout << "Enter marks: ";
        for (int i = 0; i < subjects; i++) {
            float m;
            cin >> m;
            marks.push_back(m);
        }
    }

    // Modify student details
    void modifyStudent(string newName, vector<float> newMarks) {
        name = newName;
        marks = newMarks;
    }

    // Display student details
    void displayStudent() {
        cout << "Roll No: " << rollno << endl;
        cout << "Name: " << name << endl;
        cout << "Marks: ";
        for (float m : marks) cout << m << " ";
        cout << endl;
        cout << "Average: " << calculateAverage() << endl;
    }

    // Calculate average marks
    float calculateAverage() {
        if (marks.empty()) return 0;
        float sum = 0;
        for (float m : marks) sum += m;
        return sum / marks.size();
    }
}

int main() {
    Student s1;
    s1.addStudent();
    s1.displayStudent();

    vector<float> newMarks = {90, 85, 88};
    s1.modifyStudent("Updated Name", newMarks);
    cout << "\nAfter modification:\n";
    s1.displayStudent();

    return 0;
}






