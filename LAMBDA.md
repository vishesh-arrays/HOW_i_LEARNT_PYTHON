# LAMBDA
1.
A **lambda function** is a small, anonymous function defined using the `lambda` keyword. Lambda functions can take any number of arguments but can only have one expression. They are useful for creating simple, one-line functions without the need for a full function definition using the `def` keyword.

The syntax of a lambda function is:

```python
lambda arguments: expression
```

Here's a breakdown of the syntax:

- `lambda`: The keyword that indicates the start of a lambda function definition.
- `arguments`: A comma-separated list of arguments, similar to the parameters in a regular function definition.

- `expression`: A single expression that is evaluated and returned as the result of the lambda function.

Here's an example of a lambda function that adds two numbers:

```python
add = lambda x, y: x + y
result = add(5, 3)
print(result)# Output: 8
```

In this example, the lambda function takes two arguments, `x` and `y`, and returns their sum. The lambda function is assigned to the variable `add`, which can then be called like a regular function.

2.

Lambda functions can also include conditional logic using the `if-else` expression syntax.

Create a basic lambda function with an if-else condition:

```python
# Format: lambda parameters: 
value_if_true if condition ------------------------
else value_if_falseis_adult = lambda age: "Adult" if age >= 18 else "Minor"
```

Test the lambda function with different values:

```python
print(is_adult(20))  # Output: "Adult"print(is_adult(15))  # Output: "Minor"
```

You can use more complex conditions as well:

```python
grade_status = lambda score: "Amazing!" if score == 100 else "Pass" if score >= 60 else "Fail"print(grade_status(75))  # Output: "Pass"

