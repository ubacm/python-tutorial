## Hello Python!

We are going to put our pancakes on the backburner for a bit now - haha solid pun - and we are going to introduce 
the Python programming language. I have always felt that it is the easiest language to pick up for first timers, 
its very easy to use, but at the same time its very powerful. 

Python is an interpreted, object-oriented, high level programming language with dynamic typing and simple syntax. Now 
that sentence probably contains a lot of unknown words/phrases to you right now, so lets go through each description.


#### Interpreted vs Compiled
* Python is an interpreted language, meaning that you can just write the code and test it without having to do any other 
steps. A program in the middle, known as **the interpreter** has the job to turn your code in something the computer 
its running on can recognize and perform. While all of the run scripts won't change based on the machine, the 
interpreter has to be designed for that Operating System / Hardware.

* A compiled language - like Golang, C, C++... - has an extra step in the process. After you write the code, the 
developer has to **build** it using a compiler. This does not run the code, but it builds the code into machine-readable
 bits so that the script can be directly run without the need of an interpreter.
 
In most cases, compiled languages have a slight edge on runtime speed, but interpreted languages can have better 
development speed.


#### Object Oriented
These days, most projects you will write here on out will be using Objected Oriented (OO) programming languages, 
compared to its predecessor Functional programming languages. Object Oriented programming lets you write **classes** 
for different Objects to easily represent them. A class is an abstract definition of the object, and it can have as 
many attributes as needed to describe it which can later be used/set for computation. An Object is a block of memory 
that represents an actual instance of the class. Let's say I have the class Car, it would be something like

```python
class Car:
    make       # Chevy, Ford, Mercedes....
    model      # Cobalt, Silverado, Cruze...
    owner_name # Dan, Joe, Mike
    year       # 2006, 2007
```

The attributes a class can have can be numbers, words, letters, True/False, or other objects just to name a few types. 
The class above has 4 attributes, `make`, `model`, `owner_name`, and `year`. Right now, this is just a definition, but 
somewhere in the code it takes meaning if the programmer says `I want a Car that has a Chevy make, Cobalt model, an 
owner Dan, and 2006 year`. After turning that sentence into code, you could then easily remember and access your 2006 
Chevy Cobalt wherever you want in your code. Objects make programming a lot easier, so don't get to worked up over them. 
If they are confusing to you, wait until actual concrete coding examples and it will make more sense :D


#### High Level
Python is a high level programming language, and that is why its so good to use as an introduction course, and for 
professional projects. 

* A high level programming language means that the code is simpler to read/develop, but the interpreter/compiler is 
much more complicated. This is good, because the code will be easier to read/write for new coders. Take the example
```python
print("Hello World")
```
Its not too difficult to infere that this will print out `Hello World`. That is the beauty of high level programming 
languages.
* A low level programming language involves less English words and more symbols/abbreviations, using needing more 
syntax. These languages usually require more responsibility on the programmer to watch memory allocation, bit shifting, 
and other low-level procedures that Python handles for you. Take this Assembly program that also only prints out `Hello 
World` and see how much more complicated it is.

```assembly
section     .text
global      _start                              ;must be declared for linker (ld)

_start:                                         ;tell linker entry point

    mov     edx,len                             ;message length
    mov     ecx,msg                             ;message to write
    mov     ebx,1                               ;file descriptor (stdout)
    mov     eax,4                               ;system call number (sys_write)
    int     0x80                                ;call kernel

    mov     eax,1                               ;system call number (sys_exit)
    int     0x80                                ;call kernel

section     .data

msg     db  'Hello, world!',0xa                 ;our dear string
len     equ $ - msg                             ;length of our dear string
```


#### Dynamic Typing
All programming languages let you allocate memory and save its value to something known as a **variable**. It works the 
same way as in math class; the variable can be anything it just must be defined first before its used.

Some languages are *statically typed*, meaning that once you say define a variable as having a particular type 
(e.g. integer or string), whether explicitly or implicitly, they cannot have their types changed. This will usually be 
enforced with type checks performed by the compiler.

Python is *dynamically typed*, so you can change the variable type by simply assigning the desired value. You don't need 
to explicitly say what type a variable is in Python, though we'll revisit this idea in the next section.


## Try it Yourself
*Note: Before we go much farther, if I show a code block and you see "# Some text here" then that is a comment and 
does nothing to the program other than give more information to the reader.*

In this directory, run `python hello_world.py` and see what happens. It should print out "Hello World" to wherever 
you ran that command. This is the most basic program we can write; it takes a **String** - any group of letters within 
quotation marks - and `prints` it out. Either modify that or add a new line the file trying to print out a 
greeting with your name! Mine would be...

```python
print("Hello World")
# My new line below
print("Hello, Dan!")
```
