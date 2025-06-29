# User Registration Validation System

This project implements a user account registration system for a mobile app, focusing on validating user inputs before creating accounts.

## Project Overview

As a junior developer in a startup, the task is to build a registration system that checks the validity of user-provided:

- Name  
- Email  
- Password  

Helper functions `validate_name`, `validate_email`, and `validate_password` are provided and used to perform these validations. These functions include docstrings explaining their behavior.

The registration system raises errors when inputs are invalid and stores user data when inputs are valid.

## Features

- Validation of names to ensure proper formatting  
- Email validation that checks for correct format and approved top-level domains  
- Password validation requiring complexity criteria  
- Error handling that informs users of invalid inputs  

## Code Snippet

```python
def validate_user(name, email, password):
    if validate_name(name) and validate_email(email) and validate_password(password):
        return True
    else:
        raise ValueError('Please re-check input.')

def register_user(name, email, password):
    try:
        if validate_user(name, email, password):
            return {'name': name, 'email': email, 'password': password}
    except:
        return False

# Example usage:
print(register_user('Kurt', 'kurt@email.xyz', 'Password123'))  # Invalid email
print(register_user('Kurt', 'kurt@gmail.com', 'password'))     # Invalid password
print(register_user('Kurt', 'kurt@gmail.com', 'Password123'))  # Valid credentials
```

## Links

- **DataCamp Project:** [Creating Functions to Register App Users](https://app.datacamp.com/learn/projects/2216)  
- **Learning Track:** [Python Programming Fundamentals](https://www.datacamp.com/completed/statement-of-accomplishment/track/6a449a8b71c60d608f60c140b350d5549be8643c)
