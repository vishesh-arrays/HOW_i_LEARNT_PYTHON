What is Error Handling?

**Error handling** is a crucial aspect of programming that involves responding to and recovering from error conditions in your code. In Python, errors are managed using a system of **exceptions**. An exception is an event that occurs during the execution of a program, disrupting the normal flow of the program's instructions.

When an error occurs, Python creates an exception object. If the exception is not handled, the program will terminate and display an error message. Proper error handling allows your program to detect errors, handle them gracefully, and continue running.

Common types of exceptions include `TypeError`, `ValueError`, `IOError`, and `ZeroDivisionError`. For example, a `TypeError` occurs when an operation is performed on a value of an inappropriate type, and a `ZeroDivisionError` occurs when a number is divided by zero.

Here's a simple example of an error that occurs when trying to convert a string that does not represent a number into an integer:

```python
s = "abc"
n = int(s)  # This will raise a ValueErrorprint(n)
```

In this example, the `int()` function cannot convert the string `"abc"` into an integer, so it raises a `ValueError`. Without error handling, this exception would cause the program to crash.

# Try and Except Block

The `try-except` block in Python allows you to handle exceptions and prevent your program from crashing. Code that might raise an exception is placed inside the `try` block, and the `except` block handles the error if it occurs.

Here’s the basic structure:

```python
try:    # Code that might cause an exception    risky_code()except ExceptionType:    # Code to handle the exception    handle_error()
```

Example:

```python
try:    num = int("abc")  
# This raises a ValueErrorexcept ValueError:    
print("Invalid input! Please enter a number.")
```

Output:

```python
Invalid input! Please enter a number.
```

In this example, instead of crashing, the program catches the `ValueError` and prints a friendly message. Use `try-except` to handle specific exceptions and keep your program running smoothly.
# Handling Multiple Exceptions

In Python, we can handle different types of exceptions in separate `except` blocks. This allows us to respond differently based on the specific error that occurs.

Start with a basic try-except structure:

```python
try:    # Code that might raise exceptions    passexcept Exception as e:    # Handle any exception    pass
```

To handle multiple exceptions, add specific except blocks:

```python
try:    number = int(input("Enter a number: "))    
result = 10 / number    
print(result)
except ValueError:    
print("That's not a valid number!")
2  except ZeroDivisionError:    
print("Cannot divide by zero!")
```

You can also catch multiple exception types in a single except block:

```python
try:    # Some code    passexcept (ValueError, TypeError):    print("Invalid input type!")
```

The order of except blocks matters - always place more specific exceptions before more general ones.


