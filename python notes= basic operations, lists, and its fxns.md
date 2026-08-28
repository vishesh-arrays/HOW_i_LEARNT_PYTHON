 Casting: Converting one data type to another data type. We use _int()_, _float()_, _str()_, _list_, _set_ When we do arithmetic operations string numbers should be first converted to int or float otherwise it will return an error. If we concatenate a number with a string, the number should be first converted to a string. We will talk about concatenation in String section.
# int to float
num_int = 10 
print('num_int',num_int)         # 10
num_float = float(num_int)
print('num_float:', num_float)   # 10.0

# float to int
gravity = 9.81
print(int(gravity))             # 9

# int to str
num_int = 10
print(num_int)                  # 10
num_str = str(num_int)
print(num_str)                  # '10'

# str to int or float
num_str = '10.6'
num_float = float(num_str)  # Convert the string to a float first
num_int = int(num_float)    # Then convert the float to an integer
print('num_int', int(num_str))      # 10
print('num_float', float(num_str))  # 10.6
num_int = int(num_float)
print('num_int', int(num_int))      # 10

# str to list
first_name = 'ok'
print(first_name)              
first_name_to_list = list(first_name)
print(first_name_to_list)            # ['o','k']
#%% can be used to make cell in code.
all numbering starts from 0 not from 1
create a strn value by s:
basic operations and function of py
string is denoted with " or ' enclosed
like... \n is used to add line before and after the strings 
 like...+ to add other strings together = also called as concatenation
FUNCTIONS:
1. .lower() = to make all letters of strings to lower case letter
2. .upper() = to make all letters of strings to upper case letters
3. .isupper or .islower = to check if string has upper or lower case letters : if yes = True, if no = False
4. len()= position of letter         eg= ram = len(a) =  2
5. opposite of point "4" =using [] (only sq brackets, input number in it and it will give you the letter in that position)
6.  same as "5" u can use index() to find letter in it
7. use replace() to replace a string= eg print(replace("giraffe", "elephant") = it will replace giraffe with elephant.
8.  use abs() to see absolute value of number= like -5 = after using abs = 5
9. use pow()  means power like= eg. print(pow(3,2)) = which means 3 power 2=9
9.A  = find minimum value by typing  min before bracket and after abs and same for max
9.B = find round off value by round like above for min and max eg=3.2 after rounds fxn = 3
10. to access a bunch of math functions use = from math import *
11. floor fxn is used to get max round off value like = 3.7=4
11.A ciel is used opposite of 11.
12. sqrt is used for sq root
13. use remove prefix() to remove prefix of any word or number by typing in the bracket
14. use lstrip() to strip of any letter from word.
===============
LISTS:
15. use sq brackets to make a list with commas to sepreate things.
16. you can use numbers or index of element to show as output
1st element's index will be 0 in sq brackets
17. we can also access value of elements from back also by using -ve numbers
18. if you don't want 1st element  use 1: .
19. we can end selection in above point but 1:3 or 1:2 etc. it takes elements after 1 and 3, 1 and 2 respectively
or you can change the elements by something else by assigning index number to other element.
==========
LIST FUNCTIONS :
20. extend() function = this can extend list further in it
just put all elemets you need in bracket above 
or you can make another list and  put it in bracket or u can use .append () fxn for same
21. append()`, `extend()`, and `insert()` are Python list methods to add elements, differing by location and how they handle multiple items. `append()` adds a single item at the end, `extend()` unpacks an iterable to add multiple items at the end, and `insert()` adds a single item at a specific index.
22. use remove() to remove a item , or clear() to clean whole list
 you can also use pop() to remove last item frmo list (by default its target index is -1)
23. use index("item") to check whether it's in list or not, if yes itwill show its index otherwise no
24. use count() to see how many times that element is coming
sin list. (put item in brackets.
25. We can use Sort() To sort the list in Ascending order
 26. Make a new copy() To copy the list






