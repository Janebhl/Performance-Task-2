//Performance Task 2:
//Description: Convertion Console App using function [Dollar to Peso to Dollar]
//              This is also a debugging activity
//Name: Jane Cristel Bohol

#include <iostream>
#include <iomanip>
#include <locale>
#include <conio.h>
#include <dirent.h>
#include <string>

using namespace std;

//function for monetary formatting
struct group_face: public numpunct <char> {
    protected:
        string do_grouping() const { 
            return "\03"; 
            }
};

// First function prototypes
void promptAndWait();

/* Functions takes two arguements: one float and one unsigned int.
    The unsigned int has a default value of 1. Function returns no value.*/
void dollarsToPeso (float rate, unsigned dollars);
void pesoToDollars (float r, unsigned p);
void showConversionRate (float cr);

int main() {
     //Declare the variables for theuser input.
     float conversionRate = 50.73; // $1 = 50.75 Pesos
     unsigned dollarsIn, pesoIn;
     int ch, ans = 0;
    do{
        system("cls");
        cout << endl;
        cout << "Dollar to Peso Conversion App" << endl << endl;
        cout << "[1] Dollar to Peso" << endl;
        cout << "[2] Peso to Dollar" << endl;
        cout << "[0] Exit the Conversion App" << endl;
        cout << "Select Conversion : ";
        cin >> ch;

        switch (ch){
            case 1: {
                cout <<"\n << Convert Dolllar to Peso >>" << endl;
                showConversionRate(conversionRate); // Show the exchange rate by calling the function.
                // Prompt the user and take US dollars input.*/
                cout << "Enter a US dollar amount (without the dollar sign, commas or a decimal): [####] ";
                cin >> dollarsIn;
                dollarsToPeso (conversionRate, dollarsIn); // Show the conversion by calling the function.
                promptAndWait(); // Call the promptAndWait() function.
                break;
            }
            case 2: {
                cout << "\n << Convert Peso to Dollar >>" <<endl;
                showConversionRate(conversionRate);
                cout << "Enter a PHP amount (without the peso sign, commas or a decimal): [####] ";
                cin >> pesoIn;
                pesoToDollars (conversionRate, pesoIn); // Show the conversion by calling the function.
                promptAndWait(); // Call the promptAndWait() function.
                break;
            }
            case 0: {
                promptAndWait();
                cout << "\nConversion App Terminated \nThank you for using the app!";
                return 0;
            }
            option: {
                cout << "Invalid Input!";
                promptAndWait();
            }
        }    
    }while (ans == 0);
} //End of main function
//Define the promtpAndWait() function.
void promptAndWait() {
    cin.ignore (100, '\n');
    cout << "\nPress Enter or Return to continue...";
    cin.get();
}

//Define the dollarsToPeso function.
void dollarsToPeso (float rate, unsigned dollar) {
    // Adjust the formatting.
    cout.setf(ios::fixed);
    cout.setf(ios::showpoint);
    cout.precision(2);

    // Print the results.
    cout.imbue(locale(cout.getloc(), new group_face));
    cout << "\n$ " << dollar << " US = " << (rate * dollar) << " Pesos. \n";
}
void showConversionRate (float cr){
    cout << "The rate of 1 dollar to peso is " << cr << endl;
}

void pesoToDollars(float r, unsigned p) {
    //adjust the formatting.
    cout.setf(ios::fixed);
    cout.setf(ios::showpoint);
    cout.precision(2);

    // Print the results.
    cout.imbue(locale(cout.getloc(), new group_face));
    cout << "\nPHP " << p << " = " << (p / r) << " dollars" << endl;
}
