# Classes

> Object-oriented programming (OOP) is a programming language model organized around 
> objects rather than "actions" and data rather than logic. Historically, a program 
> has been viewed as a logical procedure that takes input data, processes it, and 
> produces output data.
> - http://searchsoa.techtarget.com/definition/object-oriented-programming

## Object Oriented Programming
Object Oriented programming (OOP) is a higher level programming term/philosophy that is in great use 
over the older Functional Programming. In OOP, there are your primitive variables that you have 
already seen - integers, booleans, strings... - but there are also variables that can be **objects** 
that can contain as much information as desired. Its a way to more easily represent the world around us.
Think of any object, for this we will use a car. We can identity as few or as many ways to describe the car. 

* Brand            - "Jeep"
* Make             - "Liberty"
* Year             - 2006
* Owner            - "Daniel S"
* Number of Wheels - 4 (you'll see why this is used)

We COULD represent all those values as different variables, but that would get very hard to follow once you 
introduce more and more cars...An easier way to handle all that data is to use a class! In Python and other 
OOP languages, classes let you define an Object - like a car - and easily assign it different attributes that 
can be pulled out and called whenever needed. You have to first declare the class - write out the abstract 
view - before you can create Objects using it. The generic way to declare a class is below. *Note: We introduce a 
new term 'kwargs' which will be explained after.*

```python
class ClassName:  # Tell Python you want a class and give it a name
    
    constant_1 = "value_1"  # Declare any attributes you want all objects of that type to have.
    constant_2 = "value_2"
    
    def __init__(self, attribute_1, **kwargs):  # The constructor that is called when an object is created.
        self.attribute_1 = attribute_1          # Set the object's attribute to the value that was passed.
        
        for k in kwargs.keys():                 # Any extra attributes that the user might want to add
            self.__setattr__(k, kwargs[k])      # get saved. 
```

`**kwargs` is just a dictionary. A dictionary has `key`s and `value`s. It is like a list but instead of using indices 
to find things, you use actual strings or objects to map from one thing to another. An example of a dictionary is below:

```python
stuff = {'name': 'Zed', 'age': 39, 'height': 6 * 12 + 2}
print(stuff['name'])
> Zed
print(stuff['age'])
> 39
print(stuff['height'])
> 74
stuff['city'] = "San Francisco"
print(stuff['city'])
> San Francisco
```

You will see that instead of just numbers we're using strings to say what we want from the stuff dictionary. We can also 
put new things into the dictionary with strings. It doesn't have to be strings though. We can also do this:

```python
stuff[1] = "Wow"
stuff[2] = "Neato"
print(stuff[1])
> Wow
print(stuff[2])
> Neato
print(stuff)
> {'city': 'San Francisco', 2: 'Neato', 'name': 'Zed', 1: 'Wow', 'age': 39, 'height': 74}

```

`**kwargs` is a dictionary but you don't know the length or the key names. It just lets you set more attributes that the 
user might pass where you don't actually know/care what they are when you declare the class. Its good practice to put 
it in there, even if you don't understand it fully.

And then to describe our car, we can create this:

```python
# Declare the class with a name
class Car:        # Declare a 'class' named 'Car'
    
    num_of_wheels = 4     # The number of wheels the car has. All cars have 4 wheels, so this is 
                          # outside of the '__init__()' function because this value never changes.
                           
    def __init__(self, brand, make, year, owner, **kwargs):  # This function is called when you create an object of 
        self.brand = brand                                   # type 'Car'. This creates all your 'descriptions'.
        self.make = make
        self.year = year                         # The four lines right here assign the values passed to the function
        self.owner = owner                       # to the attributes of the object so we can get/set them later.
        
        for k in kwargs.keys():                  # If any other values with keywords are passed, they will be added, 
            self.__setattr__(k, kwargs[k])       # say if we needed ' condition="good" ' to describe the car as well.
    
```

With this constructor, you can create a Car object and include your most important variables associated with it, while 
still being able to associate any other variables as well. So how would you use this class in your code? An example file
 is shown below, with everything shown.
 
```python

# Declare the class with a name
class Car:        # Declare a 'class' named 'Car'
    
    num_of_wheels = 4     # The number of wheels the car has. All cars have 4 wheels, so this is 
                          # outside of the '__init__()' function because this value never changes.
                           
    def __init__(self, brand, make, year, owner, **kwargs):  # This function is called when you create an object of 
        self.brand = brand                                   # type 'Car'. This creates all your 'descriptions'.
        self.make = make
        self.year = year                         # The four lines right here assign the values passed to the function
        self.owner = owner                       # to the attributes of the object so we can get/set them later.
        
        for k in kwargs.keys():                  # If any other values with keywords are passed, they will be added, 
            self.__setattr__(k, kwargs[k])       # say if we needed ' condition="good" ' to describe the car as well.
            

"""
Main running code below this comment
"""

def create_car():
    """
    This will call a bunch of inputs and return a new Car object
    """
    brand = input("What is the brand of your Car? ")
    make = input("What is the make of your Car? ")
    year = input("What is the year of your Car? ")
    owner = input("What is your name? ")
    return Car(brand, make, year, owner)  # This will create a Car object based on what we have above

my_first_car = create_car()  # Create one car using the function above

my_second_car = create_car() # Create another car using the function above (change the input values)

print(my_first_car.brand)  # Prints out whatever brand equalled above.
print(my_second_car.brand)  # Prints out whatever brand equalled above.

if int(my_first_car.year) < int(my_second_car.year):
    print("My second car is newer!")
else:
    print("My old car was newer")

```

