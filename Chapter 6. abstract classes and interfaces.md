# Chapter 6. abstract classes and interfaces: Serious Polymorphism
## The Animal class hierarchy revisited
![Screen Shot 2021-08-03 at 3 26 31 PM](https://user-images.githubusercontent.com/7098685/128081476-3f76cae4-3ff4-4fb4-b8fa-740c578f3524.png)

## Some classes shouldn’t be instantiated

### Declare a class as abstract to stop it from being instantiated

If you want to prevent a class from being instantiated, you can mark the class as abstract by prefixing it with the abstract keyword. Here’s how, for example, you turn Animal into an abstract class:

![Screen Shot 2021-08-03 at 3 27 28 PM](https://user-images.githubusercontent.com/7098685/128081577-01d82dde-c545-40cc-83ab-f399e808d3e0.png)

Being an abstract class means that nobody can create any objects of that type, even if you’ve defined a constructor for it.
![Screen Shot 2021-08-03 at 3 27 56 PM](https://user-images.githubusercontent.com/7098685/128081623-2d554b16-9375-4e8c-9a4e-29f39565d46b.png)
<i>If a superclass is marked as abstract, you don’t need to declare that it’s open.</i>

## Abstract or concrete?

A class that’s not abstract is called concrete, so that leaves Hippo, Wolf, Fox, Lion, Cheetah and
Lynx as the concrete subclasses.

![Screen Shot 2021-08-03 at 3 29 54 PM](https://user-images.githubusercontent.com/7098685/128081877-2c486dc6-8cc5-4ea0-8a1f-6b4a91a75c84.png)

## An abstract class can have abstract properties and functions
An abstract class can contain abstract and non-abstract properties and functions. It’s possible for an abstract class to have no abstract members.

### We can mark three properties as abstract
![Screen Shot 2021-08-03 at 3 30 57 PM](https://user-images.githubusercontent.com/7098685/128081995-1bad0df2-0c98-4d0b-b759-79a93acfbffe.png)
<i>Abstract properties and functions don’t need to be marked as open.</i>

## The Animal class has two abstract functions

 we can mark the makeNoise and eat functions as abstract by prefixing each one with the abstract keyword. Here’s the code to do this:
 
 ![Screen Shot 2021-08-03 at 3 32 39 PM](https://user-images.githubusercontent.com/7098685/128082177-96a925e4-7ebc-45c7-bc9c-c4e4acd87a69.png)


<i>If you mark a property or function as abstract, you must mark the class as abstract too.
If you put even one abstract property or function in a class, you have to mark the class as abstract or your code won’t compile.
</i>

**Abstract properties and functions define a common protocol so that you can use polymorphism.**
![Screen Shot 2021-08-03 at 3 34 52 PM](https://user-images.githubusercontent.com/7098685/128082452-1d6467b3-7cb5-40b7-a965-d08b4d46d24d.png)

## How to implement an abstract class
![Screen Shot 2021-08-03 at 3 35 49 PM](https://user-images.githubusercontent.com/7098685/128082590-2ae23ca6-bbdb-4356-9314-5c6ceadf95c6.png)
![Screen Shot 2021-08-03 at 3 36 01 PM](https://user-images.githubusercontent.com/7098685/128082605-eb911c5c-7ee6-4653-9871-9437a10b429a.png)

When you implement abstract properties and functions, you must follow the same rules for overriding that you use for overriding normal properties and functions:
- When you implement an abstract property, it must have the same name, and its type must be compatible with the type defined in the abstract superclass. In other words, it must be the same type, or one of its subtypes.
- When you implement an abstract function, it must have the same function signature (name and arguments) as the function that’s defined in the abstract superclass. Its return type must be compatible with the declared return type.

## You MUST implement all abstract properties and functions

The first concrete class in the inheritance tree below the abstract superclass must implement all abstract properties and functions.
<br>
With abstract subclasses, you have a choice: you can either implement the abstract properties and functions, or pass the buck to its subclasses.

## Let’s define the Roamable interface
![Screen Shot 2021-08-03 at 3 39 06 PM](https://user-images.githubusercontent.com/7098685/128082927-661804e3-ebbd-47d9-9aaa-3c12eb39dedc.png)

### Interface functions can be abstract or concrete
![Screen Shot 2021-08-03 at 3 39 47 PM](https://user-images.githubusercontent.com/7098685/128083019-0ca8cbfb-59fa-419d-88f3-386f4515199b.png)

You can also add concrete functions to interfaces by providing the function with a body. The following code, for example, provides a concrete implementation for the roam function:

![Screen Shot 2021-08-03 at 3 40 14 PM](https://user-images.githubusercontent.com/7098685/128083074-7c3725f2-f073-4a34-bf85-95aac58a4aa7.png)

## How to define interface properties

You add a property to an interface by including it in the interface body. This is the only way in which you can define an interface property, as unlike abstract classes, interfaces can’t have constructors.

![Screen Shot 2021-08-03 at 3 41 02 PM](https://user-images.githubusercontent.com/7098685/128083217-8015238b-2034-45eb-89fb-c5ef72a68bd8.png)

Unlike properties in abstract classes, properties that are defined in an interface can’t store state, and therefore can’t be initialized. You can, however, return a value for a property by defining a custom getter using code like this:
![Screen Shot 2021-08-03 at 3 41 46 PM](https://user-images.githubusercontent.com/7098685/128083344-9c45424b-388a-4112-abb3-7be985054049.png)
![Screen Shot 2021-08-03 at 3 42 49 PM](https://user-images.githubusercontent.com/7098685/128083396-dcd45f39-a2cf-4329-bdcb-56550332c52c.png)
![Screen Shot 2021-08-03 at 3 43 18 PM](https://user-images.githubusercontent.com/7098685/128083464-2c660c71-4ef5-4537-9c1f-e4f22ac80562.png)

## Declare that a class implements an interface...


### ...then override its properties and functions
![Screen Shot 2021-08-03 at 3 44 01 PM](https://user-images.githubusercontent.com/7098685/128083589-f6d74e72-e6ad-40b7-abae-2ab721ffb857.png)

<i>Concrete classes can’t contain abstract properties and functions, so they must implement all of the abstract properties and functions that they inherit.</i>

## How to implement multiple interfaces

![Screen Shot 2021-08-03 at 3 45 42 PM](https://user-images.githubusercontent.com/7098685/128083787-ff946adf-ef2b-4fec-ab2a-1cbb0b7aa0c5.png)

A class can also inherit from a superclass in addition to implementing one or more interfaces. Here’s
how, for example, you specify that class Y implements interface A, and inherits from class C:

![Screen Shot 2021-08-03 at 3 48 58 PM](https://user-images.githubusercontent.com/7098685/128084157-54f3eeed-07b5-4203-8064-01d66a450b7e.png)

![Screen Shot 2021-08-03 at 3 49 46 PM](https://user-images.githubusercontent.com/7098685/128084255-0b42a4df-aa3c-4436-a86b-5e74850c8113.png)

## How do you know whether to make a class, a subclass, an abstract class, or an interface?

- Make a class with no superclass when your new class doesn’t pass the IS-A test for any other type.
- Make a subclass that inherits from a superclass when you need to make a more specific version of a class and need to override or add new behaviors.
- Make an abstract class when you want to define a template for a group of subclasses. Make the class abstract when you want to guarantee that nobody can make objects of that type.
- Make an interface when you want to define common behavior, or a role that other classes can play, regardless of where these classes are in the inheritance tree.

## Interfaces let you use polymorphism
![Screen Shot 2021-08-03 at 3 52 17 PM](https://user-images.githubusercontent.com/7098685/128084524-e0c729da-761e-4732-9cac-bb26dd62ff01.png)

### Access uncommon behavior by checking an object’s type

![Screen Shot 2021-08-03 at 3 53 05 PM](https://user-images.githubusercontent.com/7098685/128084649-eeb776d7-4215-48b6-8cdf-5c1b6f62cceb.png)

In the above code, the compiler knows that the underlying object is a Wolf, so it’s safe to run any code that’s Wolf-specific. This means that if we want to call the eat function for each Animal object in an array of Roamables, we can use the following:

![Screen Shot 2021-08-03 at 3 53 37 PM](https://user-images.githubusercontent.com/7098685/128084706-8b77fb8e-66ec-4c3e-a7c8-b515e62b2434.png)

<i>Use the is operator to check if the underlying object is the specified type (or one of its
subtypes).</i>

## Where to use the is operator

### As the condition for an if
![Screen Shot 2021-08-03 at 3 54 58 PM](https://user-images.githubusercontent.com/7098685/128084838-0e371143-a38f-4abb-91c8-5c1726b5fda1.png)


### In conditions using && and ||
![Screen Shot 2021-08-03 at 3 55 47 PM](https://user-images.githubusercontent.com/7098685/128084928-32a51b22-9274-4147-b87a-36eac2a5cf7f.png)

You can also use !is to test if an object is not a particular type.

![Screen Shot 2021-08-03 at 3 56 17 PM](https://user-images.githubusercontent.com/7098685/128084988-b9a71061-17c1-44d4-a6f2-e02a8c1022d9.png)

In a while loop
If you want to use the is operator as the condition for a while loop, you can do so using code like this:
```kotlin
while (animal is Wolf) {
  //Code that runs while the Animal is a Wolf
}
```

## Use when to compare a variable against a bunch of options
A when statement is useful if you want to compare a variable against a set of different options. It’s like using a chain of if/else expressions, but more compact and readable.

![Screen Shot 2021-08-03 at 3 57 35 PM](https://user-images.githubusercontent.com/7098685/128085135-811187c2-405f-47ea-933f-90c83e006ef4.png)

![Screen Shot 2021-08-03 at 3 57 59 PM](https://user-images.githubusercontent.com/7098685/128085169-e07bdfce-082b-456a-abf0-aef23fe789ed.png)

You can also use when as an expression, which means that you can use it to return a value. The following code, for example, uses a when expression to assign a value to a variable:
```kotlin
var y = when (x) { 
  0 -> true
  else -> false 
}
```
## The is operator usually performs a smart cast

In most circumstances, the is operator performs a smart cast. Casting means that the compiler treats a variable as though its type is different to the one that it’s declared as, and smart casting means that the compiler automatically performs the cast on your behal

## Use as to perform an explicit cast
![Screen Shot 2021-08-03 at 4 01 27 PM](https://user-images.githubusercontent.com/7098685/128085622-2dab9531-431e-4a9a-b663-c824a27be940.png)














