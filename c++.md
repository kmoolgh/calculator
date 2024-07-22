# calculator
 C++ calculator program
#include <iostream>  
#include <limits>  

using namespace std;  

double add(double a, double b) { return a + b; }  
double subtract(double a, double b) { return a - b; }  
double multiply(double a, double b) { return a * b; }  
double divide(double a, double b) {   
    if (b == 0) {  
        throw runtime_error("Cannot divide by zero!");  
    }  
    return a / b;   
}  

void displayMenu() {  
    cout << "Simple Calculator" << endl;  
    cout << "Select an operation:" << endl;  
    cout << "1. Addition (+)" << endl;  
    cout << "2. Subtraction (-)" << endl;  
    cout << "3. Multiplication (*)" << endl;  
    cout << "4. Division (/)" << endl;  
    cout << "5. Exit" << endl;  
}  

void calculate() {  
    double num1, num2, result;  
    int choice;  

    while (true) {  
        displayMenu();  
        cout << "Enter your choice: ";  
        cin >> choice;  

        if (choice == 5) {  
            cout << "Exiting the calculator. Goodbye!" << endl;  
            break;  
        }  

        cout << "Enter two numbers: ";  
        while (!(cin >> num1 >> num2)) {  
            cout << "Invalid input. Please enter numbers: ";  
            cin.clear(); // clear the error flags  
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard invalid input  
        }  

        try {  
            switch (choice) {  
                case 1:  
                    result = add(num1, num2);  
                    cout << "Result: " << num1 << " + " << num2 << " = " << result << endl;  
                    break;  
                case 2:  
                    result = subtract(num1, num2);  
                    cout << "Result: " << num1 << " - " << num2 << " = " << result << endl;  
                    break;  
                case 3:  
                    result = multiply(num1, num2);  
                    cout << "Result: " << num1 << " * " << num2 << " = " << result << endl;  
                    break;  
                case 4:  
                    result = divide(num1, num2);  
                    cout << "Result: " << num1 << " / " << num2 << " = " << result << endl;  
                    break;  
                default:  
                    cout << "Invalid choice! Please select a valid operation." << endl;  
            }  
        } catch (const runtime_error& e) {  
            cout << "Error: " << e.what() << endl;  
        }  
    }  
}  

int main() {  
    calculate();  
    return 0;  
}  
