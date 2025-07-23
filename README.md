# Login-System
#include <cs50.h>
#include <stdio.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>

bool is_valid_user(string username);
bool is_valid_pass(string password);

int main(void)
{
    string username = get_string("Username: ");
    string password = get_string("Password: ");
    
    if (is_valid_user(username) && is_valid_pass(password))
    {
        printf("Login successful!\n");
    }
    else
    {
        printf("Invalid credentials!\n");
    }
}

bool is_valid_user(string username)
{
    return strlen(username) >= 3;
}

bool is_valid_pass(string password)
{
    bool has_upper = false;
    bool has_lower = false;
    bool has_digit = false;
    
    for (int i = 0; i < strlen(password); i++)
    {
        if (isupper(password[i]))
        {
            has_upper = true;
        }
        else if (islower(password[i]))
        {
            has_lower = true;
        }
        else if (isdigit(password[i]))
        {
            has_digit = true;
        }
    }
    
    return has_upper && has_lower && has_digit && strlen(password) >= 6;
}
