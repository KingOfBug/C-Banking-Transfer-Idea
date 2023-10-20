#include <iostream>
#include <string>
using namespace std;

float accBal;
int pin;
string accName;
float amount;

void login() {
while (true) {
cout << "Enter Name: ";
getline (cin, accName);
if (accName == "Bug"){
cout << "Welcome" << endl;
break;
} 
else {
system("cls");
cout << "Unknown Name\n";
continue;
}
}
}

void deposit(){
while (true){
system("cls");
cout << "Deposit: ";
cin >> amount;
if(amount > 0){
accBal += amount;
break;
}
else {
system("cls");
cout << "Invalid Amount" << endl;
continue;
}
}
amount = 0;
}

void withdraw() {
while(true){
system("cls");
cout << "Withdraw: ";
cin >> amount;
if(amount < accBal && accBal > amount){
cout << "Successfully";
break;
}
else {
system("cls");
cout << "Not Enough Balance\n";
continue;
}
}
amount = 0;
}

void balance() {
system("cls");
cout << "Name: " << accName << endl;
cout << "Balance: " << accBal << endl;
}

void menu() {
int choice;
system("cls");
cout << "Welcome To KingOfBug Company\n";
cout << "[1] Deposit\n[2] Withdraw\n[3] Balance\n[4] Exit\n";
cout << "Input: ";
cin >> choice;

switch (choice)

case 1: deposit(); break;
case 2: withdraw(); break;
case 3: balance(); break;
case 4: exit(1); break;
default:
system("cls");
cout << "Invalid Choice\n";
}

int main() {

login();
deposit();
menu();

return 0;
}
