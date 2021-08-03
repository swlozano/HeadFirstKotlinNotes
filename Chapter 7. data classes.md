# Chapter 7. data classes: Dealing with Data

## == calls a function named equals

![Screen Shot 2021-08-03 at 4 04 57 PM](https://user-images.githubusercontent.com/7098685/128086023-71cb28c2-934a-4ca4-841d-2187f4324316.png)


If, however, w1 and w2 hold references to separate Wolf objects, comparing them with the == operator will evaluate to false, even if the objects hold identical property values.

![Screen Shot 2021-08-03 at 4 05 51 PM](https://user-images.githubusercontent.com/7098685/128086081-0e928ad9-6e26-40cc-9f3b-d3c837e2d713.png)

## equals is inherited from a superclass named Any

<i>Every class is a subclass of the Any class, and inherits its behavior. Every class IS-A type of Any without you having to say so.</i>


## The common behavior defined by Any

- equals(any: Any): Boolean
- hashCode(): Int
- toString(): String

<i>By default, the equals function checks whether two objects are the same underlying object. The equals function defines the behavior of the == operator.</i>

## A data class lets you create data objects
![Screen Shot 2021-08-03 at 4 08 12 PM](https://user-images.githubusercontent.com/7098685/128086365-f4b006c1-838a-4a9b-b6ef-582d4cbf6723.png)

### How to create objects from a data class

![Screen Shot 2021-08-03 at 4 08 52 PM](https://user-images.githubusercontent.com/7098685/128086459-385aff2a-062f-4181-9e57-03f4d0a57483.png)


## Copy data objects using the copy function
![Screen Shot 2021-08-03 at 4 10 03 PM](https://user-images.githubusercontent.com/7098685/128086596-f6655055-bca1-4782-8396-3af4f299cbd1.png)
If you wanted to create a copy of the Recipe object, altering the value of its isVegetarian property to true, you could do so using the copy function like so:

![Screen Shot 2021-08-03 at 4 10 24 PM](https://user-images.githubusercontent.com/7098685/128086638-6184dc57-3cd9-4ebc-b41d-71a1ebf91807.png)

## Data classes define componentN functions...
![Screen Shot 2021-08-03 at 4 11 16 PM](https://user-images.githubusercontent.com/7098685/128086729-27a25f53-0e48-443e-a2b5-6e8674323ce5.png)

If you wanted to retrieve the value of the object’s first property (its title property), you could do this by calling the object’s component1() function like this:

![Screen Shot 2021-08-03 at 4 11 43 PM](https://user-images.githubusercontent.com/7098685/128086781-864536c5-0eca-4fa7-8873-ba87760f9c40.png)

### ...that let you destructure data objects
![Screen Shot 2021-08-03 at 4 12 22 PM](https://user-images.githubusercontent.com/7098685/128086839-a6ce7aa2-30eb-4a68-aefc-aee8a2db9e90.png)

**The === operator always lets you check whether two variables refer to the same underlying object.**
<i>
== checks for object equivalence.<br>
=== checks for object identity.
  </i>

## Generated functions only use properties defined in the constructor

![Screen Shot 2021-08-03 at 4 29 03 PM](https://user-images.githubusercontent.com/7098685/128088773-61f1a8b8-acb6-4dba-80c7-6eb91e6d27c0.png)
![Screen Shot 2021-08-03 at 4 29 11 PM](https://user-images.githubusercontent.com/7098685/128088786-ac263f5c-e887-42e5-bee2-697743f0efed.png)

he == operator will only look at the title and isVegetarian properties to determine if the two objects are equal because only these properties have been defined in the data class constructor. If the
two objects have different values for the mainIngredient property (as in the above example), the equals function won’t look at this property when considering whether two objects are equal.

## Initializing many properties can lead to cumbersome code

Every data class must have a primary constructor, which must define at least one parameter. Each parameter must be prefixed with val or var.


### Default parameter values to the rescue!

![Screen Shot 2021-08-03 at 4 30 48 PM](https://user-images.githubusercontent.com/7098685/128088975-13105c52-bf14-494a-a61d-e226910bc2f4.png)

### How to use a constructor’s default values


1. Passing values in order of declaration
2. Using named arguments
![Screen Shot 2021-08-03 at 4 31 59 PM](https://user-images.githubusercontent.com/7098685/128089118-9025a6ec-80f7-47d1-9b60-751075151ac7.png)

### SECONDARY CONSTRUCTORS
![Screen Shot 2021-08-03 at 4 33 24 PM](https://user-images.githubusercontent.com/7098685/128089739-6c37dd54-c9ed-4ac2-8f11-255bdf5d0d2f.png)


## Functions can use default values too

![Screen Shot 2021-08-03 at 4 34 05 PM](https://user-images.githubusercontent.com/7098685/128089384-819711ec-6592-4755-a3ac-02359b211642.png)

## Overloading a function
Function overloading is when you have two or more functions with the same name but with different argument lists.

```kotlin
fun addNumbers(a: Int, b: Int) : Int { 
  return a + b
}
```

![Screen Shot 2021-08-03 at 4 35 41 PM](https://user-images.githubusercontent.com/7098685/128089536-6d5b65df-7f53-4664-8354-0f109c1bbab8.png)

<i>An overloaded function is just a different function that happens to have the same function name
with different arguments. An overloaded function is NOT the same as an overridden function.</i>

**Dos and don’ts for function overloading:**
1. * The return types can be different.
2. * You can’t change ONLY the return type.








