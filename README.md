# Calderon_signinlogin.cpp

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    string user, pass, id, p;
    int choice;

    cout << "1. Register\n2. Login\nChoose: ";
    cin >> choice;

    if (choice == 1) {
        cout << "Enter username: ";
        cin >> user;
        cout << "Enter password: ";
        cin >> pass;

        ofstream file("records.txt", ios::app);
        file << user << " " << pass << endl;
        file.close();

        cout << "Registered!";
    }
    else if (choice == 2) {
        cout << "Enter username: ";
        cin >> user;
        cout << "Enter password: ";
        cin >> pass;

        ifstream file("records.txt");
        bool ok = false;
        while (file >> id >> p) {
            if (id == user && p == pass) {
                ok = true;
                break;
            }
        }
        file.close();

        if (ok)
            cout << "Login successful";
        else
            cout << "Login failed";
    }
    return 0;
}
