# LIST COMPREHENSIONS/DATA AGGREGATION:
List comprehensions provide a concise way to create new lists based on existing iterables. You can integrate data aggregation functions like `sum()`, `min()`, and `max()` directly within list comprehensions to perform calculations on the elements of the new list as it's being created.

Calculating the Sum of Squares:

```python
numbers = [1, 2, 3, 4, 5]
sum_of_squares = sum([n * n for n in numbers])
print(sum_of_squares)# Output: 55
```

In this example, the list comprehension `[n * n for n in numbers]` creates a list of squares, and the `sum()` function calculates the sum of these squares.

Finding the Minimum of Transformed Values:

```python
numbers = [-3, -1, 0, 1, 3]
min_absolute = min([abs(n) for n in numbers])
print(min_absolute)# Output: 0
```

Here, the list comprehension `[abs(n) for n in numbers]` creates a list of absolute values, and the `min()` function finds the minimum value in this list.

Finding the Maximum of Filtered Values:

```python
numbers = [1, 2, 3, 4, 5, 6]max_even = max([n for n in numbers if n % 2 == 0])print(max_even)# Output: 6
```

In this example, the list comprehension `[n for n in numbers if n % 2 == 0]` creates a list of even numbers, and the `max()` function finds the maximum value in this list.




# Sorting:
Sorting is a fundamental operation in computer science, and Python offers powerful built-in tools to sort data efficiently. The primary function for sorting is `sorted()`, which can be used to sort various types of data, including numbers, strings, and more complex objects.

Basic Sorting:

The `sorted()` function takes an iterable (e.g., a list, tuple, or set) as its argument and returns a new list containing the sorted elements. By default, it sorts in ascending order.

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]sorted_numbers = sorted(numbers)print(sorted_numbers)# Output: [1, 1, 2, 3, 4, 5, 6, 9]
```

In this example, `sorted()` sorts the `numbers` list in ascending order.

Reverse Sorting:

To sort in descending order, you can use the `reverse` parameter and set it to `True`.

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]sorted_numbers_desc = sorted(numbers, reverse=True)print(sorted_numbers_desc)# Output: [9, 6, 5, 4, 3, 2, 1, 1]
```

Here, `sorted()` sorts the `numbers` list in descending order.

Sorting Strings:

The `sorted()` function can also sort strings based on their lexicographical order (i.e., the order they would appear in a dictionary).

```python
words = ["apple", "banana", "cherry"]
sorted_words = sorted(words)
print(sorted_words)# Output: ['apple', 'banana', 'cherry']
```

In this example, `sorted()` sorts the `words` list in alphabetical order.

Custom Sorting with Key Function:

For more complex sorting needs, you can use the `key` parameter to specify a function that determines the sorting order. The `key` function is applied to each element before sorting, and the returned values are used for comparison.

```python
words = ["apple", "banana", "cherry"]
sorted_words_by_length = sorted(words, key=len)
print(sorted_words_by_length)# Output: ['apple', 'banana', 'cherry']
```

In this case, `sorted()` sorts the `words` list based on the length of each word, using the `len()` function as the `key`.

# Recursive FXN 1

Recursive Functions Part 1

A recursive function is a function that calls itself to solve smaller instances of a problem. Each recursive call must bring the function closer to a base case, which stops the recursion.

Example: Summing numbers from 1 to n:

```python
def sum_to_n(n):    
if n == 0:  # Base case        
return 0    
return n + sum_to_n(n - 1)  # Recursive stepprint(sum_to_n(5))  # Output: 15
```

# Recursive Functions Part 2

Recursive functions typically have two parts:

1. **Base Case**: Defines when the recursion should stop.
2. **Recursive Step**: Calls the function itself with smaller input.

Example: Calculating factorial using recursion:

```python
def factorial(n):    
if n == 1:  # Base case        
return 1    
return n * factorial(n - 1)  # Recursive callprint(factorial(5))  # Output: 120
```

Here, the function keeps calling itself with `n - 1` until it reaches `1`, where the recursion stops.

Example: Reversing a String:

```python
def recursive_reverse(s):    if len(s) <= 1:  # Base case: empty or single-character string        return s    else:        return recursive_reverse(s[1:]) + s[0]  # Recursive steptext = "hello"result = recursive_reverse(text)print(result)# Output: olleh
```

In this example, the `recursive_reverse` function calls itself with the rest of the string (`s[1:]`) until the string is empty or has only one character. Each call appends the first character to the result of the recursive call, effectively reversing the string.

