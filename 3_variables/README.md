# Variables in Python

In this section, we will introduce variables and strings, going indepth into both. If files are included with a 
section, it will be mentioned.


## Variables

A variable is something that holds a value that may change. Think of it like a box that you can put stuff in, look at, 
and swap out whenever you want. Look at the example below.
```python
# File
some_number = 7
print(some_number)
# Endfile, output below
7
```

The code creates a variable called `someNumber` and assigns it the integer value 7. When we try to print `someNumber`, 
Python finds where we declared it and prints out the value we assigned to it. Declaring/Instantiating a variable in 
Python follows this construct:
```
my_variable_name = integer/long | string | boolean/expression | float | Object | list | dictionary  # Don't worry about dictionaries yet.
```

As you can see, a variable can be set to many different things. The name of the variable - on the left side - can be 
anything as long as it starts with a letter A-Z and/or a '_'. Try to be as specific as possible when naming variables, 
because it makes the code easier to read. If a variable holds the number of students in a class, then call it 
`num_of_students`. If you need more than one word in a variable name, split the words with an underscore and do not 
capitalize.

The right side of the declaration can be any of any type. Each of the types are explained below.


#### Integers

Integers are positive or negative whole numbers with no decimal point. 
- Examples: `5, 4, 7, 10, -15, 0, 100, -145`
- Creation: Either you can just put the number like `5` or if you have a string that can be turned into a number,
  wrap it in `int(<string>)` like `int("5")` will equal `5`.
    
    
#### String

A string is a collection of characters with a length equal to the number of characters in it. A character is any alpha-
numeric symbol - A-Z, 0-9, !@#$% - such as `"Hello World", "c", "!dfdfwer", "I am a string!"`. A string can also have 
length zero and be equivalent to `""`. Strings can be single or double quoted. 

* If you want the same quote type inside of the string, then you have to 'escape' it by putting a `\` in front of it -
example: `"He said to me, \"Woah\""`. If you don't want to escape it, then you can put `r` infront of it like so

```python
print('C:\\nowhere')  # Will be escaped to print 'C:\nowhere'
print(r'C:\\nowhere') # Will print as is. 'C:\\nowhere'
```

Strings can be added together like so:

```python
greeting = "Hello, " + "Dan, " + " you look good today!"
print(greeting)
# End of file, output below
Hello, Dan, you look good today!
```

To turn a current variable into its string representation, wrap the variable in `str(value)`. If you gave it something 
like `str(5)` it will return `"5"`. If you want to print a string and number together, you must wrap the number in the 
`str()` function.

Go into `greeting.py` and follow the directions about assigning variables and printing them out.


#### Boolean Expressions and Logic Operators
A Boolean value is either True or False. It is named after the British mathematician, George Boole, who first 
formulated Boolean algebra — some rules for reasoning about and combining these values. This is the basis of all modern 
computer logic. In Python, boolean values can be either `True` or `False`. 

```python
# Two different Booleans
am_i_cool = True

can_operate = False
```

An expression is a line of code that be evaluated to a Boolean. There are six boolean expression operators you should know:

```python
x == y               # Produce True if ... x is equal to y
x != y               #                 ... x is not equal to y
x > y                #                 ... x is greater than y
x < y                #                 ... x is less than y
x >= y               #                 ... x is greater than or equal to y
x <= y               #                 ... x is less than or equal to y

# Some examples of boolean expressions
age = 18  # Int variable
old_enough_to_get_driving_license = age >= 16  # True
print(old_enough_to_get_driving_license)

# Another example
number = 7
equal_to = (6 == number)  # False
```

*Boolean expressions get evaluated from most inward parenthesis to outward.*

* Go into the `3_variables` directory in this repository and run the command below to test your boolean expression 
knowledge!
```bash
cd 3_variables/
# Once inside of the directory
python expressions.py
```

##### Logic Operators
Coupled with Boolean expressions, Logic operators are very important to Computer Science. The three Logic Operators are 
`and`, `or`, and `not`. They are used to group multiple boolean expressions to form one boolean evaluation. They are 
good with telling if a number is in a range or not amongst other things. Another useful operator is using `is` to denote 
equality.

```python
old_enough_to_drive = True
clean_record = False

# If they are old enough and have a clean record
low_insurance = old_enough_to_drive and clean_record

# If a drive is not old enough or has a bad record
bad_driver = not old_enough_to_drive or not clean_record

# Junior driver if their age is 16 or 17.
age = 16
junior_driver = age >=16 and age < 18
```


#### Floats
Floats represent real numbers and are written with a decimal point dividing the integer and fractional parts. 
Floats usually represent decimal numbers, but they can also represent numbers in scientific notation. 

**WATCH OUT: Occasionally floating point errors occur with arithmetic.**

```python
# Float examples
example1 = 6/8
example2 = 7/3
example3 = 2.323
example4 = example1 / example3
example5 = float(7)
example6 = float("5")
example7 = float("3.14")
```


#### Objects
These will be covered at a later time.


#### Lists
The most basic data structure in Python is the **list**. Each element of a sequence is assigned a number - its position 
or index. The first index is zero, the second index is one, and so forth. The list is a most versatile datatype 
available in Python which can be written as a list of comma-separated values (items) between square brackets. Important 
thing about a list is that items in a list need not be of the same type. To create a list, follow the syntax below.
To access values in lists, use the square brackets for slicing along with the index or indices to obtain value 
available at that index.

```python
         # Index: 0  1  2  3  4
my_number_list = [1, 4, 6, 8, 10]
my_number = my_number_list[0]  # Get the first number; will be 1.

my_string_list = ["Hello", "World"]
my_string = my_string_list[1]  # Equates to "World"

my_mixed_list = [1, "Hi", 15, True]
my_mixed = my_mixed_list[3]  # Equates to True
```

To update the value at an index, you can access the value with the square brackets, and then just put that on the left 
side of a declaration statement.

```python
my_list = ['physics', 'chemistry', 1997, 2000]

print("Value available at index 2 : ")
print(my_list[2])
my_list[2] = 2001
print("New value available at index 2 : ")
print(my_list[2])
```

To add to an existing list, use `list.append(some_value)`

```
my_list = [1, 10, 15]
my_list.append(5)
print(my_list)  # Will print "[1, 10, 15, 5]"
```

To remove from an existing list, use `list.remove(some_value)`

```
my_list = [1, 10, 15]
my_list.remove(10)
print(my_list)  # Will print "[1, 15]"
```

If you want the value returned back, use `list.pop(index)`
```
my_list = [1, 10, 15]
my_num = my_list.pop(0)
print(my_num)  # Will print "1"
```

* You can mess around and assign different variables in `variables.py` and see how they change!

#### Dictionary
Dictionaries are like arrays, but allow you to map a key to a value. With lists, you use integers are indices, with maps, you can use (just about) anything.

```python
my_dictionary = {"Dan": 19, None: "Nothing", 5: "My age.", "coolness": False}

print(my_dictionary["Dan"])  # Prints 19

my_dictionary["new_key"] = "My New Value"

print(my_dictionary)  # Prints '{"Dan": 19, None: "Nothing", 5: "My age.", "coolness": False, "new_key": "My New Value"}'
```
