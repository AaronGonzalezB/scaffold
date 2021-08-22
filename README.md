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

  **1. Makefile:**
  
    install:
       pip install --upgrade pip &&\
        pip install -r requirements.txt

     format:
       black *.py

     lint:
       pylint --disable=R,C hello.py

     test:

       python -m pytest -vv --cov=hello test_hello.py
   
   **2. Requirements.txt:**
   
     pylint
     pytest
     click
     black
     pytest-cov
     
   Then, in the terminal install the requirements with `make install`

