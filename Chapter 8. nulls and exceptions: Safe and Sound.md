# Chapter 8. nulls and exceptions: Safe and Sound
![ch8_1](https://user-images.githubusercontent.com/7098685/127723846-a0ead02c-618c-47b4-949a-de8e187958c4.png)

## You can use a nullable type everywhere you can use a non- nullable type
**When defining variables and properties.**
var str: String? = "Pizza"
![ch8_2](https://user-images.githubusercontent.com/7098685/127723870-cbe14744-99c8-4e40-bf7e-79c7eec4da48.png)

**When defining parameters.**

```kotlin
fun printInt(x: Int?) { 
  println(x)
}
```

**When defining function return types.**
![ch8_3](https://user-images.githubusercontent.com/7098685/127723900-af77836b-d3d8-4cd7-9fc0-d099303a2981.png)

## How to create an array of nullable types
![ch8_4](https://user-images.githubusercontent.com/7098685/127723912-96537247-fec1-41d3-902b-bb7620315b86.png)
```kotlin
var myArray = arrayOf("Hi", "Hello", null)
```
![ch8_5](https://user-images.githubusercontent.com/7098685/127723932-dc15fcf4-f450-49fe-a1a1-6bf9b10b9cad.png)

## Keep things safe with safe calls

```kotlin
var w: Wolf? = Wolf()
```

![ch8_6](https://user-images.githubusercontent.com/7098685/127724016-775e5e19-cbbf-4e62-b612-8d3a06c320d2.png)

## You can chain safe calls together

Suppose you have a class named MyWolf that has a single Wolf? property named w. Here’s the class definition:
```kotlin
class MyWolf {
  var w: Wolf? = Wolf()
}
```
Suppose also that you have a MyWolf? variable named myWolf like this:
```kotlin
var myWolf: MyWolf? = MyWolf()
```
If you wanted to get the value of the hunger property for the myWolf variable’s Wolf, you could do so
using code like this:

![ch8_7](https://user-images.githubusercontent.com/7098685/127724128-fac7ab1f-3f1b-46ae-b0cc-5b6f48ebff86.png)

## Use let to run code if values are not null
When you use nullable types, you may want to execute code if (and only if) a particular value is not null. If you have a Wolf? variable named w, for example, you might want to print the value of w’s
hunger property so long as w is not null.
One option for performing this kind of task is to use the code:
```kotlin
if (w != null ) { 
  println(w.hunger)
}
```
An alternative approach that will work in all situations is to use the code:
![ch8_8](https://user-images.githubusercontent.com/7098685/127724275-98c88b5d-59af-4d30-8883-b972d142a8af.png)
```kotlin
  w?.let { println(it.hunger)
}
```

?.let allows you to run code for a value that’s not null.
Once you’ve established that the value is not null, you can refer to it in the body of the let using it.

![ch8_9](https://user-images.githubusercontent.com/7098685/127724335-06f3934a-70e6-4ab8-a9da-01d8f1eb94b4.png)

## Using let with array items

![ch8_10](https://user-images.githubusercontent.com/7098685/127724384-9960c51f-5936-41f1-b3f8-4f0820958392.png)

### Using let to streamline expressions

Suppose you have a function named getAlphaWolf that has a return type of Wolf? like this:
```kotlin
fun getAlphaWolf() : Wolf? { 
  return Wolf()
}
```

you could do so (in most situations) using the following code:
```kotlin
var alpha = getAlphaWolf() if (alpha != null) {
  alpha.eat() 
}
```

If you were to rewrite the code using let, however, you would no longer need to create a separate variable in which to hold the function’s return value. Instead, you could use:
![ch8_11](https://user-images.githubusercontent.com/7098685/127726005-97377bf2-72fb-449b-9a92-ad1f594d292d.png)

## Instead of using an if expression...

if (w != null) w.hunger else -1

**...you can use the safer Elvis operator**
w?.hunger ?: -1

## The !! operator deliberately throws a NullPointerException
![ch8_12](https://user-images.githubusercontent.com/7098685/127726105-349ce0c1-5e74-45b3-99eb-2a67af122d11.png)


## An exception is an object of type Exception
![ch8_13](https://user-images.githubusercontent.com/7098685/127726163-0cd494b0-8bd4-4f67-a328-988fd92ad1dd.png)

You can also create your own types of exception by defining a new class with Exception as its superclass. The following code, for example, defines a new type of exception named<br>
AnimalException:<br>

```kotlin
class AnimalException : Exception() { }
```

The safe alternative is to perform a safe cast using the as? operator using code like this: 
```kotlin
val wolf = r as? Wolf
```
This casts r as a Wolf if r holds an object of that type, and returns null if it doesn’t. This saves you from getting a ClassCastException if your assumptions about the variable’s type are
incorrect.
<i>as? lets you perform a safe explicit cast. If the cast fails, it returns null.</i>

**You can explicitly throw exceptions**
![ch8_14](https://user-images.githubusercontent.com/7098685/127726259-2aa0105b-80dd-4c72-bb0d-e6d6cf872538.png)

## try and throw are both expressions
Unlike in other languages such as Java, try and throw are expressions, so they can have return values.

### How to use try as an expression
![ch8_15](https://user-images.githubusercontent.com/7098685/127726310-6bddedd5-ddd7-4caa-a68a-09c06965623e.png)

### How to use throw as an expression

throw is also an expression, so you can, for example, use it with the Elvis operator using code like this:
```kotlin
val h = w?.hunger ?: throw AnimalException()
```
If w and hunger are not null, the above code assigns the value of w’s hunger property to a new variable named h. If, however, w or hunger are null, it throws an AnimalException.

**BULLET POINTS**
- null is a value that means a variable doesn’t hold a reference to an object. The variable exists, but it doesn’t refer to anything.
- A nullable type can hold null values in addition to its base type. You define a type as nullable by adding a ? to the end of it.
- To access a nullable variable’s properties and functions, you must first check that it’s not null.
- If the compiler can’t guarantee that a variable is not null in between a null-check and its usage, you must access properties and functions using the safe call operator (?.).
- You can chain safe calls together.
- To execute code if (and only if) a value is not null, use ?.let.
- The Elvis operator (?:) is a safe alternative to an if expression.
- The not-null assertion operator (!!) throws a NullPointerException if the subject of your assertion is null.
- An exception is a warning that occurs in exceptional situations. It’s an object of type Exception.
- Use throw to throw an exception.
- Catch an exception using try/catch/finally.
- try and throw are expressions.
- Use a safe cast (as?) to avoid getting a ClassCastException.
