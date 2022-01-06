//# register-and-login
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

bool IsLogged()
{
    string username, password, un, pw;
    cout << "Enter username: " << endl;
    cin >> username;
    cout << "Enter password: " << endl;
    cin >> password;

    ifstream read("sample60.txt");
    getline(read, un);
    getline(read, pw);

    if (un == username && pw == password)
    {
        return true;
    }
    else
    {
        return false;
    }
}

int main()
{
    int choice;

    cout << "1 : Register\n2: Login\nYour choice: ";
    cin >> choice;
    if (choice == 1)
    {
        string username, password;

        cout << "Select a username: " << endl;
        cin >> username;
        cout << "Select a password: " << endl;
        cin >> password;

        ofstream file;
        file.open("sample60.txt");

        file << username << endl << password;
        file.close();
        main();
    }
    else if (choice == 2)
    {
        bool status = IsLogged();
        if (!status)
        {
            cout << "False login!" << endl;
            system("PAUSE");
            return 0;
        }
        else
        {
            cout << " Succesfully logged in!" << endl;
            system("PAUSE");
            return 1;
        }
    }
}
