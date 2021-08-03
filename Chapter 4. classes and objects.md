# Chapter 4. classes and objects: A Bit of Class

## Object types are defined using classes

## How to design your own classes

When you want to define your own class, you need to think about the objects that will be created from that class. You need to consider:
- The things each object knows about itself. 
- The things each object can do.

The things an object knows about itself are its properties. They represent an object’s state (the data), and each object of that type can have unique values. A Dog class, for example, might have name, weight and breed properties. A Song class might have title and artist properties.

<i>The things an object knows about itself are its properties.</i>

The things an object can do are its functions. They determine an object’s behavior, and may use the object’s properties. <br>
<i>The things an object can do are its functions.</i>

## Let’s define a Dog class
![Screen Shot 2021-08-03 at 11 22 51 AM](https://user-images.githubusercontent.com/7098685/128051206-d7339c77-9099-4e18-9b6e-1b1f063d7746.png)

<i>A function that’s defined inside a class is called a member function. It’s sometimes called a method.</i>

## How to create a Dog object
![Screen Shot 2021-08-03 at 11 24 13 AM](https://user-images.githubusercontent.com/7098685/128051396-f7c98a2c-4196-4f74-8fc3-9227aa12e8e5.png)

## How to access properties and functions
![Screen Shot 2021-08-03 at 11 30 22 AM](https://user-images.githubusercontent.com/7098685/128052259-48d5da20-6f79-466f-a5b8-f30868413c90.png)

### What if the Dog is in a Dog array?
You can also add any objects you create to an array. If you wanted to create an array of Dogs, for example, you would use code like this:
![Screen Shot 2021-08-03 at 11 31 14 AM](https://user-images.githubusercontent.com/7098685/128052357-6f53f091-6bed-4877-a762-3752cdfbc4f5.png)
![Screen Shot 2021-08-03 at 11 31 37 AM](https://user-images.githubusercontent.com/7098685/128052412-03c04dcd-ec5a-458d-81b9-c2a258b824b3.png)

## Going deeper into properties
![Screen Shot 2021-08-03 at 11 34 01 AM](https://user-images.githubusercontent.com/7098685/128052743-7b4ac08b-4d97-40da-a030-315f2b88f8ef.png)

Here, the three constructor parameters—name_param, weight_param and breed_param—have no val and var prefixes, which means that they no longer define properties. They are plain old
parameters, just like the ones you see in function definitions. The name, weight and breed properties are instead defined in the main body of the class. Each one is assigned the value of the associated constructor parameter.

## Flexible property initialization
Defining properties in the main body of the class gives you a lot more flexibility than adding them to the constructor, as it means that you no longer have to initialize each one with a parameter value.
![Screen Shot 2021-08-03 at 11 37 37 AM](https://user-images.githubusercontent.com/7098685/128053223-e40c7caa-cb59-445a-ba90-46f94005f554.png)
Alternatively, you might want to tweak the value of a constructor parameter before assigning it to a
property. 
![Screen Shot 2021-08-03 at 11 38 40 AM](https://user-images.githubusercontent.com/7098685/128053354-4331611c-4f10-4eb6-bddd-6ecdfca7b37a.png)

## How to use initializer blocks
If you need to initialize a property to something more complex than a simple expression, or if there’s extra code you want to run when each object is created, you can use one or more initializer blocks.
Initializer blocks are executed when the object is initialized, immediately after the constructor is called, and they’re prefixed with the init keyword. Here’s an example of an initializer block that prints a message whenever a Dog object is initialized:

![Screen Shot 2021-08-03 at 11 39 57 AM](https://user-images.githubusercontent.com/7098685/128053543-2d4c4d49-0f4b-4ab2-92a7-640405c60897.png)
Your class can have multiple initializer blocks. Each one runs in the order in which it appears in the class body, interleaved with any property initializers. Here’s an example of some code with multiple initializer blocks:
![Screen Shot 2021-08-03 at 11 40 30 AM](https://user-images.githubusercontent.com/7098685/128053600-e82f2c3f-0265-4eb6-952b-a744e0afcbe4.png)

## You MUST initialize your properties

The following code, for example, won’t compile because
we’ve added a new property named temperament which hasn’t been initialized:

![Screen Shot 2021-08-03 at 11 41 30 AM](https://user-images.githubusercontent.com/7098685/128053740-a1a15e62-6d6d-4261-96fb-702e9ade2e2b.png)

## How do you validate property values?

### The solution: custom getters and setters
If you want to tweak a property’s return value, or validate a value before it gets assigned to a property, you can write your own getters and setters.


## How to write a custom getter
![Screen Shot 2021-08-03 at 11 44 23 AM](https://user-images.githubusercontent.com/7098685/128054132-3538a635-7a9d-42b5-b106-0787f41e4fde.png)

## How to write a custom setter
![Screen Shot 2021-08-03 at 11 45 26 AM](https://user-images.githubusercontent.com/7098685/128054233-23acd65d-6b4e-4bba-b547-7eeb793fb266.png)

The setter updates the value of the weight property by means of the field identifier. field refers to the property’s backing field, which you can think of as being a reference to the underlying value of the
property. 

Dont do That
![Screen Shot 2021-08-03 at 11 46 31 AM](https://user-images.githubusercontent.com/7098685/128054423-3f09d8bf-b16f-449f-a7da-c108fdb8823d.png)


A val property doesn’t need a setter because once it’s been initialized, its value can’t be updated.
<br>
the compiler secretly adds the following getters and setters when the code is compiled:
```kotlin
var myProperty: String
  get() = field 
  set(value) {
    field = value
  }
```
This means that whenever you use the dot operator to get or set a property’s value, behind the scenes its always the property’s getter or setter that gets called.


<i>Removing direct access to a property’s value by wrapping it in getters and setters is known as data hiding.</i>



















