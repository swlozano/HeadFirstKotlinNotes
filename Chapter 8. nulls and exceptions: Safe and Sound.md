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

