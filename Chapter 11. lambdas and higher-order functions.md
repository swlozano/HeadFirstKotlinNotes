# Chapter 11. lambdas and higher-order functions: Treating Code Like Data

A lambda expression, or lambda, is a type of object that holds a block of code. You can assign a lambda to a variable, just as you can any other sort of object, or pass a lambda to a function which can then execute the code it holds. This means that you can use lambdas to pass specific behavior to a more generalized function.
The collections package has a built-in sortBy function, for example, that provides a generic implementation for
sorting a MutableList
![Screen Shot 2021-08-02 at 12 00 59 PM](https://user-images.githubusercontent.com/7098685/127897817-58cfa052-f5b8-44ea-8459-895d9ff5cb41.png)

**What we’re going to do**

1. Define a lambda.
You’ll discover what a lambda looks like, how to assign it to a variable, what its type is, and
how to invoke the code that it contains.
2. Create a higher-order function.
You’ll find out how to create a function that has a lambda parameter, and how to use a lambda as a function’s return value.

## What lambda code looks like
We’re going to write a simple lambda that adds 5 to an Int parameter value. Here’s what the lambda for this looks like:
![Screen Shot 2021-08-02 at 12 02 53 PM](https://user-images.githubusercontent.com/7098685/127897988-5971ac85-7ec1-44be-ae5e-1165cd50560d.png)

Int. Lambdas can have single parameters (as is the case here), multiple parameters, or none at all.<br>
The parameter definition is followed by ->. -> is used to separate any parameters from the body. It’s like saying “Hey, parameters, do this!”
<br>
Finally, the -> is followed by the lambda body—in this case, x + 5. This is the code that you want to be executed when the lambda runs. The body can have multiple lines, and the last evaluated expression in the body is used as the lambda’s return value.
<br>

## You can assign a lambda to a variable

val addFive = { x: Int -> x + 5 }
![Screen Shot 2021-08-02 at 12 05 40 PM](https://user-images.githubusercontent.com/7098685/127898305-105e0682-eed6-4288-9c69-90872ffa503b.png)
When you assign a lambda to a variable, you’re assigning a block of code to it, not the result of the code being run. To run the code in a lambda, you need to explicitly invoke it.

### Execute a lambda’s code by invoking it
You invoke a lambda by calling its invoke function, passing in the values for any parameters. The following code, for example, defines a variable named addInts, and assigns a lambda to it that adds together two Int parameters.

```kotlin
val addInts = { x: Int, y: Int -> x + y } 
val result = addInts.invoke(6, 7)
```
You can also invoke the lambda using the following shortcut:
```kotlin
val result = addInts(6, 7)
```

## Lambda expressions have a type

A lambda’s type is also known as a function type.
A lambda’s type takes the form:
```kotlin
(parameters) -> return_type
```
So if you have a lambda with a single Int parameter that returns a String like this: 
```kotlin
val msg = { x: Int -> "The value is $x" }
```
its type is:
```kotlin
(Int) -> String
```
When you assign a lambda to a variable, the compiler infers the variable’s type from the lambda that’s assigned to it, as in the above example. 

```kotlin
val add: (Int, Int) -> Int
add = { x: Int, y: Int -> x + y }
```

Similarly, the following code defines a variable named greeting that can hold a reference to a
lambda with no parameters, and a String return value: 

```kotlin
val greeting: () -> String = { "Hello!" }
val greeting: () -> String
```
![Screen Shot 2021-08-02 at 12 12 49 PM](https://user-images.githubusercontent.com/7098685/127899147-c6cf751e-bccf-4397-938b-4699d27b344e.png)
![Screen Shot 2021-08-02 at 12 13 14 PM](https://user-images.githubusercontent.com/7098685/127899157-83f0624a-2054-40f7-a8b5-1721c71e380f.png)
![Screen Shot 2021-08-02 at 12 13 21 PM](https://user-images.githubusercontent.com/7098685/127899166-873c7113-fb31-4251-93f2-eb9e003b96da.png)

## The compiler can infer lambda parameter types

![Screen Shot 2021-08-02 at 12 14 33 PM](https://user-images.githubusercontent.com/7098685/127899292-662cd0d0-b3a0-4c11-aea6-78e3947b8f69.png)
![Screen Shot 2021-08-02 at 12 14 39 PM](https://user-images.githubusercontent.com/7098685/127899298-f7d3b147-5cc4-4490-8cba-a9e8d6c2cf33.png)

### You can replace a single parameter with it

```kotlin
val addFive: (Int) -> Int = { x: Int -> x + 5 }
```

As the lambda has a single parameter, x, and the compiler can infer that x is an Int, we can omit the x
parameter from the lambda, and replace it with it in the lambda body like this:

```kotlin
val addFive: (Int) -> Int = { it + 5 }
```
![Screen Shot 2021-08-02 at 12 16 08 PM](https://user-images.githubusercontent.com/7098685/127899459-6f7fb13e-ab2a-412d-b7a1-970e3db0cf8d.png)

Intheabovecode,{ it + 5 }isequivalentto{ x -> x + 5 },butit’smuchmoreconcise. Note that you can only use the it syntax in situations where the compiler can infer the type of the
parameter. The following code, for example, won’t compile because the compiler can’t tell what type it should be:

![Screen Shot 2021-08-02 at 12 17 02 PM](https://user-images.githubusercontent.com/7098685/127899536-f64983ae-507c-4c95-8951-fb16b9efca1d.png)


## Use the right lambda for the variable’s type
