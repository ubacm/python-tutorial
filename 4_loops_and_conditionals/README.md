## Loops and Conditionals

Now I know that up to this point its been a lot of learning and not terribly a lot of doing, *BUT THAT ALL CHANGES NOW!*

Once we learn a few things in this section, you'll have most of the basics down to build some cool games and programs, 
and that is exactly what we are going to do! We are going to build a very basic version of *Hangman* to use what 
we already learned coupled with the new topic of Loops and Conditionals.

#### Don't Get HUNG up on the Details
(ah, I'm so funny!)

Before we begin programming, let's break down the game of Hangman in the same way we broke down making pancakes in the 
introduction. Instead of physical objects this time though, we need to think of how the game is played, and what is 
needed to play it. I have a small list below of what I could think of...

Things needed:

1. A random, unknown word
2. A number of wrong guesses before a loss

Gameplay Instructions:

1. Computer picks a random word.
2. The game begins a loop
    1. The user will pick a letter.
    2. If the letter was already said, restart loop.
    3. If the letter is in the word, add it.
    4. If the letter is not in the word, add 1 to bad guess count.
    5. If the word is finished, the player wins
    6. If the player used all the wrong guesses, then end the games.
    
    
#### Starting with the Variables
So before we can begin playing the game, we have to set up the all the variables using the types of variables from the 
previous lesson. Lets start with the unknown word. To pick from a word, we will need a **list** of words...Hm, see any 
words stick out in that last sentence that we should thing about?? OH YEA! A list of strings would be cool! Lets start 
there and move on... *Note that you can code this in `4_loops_and_conditionals/hangman.py`. To run a Python file, just
run `python <FILE LOCATION/NAME.py>` so this would be `python 4_loops_and_conditionals/hangman.py`.*

```python
# Create a list of strings for possible words to guess
# Your list can have any words you can think of
# To make life easier, set all the characters to uppercase or lowercase
word_list = ["pizza", "tomato", "pepper", "gingersnap", "oreos"]
```

Okay, so now we have a pretty decent sized list. We can worry about word choices after we get the rest running. Now to 
pick a random word, we are going to use a **function** that is already built into Python by default. We are going to 
introduce the **import** syntax, which lets you use code/functions for another python file, but we will go more indepth 
with it later. The Python `random` module - a module is a group of python code in a directory together - contains useful 
functions to come up with random values for most types such as booleans, numbers, and indexes of a list. We are going to 
take advantage of `random.choice( list )` which when input a list, will return a random value in the list. Let's use it 
to pick a random word from our list. *Note that `import` statements should always be at the top of a file before any 
executable code just for formality and clean code.*

```python
# New code
# Import the module named 'random' to have access to its functions
import random

# Create a list of strings for possible words to guess
# Your list can have any words you can think of
# To make life easier, set all the characters to uppercase or lowercase
word_list = ["pizza", "tomato", "pepper", "gingersnap", "oreos"]

# New code
# Pick a random word from the list
chosen_word = random.choice(word_list)
```

We now have a random word from our list!

In order to set the number of incorrect guesses and the total guesses before losing the game, we need two integer values.
We will compare the number of wrong guesses to the total guesses before losing to make sure the former is less. We also 
need a list of characters they have guessed that will start as an empty list.

```python
# ...Previous code from above...

incorrect_guesses = 0  # Start this at zero and +1 each wrong guess
total_incorrect_allowed = 6  # After 6 incorrect guesses, you lose

guessed_letters = []  # Will hold the previously guessed characters
```

Sweet, so now we have most of the stuff set up to play the game, but we aren't actually doing anything with this stuff! 
Time to take a short interlude and talk about **loops** and **conditionals**.

### Loops
>In general, statements are executed sequentially: The first statement in a function is executed first, followed by the 
>second, and so on. There may be a situation when you need to execute a block of code several number of times.
>Programming languages provide various control structures that allow for more complicated execution paths.
>A loop statement allows us to execute a statement or group of statements multiple times.
> - TutorialsPoint

The above summarizes loops. They let you perform the same block of code over and over again. The types of loops are 
below. Note that the block of code you want run should be indented with 4 spaces from the indentation of the loop 
statement.

#### While Loops
A `while` loop repeats a statement or group of statements while a given condition is TRUE. It tests the condition 
before executing the loop body. **BE CAREFUL OF INFINITE LOOPS THAT NEVER EXIT**, although sometimes they can be good.

```python
# Basic abstract usage
while BOOLEAN_EXPRESSION:
    code_block
    code_block
code_outside_of_loop

# This increments and prints out a counter
count = 0
while count <= 10:
    print(count)
    count += 1
# Will print 1 -> 10 on different lines


# This will print "Haha" forever
# Infinite loops are really only useful for game loops
while True:
    print("Haha")

```

#### For Loops
A `for` loop executes a sequence of statements multiple times and abbreviates the code that manages the loop variable. A 
for loop will take a list and go through each index in it, or it will go through each character in a string, or iterate 
through some sequence it is given.

```python

for VARIABLE in SEQUENCE | STRING | ITERATOR:
    code_block
    code_block
code_outside_of_loop

# Will run 3 times
# Will print:
# We're on time 0
# We're on time 1
# We're on time 2
for x in range(0, 3):
    print("We're on time %d" % x)
    
    
# Iterate through a list
names = ["Dan", "Joe", "Jared"]

for name in names:
    # Each index will be the 'name' variable for its runthrough of the codeblock
    # The '%s' will get replaced by the variable after the '%' outside of the string.
    print("Hello, %s" % name)
    
# The code above will print everyone's name on a separate line
```

## Conditionals
>A **conditional** is when a program has more than one choice of actions depending on a variable's value. Think of a traffic 
>light. When it is green, we continue our drive. When we see the light turn yellow, we reduce our speed, and when it is 
>red, we stop. These are logical decisions that depend on the value of the traffic light. Luckily, Python has **conditionals** 
>statement to help us when our application needs to make such decision for the user.
> - Wikibooks
Conditionals are used when the actions a program takes can vary based on the value of a variable.

### If/Else
Take the codeblock below, when a boolean expression is passed to the `if` statement:
```python
n = random.randInt(-10, 11)  # Pick a random number between -10 and 10.
if n < 0:
    print("The absolute value of",n,"is",-n)
else:
    print("The absolute value of",n,"is",n)
```
and that has the output of 
```
Integer? -8
The absolute value of -8 is 8

Integer? 1
The absolute value of 1 is 1
```
So what is going on? Python reads the line "if n < 0:". If n is less than zero Python runs the line 
`print("The absolute value of", n, "is", -n)`. Otherwise Python runs the line `print("The absolute value of", n, "is", n)`.

More formally, Python looks at whether the expression `n < 0` is **True** or **False**. An if statement is followed by 
an indented block of statements that are run when the expression is `True`. After the if statement is an optional 
**else** statement and another indented block of statements. This 2nd block of statements is run if the expression is 
`False`.

*Note that an `if` statement does not always need an `else` associated with it.*

### Elif
Another feature of the if command is the `elif` statement. It stands for "else if," which means that if the original if 
statement is false and the elif statement is true, execute the block of code following the `elif` statement. Here's an example:
```python
a = 0
while a < 10:
    a = a + 1
    if a > 5:
        print(a, ">", 5)
    elif a <= 7:
        print(a, "<=", 7)
    else:
        print("Neither test was true")
```
With the output - Notice how the elif a <= 7 is only tested when the if statement fails to be true. elif allows 
multiple tests to be done in a single if statement:
```
1 <= 7
2 <= 7
3 <= 7
4 <= 7
5 <= 7
6 > 5
7 > 5
8 > 5
9 > 5
10 > 5
```

## Back to the Game
So back to the game; now that we know loops, we can start a game loop, because the game of Hangman is turn-based. 
Because we aren't sure how many times we will have to loop, let's use a `while` loop. It should keep running until we've
 either won the game or used enough guesses. Our boolean expression to check for the loop will be if 
`incorrect_guesses < total_incorrect_allowed`. Adding this to our current code we get:

```python
import random

# Pick a random word from a list
word_list = ["pizza", "tomato", "pepper", "gingersnap", "oreos"]
chosen_word = random.choice(word_list)

# Keep track of guesses
incorrect_guesses = 0  # Start this at zero and +1 each wrong guess
total_incorrect_allowed = 6  # After 6 incorrect guesses, you lose
guessed_letters = []  # Will hold the previously guessed characters

while incorrect_guesses < total_incorrect_allowed:
   print()  # Give a blank line to separate the turns easily.
   # Running this will be an infinite loop and will never stop.
```

Now we will go about printing out the word and our info in a good way. We will iterate through each letter in the 
`chosen_word` and if it is in `guessed_letters` then we will print it out, and if its not in the list, then we will 
print out a `_`. We will introduce a new parameter - you'll learn about parameters in the next section - to the `print` 
statement.

```python

# Old code ....

while incorrect_guesses < total_incorrect_allowed:
   print()  # Give a blank line to separate the turns easily.
   
   # New code below
   for letter in chosen_word:
        if letter.upper() in guessed_letters:
            print(letter.upper(), end=" ")
        else:
            print("_ ", end=" ")
            
   print("\n\nYou have %s bad guesses left.\n" % (total_incorrect_allowed - incorrect_guesses))
   
```

So the **for loop** is going through each letter of the `chosen_word`, and then it checks if the letter is in `guessed_letters`. 
The syntax to check if an element is in a list is very simple - `ELEMENT in LIST`. We use the `.upper()` to make the letter 
uppercase because in programming, *l* does not equal *L*, so its good to stick to either all uppercase or all lowercase. 
If its in the list, then we print the letter, and the `end=" "` means to print a space after it, instead of moving to 
the next line. If the letter is not in `guessed_letters` then we do the same, but print out an underscore (_) instead. 
The print line below the for loop prints out the number of guesses you have left. The `\n\n` at the beginning indicates 
two **newline** characters, which together end the line below and print a blank line, giving the game some clean 
formatting to it.

While we are in this loop, lets figure out if we've won or not. Obviously if we have to print out an underscore, then we 
haven't won yet. Let's create a boolean `has_won` and set it to `True` at the start of every loop. If we have to do the 
`else` of the conditional, then we set it to `False`. Edit the loop to look like this:

```python
has_won = True
for letter in chosen_word:
        if letter.upper() in guessed_letters:
            print(letter.upper(), end=" ")
        else:
            has_won = False
            print("_ ", end="")
```

If you have won, then we should check the `has_won` variable, print something nice, and quit the game. Let's add that 
below our print statement that we had after the for loop. The whole program should look like this:

```python
import random

# Pick a random word from a list
word_list = ["pizza", "tomato", "pepper", "gingersnap", "oreos"]
chosen_word = random.choice(word_list)

# Keep track of guesses
incorrect_guesses = 0  # Start this at zero and +1 each wrong guess
total_incorrect_allowed = 6  # After 6 incorrect guesses, you lose
guessed_letters = []  # Will hold the previously guessed characters

while incorrect_guesses < total_incorrect_allowed:
   print()  # Give a blank line to separate the turns easily.
   has_won = True
   for letter in chosen_word:
       if letter.upper() in guessed_letters:
           print(letter.upper(), end=" ")
       else:
           has_won = False
           print("_ ", end=" ")
           
   print("\n\nYou have %s bad guesses left.\n" % (total_incorrect_allowed - incorrect_guesses))
   
   # new code
   # If they won, print something nice and exit out.
   if has_win:
        print("You have won!!")
        exit()
```

Now the player will win if they successfully guessed all the letters, or lose if they use all their incorrect attempts. 
When the player loses, the **while** loop will break, so we should print something at the very end telling them they 
lost.

```python
    if has_win:
        print("You have won!!")
        exit()
        
# New code -- Note that the line is NOT indented
print("You lost! Your man is dead! The word was %s." % chosen_word)
```

Now we give the user the correct word and tell them they lost if they use up all their guesses.

### User Input
So now that we have all of the computer's end finished, its time to break the infinite loop and have the user give 
some input to play the game. In python, to collect user input, use the function `input(str:prompt)`. You pass it the 
prompt that will be shown to the user, and you save the returned value to a variable. Under the `if has_win` conditional 
- but not inside of it - place this line; `.replace()` will replace any occurrences of the first string with the second, 
in this example we are removing spaces:

```python
    # ...Old code...
    if has_win:
        print("You have won!!")
        exit()
    
    # New line -- Collect user input 
    letter = input("Please enter a single letter: ").replace(" ", "")
        
        
print("You lost! Your man is dead! The word was %s." % chosen_word)
```

Now that we have a letter, we can do the appropriate thing with it. Whenever you get user input, ALWAYS TEST IT FOR 
BAD INPUT. **Lesson #1, Never trust the user!** Check to make sure that their input is correct. For this example, we 
will have to make sure that the length of the input is no longer than 1, and that the choice is not already in `guessed_letters`.
I am going to throw a lot of code out there, but try to understand it on your own first before looking below it for 
explanations.

```python
    
    letter = input("Please enter a single letter: ").replace(" ", "")
    
    # New code block
    if len(letter) > 1 or letter.upper() in guessed_letters:
        print("Bad input!")
    else:
        if letter.upper() in chosen_word.upper():
            print("%s is in the word!" % letter.upper())
        else:
            print("%s is not in the word!" % letter.upper())
            incorrect_guesses += 1
        guessed_letters.append(letter.upper())
        
    # ...Old Code...
```

In the first conditional, we are making sure that the letter variable is no longer than 1 with python's `len(variable)` 
function. `len()` can take any object or sequence, so its always a useful function to double check sizes. If the input 
fails - that means passes the first condition with `True` - then we print out *Bad Input*. If its a good input and goes 
to the `else` block, then it faces another conditional to see if the letter is in the word. If it is, then we tell the 
user that it is in the word, and if it isn't, then we increment to the incorrect_guesses by 1. Note that `incorrect_guesses += 1` 
is the same as `incorrect_guesses = incorrect_guesses + 1` but its an easier way to do it - same works for `*=`, `-=`, 
and `/=`. Either way, if its in the word or not, we add the letter to `guessed_letters` at the end. Note that we are 
always checking with Upper case letters to stay consistent.


## You Have Hangman!
Congrats, you just programmed your first game!! Pretty sweet right? You can play that, or play with `hangman_solution.py` which
has close to 11,000 possible word choices! The final code is below:

```python
import random

# Pick a random word from a list
word_list = ["pizza", "tomato", "pepper", "gingersnap", "oreos"]
chosen_word = random.choice(word_list)

# Keep track of guesses
incorrect_guesses = 0  # Start this at zero and +1 each wrong guess
total_incorrect_allowed = 6  # After 6 incorrect guesses, you lose
guessed_letters = []  # Will hold the previously guessed characters

while incorrect_guesses < total_incorrect_allowed:
   print()  # Give a blank line to separate the turns easily.
   
   has_won = True
   for letter in chosen_word:
       if letter.upper() in guessed_letters:
           print(letter.upper(), end=" ")
       else:
           has_won = False
           print("_ ", end=" ")
           
   print("\n\nYou have %s bad guesses left.\n" % (total_incorrect_allowed - incorrect_guesses))
   
   # If they won, print something nice and exit out.
   if has_win:
        print("You have won!!")
        exit()
        
   letter = input("Please enter a single letter: ").replace(" ", "")
    
    if len(letter) > 1 or letter.upper() in guessed_letters:
        print("Bad input!")
    else:
        if letter.upper() in chosen_word.upper():
            print("%s is in the word!" % letter.upper())
        else:
            print("%s is not in the word!" % letter.upper())
            incorrect_guesses += 1
        guessed_letters.append(letter.upper())

print("You lost! Your man is dead! The word was %s." % chosen_word)
```

In the next lesson we will learn about functions to shorten and clean up code blocks!
    

