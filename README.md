#include <iostream>
#include <string>
#include <windows.h>
using namespace std;

float accBal;
int pin;
string accName;
float amount;

void cyan() {
    HANDLE h= GetStdHandle (STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h,11);
}

void red() {
    HANDLE h= GetStdHandle (STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h,12);
}

void green() {
    HANDLE h= GetStdHandle (STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h,2);
}

void yellow() {
    HANDLE h= GetStdHandle (STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(h,6);
}

void login () {
    while(true){
    cout << "Enter Name: ";
    getline(cin, accName);
    if(accName == "Joshua"){
        break;
    }
    else {
        system("cls");
        cout << "Unknown Name\n";
        continue;
    }
    }
    while (true) {
        system("cls");
        cout << "Enter PIN: ";
        cin >> pin;
        if (pin == 1234) {
            cout << "Successfully Log In\n";
            break;
        }
        else {
            system("cls");
            cout << "Invalid PIN\n";
            continue;
        }
    }
}

void deposit() {
    while(true) {
    system("cls");
    cout << "Deposit: ";
    cin >> amount;
    if(amount > 0){
    accBal += amount;
    break;
}
else {
    system("cls");
    cout << "Invalid Amount\n";
    continue;
}
}
amount = 0;
}

void withdraw() {
    red();
    while(true){
        system("cls");
        cout << "Withdraw: ";
        cin >> amount;
        if (accBal > amount && amount < accBal){
            accBal -= amount;
            break;
        }
        else {
            system("cls");
            cout << "Not Enough Balance\n";
        }
    }
    amount = 0;
}


void balance() {
    system("cls");
    cout << "Name: " << accName << endl;
    cout << "Balance: " << accBal << endl;
}

void menu(){
    yellow();
    int choice;
    while(true){
        cout << "Welcome\n";
        cout << "1. Deposit\n2. Withdraw\n3. Balance\n3. Exit\n";
        cout << "Input: ";
        cin >> choice;
        
        switch(choice){
            case 1: deposit(); break;
            case 2: withdraw(); break;
            case 3: balance(); break;
            case 4: exit(1); break;
            default: 
            system("cls");
            cout << "Invalid Choice\n";
            continue;
        }
    }
}

int main() {
    cyan();
    login();
    green();
    deposit();
    menu();
}
