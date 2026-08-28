1. A function is a sequence of code that has a name. The purpose of a function is to reuse a piece of code multiple times.
2. to declare a fxn we use syntax
 def function_name():
        code....

3. when we make a fxn we call it declaring fxn, or evoking fxn. it can be used with or without parameters., we can call a fxn by calling its name the end.
4. when we use fxn without parameters,there is nothing in paranthesis., and vice versa.
5. FXN return a value by using return statement
6. We can use multiple parameters in brackets with commas to seperate
7. =========
8. MAKING FIZZBUZZ
9. def fizzbuzz(integer):

    if integer%21 == 0:

        return "FizzBuzz"

    elif integer%7 == 0:

        return "Buzz"

    elif integer%3 == 0:

        return "Fizz"

    elif "3" in str(integer):

        return "Almost Fizz"    

    else:

        return integer

print("Welcome to FizzBuzz!")

integer = int(input())

  

for i in range(1, integer+1):

    print(fizzbuzz(i))
   ### Passing Arguments with Key and Value

[](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md#passing-arguments-with-key-and-value)

If we pass the arguments with key and value, the order of the arguments does not matter.

```python
# syntax
# Declaring a function
def function_name(para1, para2):
    codes
    codes
# Calling function
print(function_name(para1 = 'John', para2 = 'Doe')) # the order of arguments does not matter here
```


### Function with Default Parameters

[](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md#function-with-default-parameters)

Sometimes we pass default values to parameters, when we invoke the function. If we do not pass arguments when calling the function, their default values will be used.

```python
# syntax
# Declaring a function
def function_name(param = value):
    codes
    codes
# Calling function
function_name()
function_name(arg)
```
### Arbitrary Number of Arguments

[](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md#arbitrary-number-of-arguments)

If we do not know the number of arguments we pass to our function, we can create a function which can take arbitrary number of arguments by adding * before the parameter name.

```python
# syntax
# Declaring a function
def function_name(*args):
    codes
    codes
# Calling function
function_name(param1, param2, param3,..)
```

### Default and Arbitrary Number of Parameters in Functions

[](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md#default-and-arbitrary-number-of-parameters-in-functions)

```python
def generate_groups (team,*args):
    print(team)
    for i in args:
        print(i) 
generate_groups('Team-1','Asabeneh','Brook','David','Eyob')
```
### Dictionary unpacking

[](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md#dictionary-unpacking)

You can call a function which has named arguments using a dictionary with matching key names. You do so using `**`.

```python
# Define a function that takes two arguments: 'name' and 'location'
def greet(name, location):
    # Print a greeting message using the provided arguments
    print("Hi there", name, "how is the weather in", location)

# Call the function using keyword arguments
greet(name="Alice", location="New York")  
# Output: Hi there Alice how is the weather in New York

# Create a dictionary with keys matching the function's parameter names
my_dict = {"name": "Alice", "location": "New York"}

# Call the function using dictionary unpacking
greet(**my_dict)  
# The ** operator unpacks the dictionary, passing its key-value pairs 
# as keyword arguments to the function.
# Output: Hi there Alice how is the weather in New York
```
The main point of unpacking a dictionary in Python is ==to **write cleaner, more concise, and highly readable code** by avoiding manual extraction of key-value pairs==.

