# Chapter 5. subclasses and superclasses: Using Your Inheritance

## Inheritance helps you avoid duplicate code

The class that contains the common code is called the superclass, and the classes that inherit from it are called subclasses.<br>
A superclass is sometimes called a base class, and a subclass is sometimes called a derived class. In this book, we’re sticking with superclass and subclass.

### An inheritance example
![Screen Shot 2021-08-03 at 11 51 22 AM](https://user-images.githubusercontent.com/7098685/128055008-6f55addd-ba12-4261-be50-c5b126ffc866.png)
<i>
A superclass contains common properties and functions that are inherited by one or more subclasses.<br>
A subclass can include extra properties and functions, and can override the things that it inherits.
</i>
![Screen Shot 2021-08-03 at 11 53 40 AM](https://user-images.githubusercontent.com/7098685/128055266-4aa1da76-976e-4e2a-b95f-a6130a2ca9e0.png)

## Use IS-A to test your class hierarchy
When you’re designing a class hierarchy, you can test if one thing should be a subclass of another by applying the IS-A test. Simply ask yourself: “Does it make sense to say type X IS-A type Y?” 
<br>
It makes sense, for example, for us to say “a Hippo IS-A Animal”. A hippo is a type of animal, so the Hippo class can sensibly be a subclass of Animal.
<br>
Keep in mind that the IS-A relationship implies that if X IS-A Y, then X can do anything that a Y can do (and possibly more), so the IS-A test works in only one direction. 

### Use HAS-A to test for other relationships

Suppose, for example, that you have two classes named Fridge and Kitchen. Saying “a Fridge IS-A Kitchen” makes no sense, and neither does “a Kitchen IS-A Fridge.” But the two classes are still related, just not through inheritance.

![Screen Shot 2021-08-03 at 2 51 07 PM](https://user-images.githubusercontent.com/7098685/128077217-8cde0048-ce37-476e-bbc4-dc44f7e65791.png)

## Declare the superclass and its properties and functions as open

Before a class can be used as a superclass, you have to explicitly tell the compiler that this is allowed. You do this by prefixing the name of the class—and any properties or functions you want to
override—with the keyword open

![Screen Shot 2021-08-03 at 2 54 48 PM](https://user-images.githubusercontent.com/7098685/128077698-fb49f86c-468d-4125-b7fa-05ea204d10f7.png)

Now that we’ve declared the Animal superclass as open, along with all the properties and functions
we want to override, we can start creating animal subclasses. Let’s see how to do this by writing the code for the Hippo class.

## How a subclass inherits from a superclass
![Screen Shot 2021-08-03 at 2 55 35 PM](https://user-images.githubusercontent.com/7098685/128077789-86b3eec4-b495-4cd6-ac65-e6ac713bd54e.png)

The Animal() after the : calls the Animal’s constructor. This ensures that any Animal initialization code—such as assigning values to properties—gets to run. Calling the superclass constructor is mandatory: if the superclass has a primary constructor, then you must call it in the subclass header or your code won’t compile. 

![Screen Shot 2021-08-03 at 2 57 21 PM](https://user-images.githubusercontent.com/7098685/128078016-15029c50-ad88-4833-862d-88ef460a1ab8.png)


## How (and when) to override properties

You override a property that’s been inherited from a superclass by adding the property to the subclass, and prefixing it with the override keyword.

![Screen Shot 2021-08-03 at 2 58 37 PM](https://user-images.githubusercontent.com/7098685/128078232-43fa71a2-0063-4c14-bb76-1b4616773dd1.png)

This means that if you define a property in the superclass using val, you must override it in the subclass if you want to assign a different value to it.

If a superclass property has been defined using var, you don’t need to override it in order to assign a
new value to it, as var variables can be reused for other values. You can instead assign it a new value in the subclass’s initializer block, as in this example:

![Screen Shot 2021-08-03 at 2 59 33 PM](https://user-images.githubusercontent.com/7098685/128078283-59ecf423-923a-4e28-8597-2fc478fa4911.png)

## Overriding properties lets you do more than assign default values

So far, we’ve only discussed how you can override a property to initialize it with a different value to the superclass, but this isn’t the only way in which overriding properties can help your class design:

- You can override a property’s getter and setter.
- You can override a val property in the superclass with a var property in the subclass.
- You can override a property’s type with one of the superclass version’s subtypes.

## How to override functions

![Screen Shot 2021-08-03 at 3 01 51 PM](https://user-images.githubusercontent.com/7098685/128078531-4c95db40-b059-4d15-addd-47d05a86e342.png)

### The rules for overriding functions

When you override a function, there are two rules that you must follow:

- The function parameters in the subclass must match those in the superclass.
- The function return types must be compatible.

## An overridden function or property stays open...

![Screen Shot 2021-08-03 at 3 04 02 PM](https://user-images.githubusercontent.com/7098685/128078773-b3c0a1a9-a949-4dd9-817a-857baa62ab32.png)


### ...until it’s declared final
If you want to stop a function or property from being overridden further down the class hierarchy, you can prefix it with final. 

![Screen Shot 2021-08-03 at 3 04 32 PM](https://user-images.githubusercontent.com/7098685/128078805-d832e293-065f-4825-bd84-f69f8e07f88f.png)

## Which function is called?

When you call a function on an object reference, you’re calling the most specific version of the function for that object type: the one that’s lowest on the inheritance tree.

![Screen Shot 2021-08-03 at 3 08 07 PM](https://user-images.githubusercontent.com/7098685/128079176-ab3a65c8-2e08-419e-8238-5c2c3fa6ed21.png)
![Screen Shot 2021-08-03 at 3 08 28 PM](https://user-images.githubusercontent.com/7098685/128079214-3a3c3155-29d3-4b77-a838-73fc0ba27bd8.png)

### Any place where you can use a superclass, you can use one of its subclasses instead
When you define a supertype for a group of classes, you can use any subclass in place of the
superclass it inherits from.

![Screen Shot 2021-08-03 at 3 09 52 PM](https://user-images.githubusercontent.com/7098685/128079374-e86329ec-c2a4-47f5-84f7-3d23c5463f83.png)


## When you call a function on the variable, it’s the object’s version that responds

Suppose, for example, that you assign a Wolf object to an Animal variable and call its eat function using code like this:
```kotlin
val animal: Animal = Wolf() 
animal.eat()
```
When the eat function gets called, it’s the version that’s in the Wolf class that responds. The system knows that the underlying object is a Wolf, so it gets to respond in a Wolf-like way.
You can also create an array of different types of animal, and get each one to behave in its own way.
As each animal is a subclass of Animal, we can simply add each one to an array, and call functions on each item in the array:
![Screen Shot 2021-08-03 at 3 12 01 PM](https://user-images.githubusercontent.com/7098685/128079656-621a6725-2037-4317-a55b-86eb2e509b71.png)

![Screen Shot 2021-08-03 at 3 12 22 PM](https://user-images.githubusercontent.com/7098685/128079730-bfb16638-21e1-45d2-9413-81c0f6b81577.png)

## You can use a supertype for a function’s parameters and return type

If you can declare a variable of a supertype (say, Animal), and assign a subclass object to it (say,
Wolf), what do you think might happen when you use a subtype as an argument to a function? Suppose, for example, that we create a Vet class with a function named giveShot:













