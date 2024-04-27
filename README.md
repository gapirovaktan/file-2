#include using namespace std;

double multiply(double a, double b) {
return a * b;
}

double divide(double a, double b) {
if (b == 0) {
cout << "Error: Division by zero!" << endl;
return 0;
}
return a / b;
}

double add(double a, double b) {
return a + b;
}

double subtract(double a, double b) {
return a - b;
}

double squareRoot(double a) {
if (a < 0) {
cout << "Error: Cannot compute square root of a negative number!" << endl;
return 0;
}
return sqrt(a);
}

double absoluteValue(double a) {
return abs(a);
}

double powerNum(double a, double b) {
return pow(a, b);
}

int main() {
double num1, num2;
char op;
string input;
vector total;

cout << "Welcome to the Calculator!" << endl;
do {
if (input == "h") {
cout << "History of calculations:" << endl;
for (const string& calc : total) {
cout << calc << endl;
}
}
cout << "Enter arithmetic expression: ";
getline(cin, input);

total.push_back(input);

istringstream iss(input);
iss >> num1;

while (iss >> op >> num2) {
switch (op) {
case '+':
num1 = add(num1, num2);
break;
case '-':
num1 = subtract(num1, num2);
break;
case '*':
num1 = multiply(num1, num2);
break;
case '/':
num1 = divide(num1, num2);
break;
case '^':
num1 = powerNum(num1, num2);
break;
case '#':
num1 = squareRoot(num1);
break;
default:
cout << "Error: Invalid operator '" << op << "'" << endl;
}
}
total.push_back(input + " = " + to_string(num1));
cout << "Result: " << num1 << endl;

cout << "Do you want to continue (Y/N/H)? ";
getline(cin, input);
} while (input == "Y"  input == "y"  input == "h");

cout << "Thank you for using the Calculator!" << endl;

return 0;
}
