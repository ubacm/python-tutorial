# Functions and Files 
>A function is a block of organized, reusable code that is used to perform a single, related action. Functions provide 
>better modularity for your application and a high degree of code reusing.
>
>As you already know, Python gives you many built-in functions like print(), etc. but you can also create your own 
>functions. These functions are called user-defined functions.
>- TutorialsPoint

In Math, a function is a pre-defined equation where you pass an input - usually **X** - and get *returned* an output. 
In programming, a function works the same way, but instead of an equation, the function is a code block.

Examples of functions you have already seen are `print()`, `input()`, and `random.choice()`. Like the quote above, you 
can also define your own functions like these, and they can save a lot of rewriting code! :D


## User Defined Functions

You will learn most of Python's built in functions, but to define your own function, follow the code structure below.

```
def functionname( parameters ):
   "function_docstring"
   code_block
   return [expression]
```

You can define functions to provide the required functionality. Here are simple rules to define a function in Python.

  * Function blocks begin with the keyword `def` followed by the function name and parentheses - ( ).
  * Any input parameters or arguments should be placed within these parentheses. You can also define parameters inside 
  these parentheses. Parameters are the inputs that you will pass to the function. You can pass anything you want, but 
  make sure you check it in the function for the correct type/usability.
  * The code block within every function starts with a colon (:) and is indented.
  * The first statement of a function can be an optional statement - the documentation string of the function or 
  docstring. This lets other programmers know what the function does.
  * The statement `return [expression]` exits a function, optionally passing back an expression to the caller. A return 
  statement with no arguments is the same as return None.

An example of a function would be:
```python
def print_oddly(my_string):
    """
    The function prints each letter of a string on a new line.
    myString: String variable of any size
    """
    for letter in myString:
        print(letter)

print("I am outside the function!")

my_name = "Dan Starner"

print_oddly(my_name)
```

* We define the function on the first line with the `def` keyword, followed by the name we want to give it - in this case `print_oddly`.
* In the parenthesis, we list what variables we want to be passed when the function is called. Here it is `my_string`.
* We then declare the function docstring within the `"""`s. The docstring tells other programmers and readers what the function does.
* Inside the function and indented 4 spaces, we place the codeblock that we want to run. In this case it is the `for` loop, that prints out each letter of `my_string` on a separate line. Note how everything is indented 4 spaces PLUS what it normally would be.
* The `print()` statement at the bottom is NOT a part of the function. When the indenting stops, the function stops kind of like a conditional does.
* Below the first `print()` statement, we define a variable `my_name` and set it to a string.
* On the last line of the code, we call the function with its name, parentheseses, and any arguments we have to pass it. When it hits this line, it will call the code within `print_oddly` with `my_string` being set to the value of `my_name`.

Functions are **VERY** cool, because it should stop you from having to write the same line of code more than once. Let's 
say you have to write out tons of words with the letters on different lines - why you would have to do this I have no idea - 
you can just keep calling `print_oddly()` instead of writing out that `for loop` over and over, and over again...
 
## Files
If you want to read/write from a file, it is very easy. Before you can read or write a file, you have to open it using 
Python's built-in open() function. This function creates a file object, which would be utilized to call other support 
methods associated with it. The best way to open a file is shown below.

```python
# Open the file and save it to 'my_file'
with open("myfile.txt", "r+") as my_file:
    # Print out the first line of the file
    print(my_file.readline())
    
    some_code_block_affecting_file()

# The file is closed outside of the 'with' loop to prevent any issues.

some_other_code()
```

You'll notice that in the `open()` function has two parameters inside of it, the **location/filename** and the **mode**. 
The location and filename should be pretty self descriptive, but the **mode** may not be. The **mode** tells Python how 
to open the file; Should it just be able to read the file? Should it append to the file, or just overwrite what's in it?
The most common modes are listed below for future reference.

| Mode        | Description          |
| ----------- |:-------------:       |
| r  | Opens a file for reading only. The file pointer is placed at the beginning of the file. This is the default mode. |
| r+ | Opens a file for both reading and writing. The file pointer placed at the beginning of the file. |
| w+ | Opens a file for both writing and reading. Overwrites the existing file if the file exists. If the file does not exist, creates a new file for reading and writing. |
| a+ | Opens a file for both appending and reading. The file pointer is at the end of the file if the file exists. The file opens in the append mode. If the file does not exist, it creates a new file for reading and writing. |

Some of the most common function calls on your file object are listed below:

| Function Name/Call          | Description    |
| --------------------------- |:---------:       |
| `.write("str")`     | This will write the string passed to it wherever the pointer is. You can pass special characters like newlines '\n' if you would like |
| `.readline()`               | This will read the next line of the file and return it as a string. |
| `.readlines()`              | This will read all of the lines of the file and put them into an array. Useful in loops. |

In the directory that this README is located, run `python file_example.py` to try reading and writing out of a file.

