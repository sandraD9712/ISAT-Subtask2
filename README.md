adding conversation functions and menu
#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>
using namespace std;

// Decimal to Binary
string decToBin(int n) {
    if (n == 0) return "0";
    string b = "";
    while (n > 0) {
        b = char('0' + n % 2) + b;
        n /= 2;
    }
    return b;
}

// Binary to Decimal
int binToDec(string b) {
    int n = 0;
    for (char c : b)
        n = n * 2 + (c - '0');
    return n;
}

// Decimal to Hexadecimal
string decToHex(int n) {
    if (n == 0) return "0";
    string h = "";
    string digits = "0123456789ABCDEF";

    while (n > 0) {
        h = digits[n % 16] + h;
        n /= 16;
    }
    return h;
}

// Hexadecimal to Decimal
int hexToDec(string h) {
    int n = 0;

    for (char c : h) {
        int value;

        if (c >= '0' && c <= '9')
            value = c - '0';
        else
            value = toupper(c) - 'A' + 10;

        n = n * 16 + value;
    }

    return n;
}

int main() {
    srand(time(0));

    int choice;

    do {
        cout << "\nConversion Menu:\n";
        cout << "1. Convert Decimal to Binary\n";
        cout << "2. Convert Binary to Decimal\n";
        cout << "3. Convert Hexadecimal to Decimal\n";
        cout << "4. Convert Decimal to Hexadecimal\n";
        cout << "5. Demo\n";
        cout << "6. Exit\n";
        cout << "Enter your choice (1-6): ";
        cin >> choice;

        switch (choice) {

            case 1: {
                int n;
                cout << "Enter a decimal number: ";
                cin >> n;
                cout << "Binary representation: " << decToBin(n) << endl;
                break;
            }

            case 2: {
                string b;
                cout << "Enter a binary number: ";
                cin >> b;
                cout << "Decimal representation: " << binToDec(b) << endl;
                break;
            }

            case 3: {
                string h;
                cout << "Enter a hexadecimal number: ";
                cin >> h;
                cout << "Decimal representation: " << hexToDec(h) << endl;
                break;
            }

            case 4: {
                int n;
                cout << "Enter a decimal number: ";
                cin >> n;
                cout << "Hexadecimal representation: " << decToHex(n) << endl;
                break;
            }

            case 5: {
                int n = rand() % 100;
                cout << "Generated random integer: " << n << endl;
                cout << "Binary representation: " << decToBin(n) << endl;
                break;
            }

            case 6:
                cout << "Exiting the program." << endl;
                break;

            default:
                cout << "Invalid choice." << endl;
        }

    } while (choice != 6);

    return 0;
}
