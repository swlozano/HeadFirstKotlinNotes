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
  
