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

