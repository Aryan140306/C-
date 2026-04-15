# C and c++
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
```cpp
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
```
##Use Case : Employee Salary Management System Using File Handling

Scenario: You need to build an employee salary management system that reads employee records from a file, calculates their salary, and writes the updated data back to the file.

Tasks:

Create an Employee class with attributes like employee_id, name, and salary.
Implement a method calculateSalary() which calculates salary based on some business logic (e.g., bonuses, deductions).
Use file handling to:
Read employee data from a text file (ifstream).
Write updated employee data back to the file (ofstream).
Implement a main function that loads employee records from the file, calculates their salary, and saves the updated records back to the file.

Approach:

File Handling: Use ifstream to read the employee data and ofstream to write the data back after processing.
Object-Oriented Design: Use a class to represent employees and encapsulate their data.
Exception Handling: Implement error checking to ensure the file exists and is accessible.
```cpp
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
using namespace std;

class Employee {
private:
    int employee_id;
    string name;
    float basic_salary;
    float bonus;
    float deductions;
    float net_salary;

public:
    // Constructor
    Employee(int id, string n, float basic, float b, float d) {
        employee_id = id;
        name = n;
        basic_salary = basic;
        bonus = b;
        deductions = d;
        net_salary = 0;
    }

    // Calculate salary
    void calculateSalary() {
        net_salary = basic_salary + bonus - deductions;
    }

    // Display employee details
    void displayEmployee() {
        cout << "ID: " << employee_id << ", Name: " << name
             << ", Net Salary: " << net_salary << endl;
    }

    // Write employee data to file
    void writeToFile(ofstream &outFile) {
        outFile << employee_id << " " << name << " "
                << basic_salary << " " << bonus << " "
                << deductions << " " << net_salary << endl;
    }
};

// Function to load employees from file
vector<Employee> loadEmployees(string filename) {
    ifstream inFile(filename);
    vector<Employee> employees;

    if (!inFile) {
        cerr << "Error: Could not open file " << filename << endl;
        return employees;
    }

    int id;
    string name;
    float basic, bonus, deductions;

    while (inFile >> id >> name >> basic >> bonus >> deductions) {
        Employee emp(id, name, basic, bonus, deductions);
        employees.push_back(emp);
    }

    inFile.close();
    return employees;
}

int main() {
    // Load employees from file
    vector<Employee> employees = loadEmployees("employees.txt");

    // Calculate salary for each employee
    for (auto &emp : employees) {
        emp.calculateSalary();
        emp.displayEmployee();
    }

    // Write updated records to new file
    ofstream outFile("updated_employees.txt");
    if (!outFile) {
        cerr << "Error: Could not open output file." << endl;
        return 1;
    }

    for (auto &emp : employees) {
        emp.writeToFile(outFile);
    }

    outFile.close();
    cout << "\nUpdated employee records written to updated_employees.txt" << endl;

    return 0;
}
```
## 
Use Case: Tic-Tac-Toe Game with Classes and Object-Oriented Design

Scenario: Develop a Tic-Tac-Toe game using object-oriented design principles. The game should allow two players to take turns, check for a winner, and reset the game.

Tasks:

Create a Game class with a board (a 3x3 matrix), turn (to keep track of whose turn it is), and winner (to determine the winner).
Implement methods for:
resetGame(): Resets the board.
makeMove(): Places a mark on the board.
checkWinner(): Checks if there is a winner.
printBoard(): Displays the current state of the board.
Implement game logic to alternate between players and check if a player wins or if it’s a draw.

Approach:

Classes/Objects: Use a class to encapsulate game-related data and methods.
Encapsulation: Keep game data (board, winner, turn) private inside the class.
Polymorphism: You could also extend this with different game modes (e.g., player vs AI).
```cpp
#include <iostream>
using namespace std;

class Game {
private:
    char board[3][3];
    char turn;
    char winner;

public:
    // Constructor
    Game() {
        resetGame();
    }

    // Reset the game
    void resetGame() {
        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                board[i][j] = ' ';
        turn = 'X';   // X always starts
        winner = ' ';
    }

    // Print the board
    void printBoard() {
        cout << "\n";
        for (int i = 0; i < 3; i++) {
            cout << " ";
            for (int j = 0; j < 3; j++) {
                cout << board[i][j];
                if (j < 2) cout << " | ";
            }
            cout << "\n";
            if (i < 2) cout << "---+---+---\n";
        }
        cout << "\n";
    }

    // Make a move
    bool makeMove(int row, int col) {
        if (row < 0 || row >= 3 || col < 0 || col >= 3) {
            cout << "Invalid move! Try again.\n";
            return false;
        }
        if (board[row][col] != ' ') {
            cout << "Cell already occupied! Try again.\n";
            return false;
        }
        board[row][col] = turn;
        checkWinner();
        turn = (turn == 'X') ? 'O' : 'X'; // alternate turn
        return true;
    }

    // Check for winner or draw
    void checkWinner() {
        // Check rows and columns
        for (int i = 0; i < 3; i++) {
            if (board[i][0] != ' ' && board[i][0] == board[i][1] && board[i][1] == board[i][2])
                winner = board[i][0];
            if (board[0][i] != ' ' && board[0][i] == board[1][i] && board[1][i] == board[2][i])
                winner = board[0][i];
        }
        // Check diagonals
        if (board[0][0] != ' ' && board[0][0] == board[1][1] && board[1][1] == board[2][2])
            winner = board[0][0];
        if (board[0][2] != ' ' && board[0][2] == board[1][1] && board[1][1] == board[2][0])
            winner = board[0][2];
    }

    // Get winner
    char getWinner() {
        return winner;
    }

    // Check if board is full (draw)
    bool isDraw() {
        if (winner != ' ') return false;
        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[i][j] == ' ')
                    return false;
        return true;
    }
};

int main() {
    Game game;
    int row, col;

    cout << "Welcome to Tic-Tac-Toe!\n";
    game.printBoard();

    while (game.getWinner() == ' ' && !game.isDraw()) {
        cout << "Player " << (game.getWinner() == ' ' ? (game.isDraw() ? ' ' : game.getWinner()) : 'X') << "'s turn.\n";
        cout << "Enter row and column (0-2): ";
        cin >> row >> col;
        game.makeMove(row, col);
        game.printBoard();
    }

    if (game.getWinner() != ' ')
        cout << "Player " << game.getWinner() << " wins!\n";
    else
        cout << "It's a draw!\n";

    return 0;
}
```
