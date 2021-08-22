[![Python application test with Github Actions](https://github.com/AaronGonzalezB/scaffold/actions/workflows/main.yml/badge.svg)](https://github.com/AaronGonzalezB/scaffold/actions/workflows/main.yml)

# scaffold
Project scaffold for Python

## AWS Cloud9

### 1. Setup:

1.1. Create a Cloud9 Enviroment.

1.2. Create a github repo to link with the Cloud9 Enviroment.

1.3. Generate a SSH key inside the Cloud9 terminal:

  * `ssh-keygen -t rsa`
  * `cat /home/ec2-user/.ssh/id_rsa.pub ` - ssh key link.
  * Inside the Settings - SSH and GPG Keys - Create new SSH key with the same name of the Repo.

### 2. Project:

Create these files inside the Project scaffold (`touch` in Cloud9 terminal):

  * Makefile
  * Hello.py
  * Test_hello.py
  * Requirements.txt

### 3. Virtual enviroment:

  * `python3 -m venv ~/.scaffold` - Create a virtual enviroment "scaffold"
  * `source ~/.scaffold/bin/activate` - Activate the virtual enviroment
  * `which python` - Ask for the python version in the venv
  * `which pip` - In a virtual env, there is always the latest version of pip based on your python version

### 4. Setting up the project files:

  **1. Makefile:** Setting up the structure of the project.
  
    install:
       pip install --upgrade pip &&\
        pip install -r requirements.txt

     format:
       black *.py

     lint:
       pylint --disable=R,C hello.py

     test:

       python -m pytest -vv --cov=hello test_hello.py
   
   **2. Requirements.txt:** packages to install.
   
     pylint
     pytest
     click
     black
     pytest-cov
     
   Then, in the terminal install the requirements with `make install`
   
   **3. Hello.py:** The glorious solution.
   
    def add(x, y):
     return x + y
     
    result = add(1, 2)
    print(f"This is the sum of 1 and 2: {result}")
    
   **Optional:** Run `make format` and `make lint` to apply format to the code.
   
   **4. test_hello.py:** Testing file of the solution.
   
    from hello import add

    def test_add():
        assert add(1,2) == 3
     
   **Optional:** To execute all the Makefile, add the lint and test: `all: install lint test` and then `make all` in the Terminal.

### 5. Push the development to GitHub:

     git status
     git add *
     git commit -m "add structure"
     git config --global user.name "Username"
     git config --global user.email emailname@domain.com
     git commit --amend --reset-author
     git push

