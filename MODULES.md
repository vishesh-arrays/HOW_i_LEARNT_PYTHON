# What is a Module

A module is a file containing a set of codes or a set of functions which can be included to an application. A module could be a file containing a single variable, a function or a big code base.
### Creating a Module

To create a module we write our codes in a python script and we save it as a .py file. Create a file named mymodule.py inside your project folder. Let us write some code in this file.

(hash)mymodule.py file
def generate_full_name(firstname, lastname):
    return firstname + ' ' + lastname

Create main.py file in your project directory and import the mymodule.py file

# Importing a Module
To import the file we use the _import_ keyword and the name of the file only.

```python
# main.py file
import mymodule
print(mymodule.generate_full_name('Asabeneh', 'Yetayeh'))
```
### Import Functions from a Module
We can have many functions in a file and we can import all the functions differently.
```python
# main.py file
from mymodule import generate_full_name, sum_two_nums, person, gravity
print(generate_full_name('Asabneh','Yetayeh'))
print(sum_two_nums(1,9))
mass = 100
weight = mass * gravity
print(weight)
print(person['firstname'])

 #Import Functions from a Module and Renaming

During importing we can rename the name of the module.
```python
# main.py file
from mymodule import generate_full_name as fullname, sum_two_nums as total, person as p, gravity as g
print(fullname('Asabneh','Yetayeh'))
print(total(1, 9))
mass = 100 
weight = mass * g
print(weight)
print(p)
print(p['firstname'])
```
```
## Import Built-in Modules
Like other programming languages we can also import modules by importing the file/function using the key word _import_. Let's import the common module we will use most of the time. Some of the common built-in modules: _math_, _datetime_, _os_,_sys_, _random_, _statistics_, _collections_, _json_,_re_



### OS Module
Using python _os_ module it is possible to automatically perform many operating system tasks. The OS module in Python provides functions for creating, changing current working directory, and removing a directory (folder), fetching its contents, changing and identifying the current directory.
# import the module
import os
# Creating a directory
os.mkdir('directory_name')
# Changing the current directory
os.chdir('path')
# Getting current working directory
os.getcwd()
# Removing directory
os.rmdir()


### Sys Module
The sys module provides functions and variables used to manipulate different parts of the Python runtime environment. Function sys.argv returns a list of command line arguments passed to a Python script. The item at index 0 in this list is always the name of the script, at index 1 is the argument passed from the command line.
