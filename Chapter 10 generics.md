# Chapter 10. generics: Know Your Ins from Your Outs

## Collections use generics

## How a MutableList is defined
![ch10_1](https://user-images.githubusercontent.com/7098685/127727018-8befd5a5-824e-4791-ad66-f08c39c0cd87.png)

MutableList uses “E” as a stand-in for the type of element you want the collection to hold and return. When you see an “E” in the documentation, you can do a mental find/replace to exchange it for whatever type you want it to hold.
<br>
MutableList<String>, for example, means that “E” becomes “String” in any function or variable declaration that uses “E”. And MutableList<Duck> means that all instances of “E” become “Duck”
instead.<br>
![ch10_2](https://user-images.githubusercontent.com/7098685/127727071-311125dc-8a13-45cd-867d-bc1c43636bef.png)

## Things you can do with a generic class or interface
- Create an instance of a generified class.
```kotlin
val duckList: MutableList<Duck>
duckList = mutableListOf(Duck("Donald"), Duck("Daisy"), Duck("Daffy")) 
val list = mutableListOf("Fee", "Fi", "Fum")
```
- Create a function that takes a generic type.
```kotlin 
fun quack(ducks: MutableList<Duck>) { 
  //Code to make the Ducks quack
}
 ````
- Create a function that returns a generic type
```kotlin  
  fun getDucks(breed: String): MutableList<Duck> {
//Code to get Ducks for the specified breed 
 }
  ```

  ## Create the Pet class hierarchy
  
