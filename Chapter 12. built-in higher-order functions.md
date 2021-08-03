# Chapter 12. built-in higher-order functions: Power Up Your Code

## Kotlin has a bunch of built-in higher-order functions

![Screen Shot 2021-08-02 at 5 35 16 PM](https://user-images.githubusercontent.com/7098685/127932138-8dec4516-b724-468b-afa7-a459773da02b.png)


### The min and max functions work with basic types

```kotlin
val ints = listOf(1, 2, 3, 4)
val maxInt = ints.max() //maxInt == 4
```

**The minBy and maxBy functions work with ALL types**

![Screen Shot 2021-08-02 at 5 36 15 PM](https://user-images.githubusercontent.com/7098685/127932209-d3af149b-b6e6-4043-903a-672fa5a07ca2.png)

And if you wanted to find the item with the lowest quantity value, you would use minBy:
![Screen Shot 2021-08-02 at 5 36 39 PM](https://user-images.githubusercontent.com/7098685/127932232-86a38f66-117c-4b47-9789-98781d4ccd66.png)

## A closer look at minBy and maxBy’s lambda parameter

```kotlin
{ i: item_type -> criteria }
```

the lambda’s parameter must have a type of Grocery:
```kotlin
{ i: Grocery -> criteria }
```

<i>minBy and maxBy work with collections that hold any type of object, making them much more flexible than min and max.</i>

### What about minBy and maxBy’s return type?


When you call the minBy or maxBy function, its return type matches the type of the items held in the collection. If you use minBy with a List<Grocery>, for example, the function will return a Grocery. And if you use maxBy with a Set<Duck>, it will return a Duck.
If you call minBy or maxBy on a collection that contains no items, the function will return a null value.
  
## The sumBy and sumByDouble functions

As you may expect, the sumBy and sumByDouble functions return a sum of the items in a collection according to some criteria which you pass to it via a lambda.
![Screen Shot 2021-08-02 at 5 40 17 PM](https://user-images.githubusercontent.com/7098685/127932514-d6ecf75d-46e3-4fea-99df-422d8391e481.png)

 And to return the sum of each unitPrice multiplied by the quantity value, you would use sumByDouble, as unitPrice * quantity is a Double:
```kotlin
  val totalPrice = groceries.sumByDouble { it.quantity * it.unitPrice }
```

### sumBy and sumByDouble’s lambda parameter
  
Just like minBy and maxBy, you must provide sumBy and sumByDouble with a lambda that takes this form:

  ```kotlin
{ i: item_type -> criteria } 
 ```

  ## Meet the filter function
  
  The next stop on our tour of Kotlin’s higher-order functions is filter. This function lets you search, or filter, a collection according to some criteria that you pass to it using a lambda.
  
  For most collections, filter returns a List that includes all the items that match your criteria, which you can then use elsewhere in your code. If it’s being used with a Map, however, it returns a Map. 
  
  ![Screen Shot 2021-08-02 at 5 45 38 PM](https://user-images.githubusercontent.com/7098685/127932869-9dbc6c48-0cb4-4db3-a368-d4a4184408aa.png)

### There’s a whole FAMILY of filter functions

  ![Screen Shot 2021-08-02 at 5 49 11 PM](https://user-images.githubusercontent.com/7098685/127933134-2b19e237-2bad-4dee-b95f-47d6e1bfa79a.png)

    
  You can find out more about Kotlin’s filter family in the online documentation:
  <a href="https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/index.html">https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/index.html</a>
  
## Use map to apply a transform to your collection  

To see how this works, suppose you have a List<Int> that looks like this: 
```kotlin
val ints = listOf(1, 2, 3, 4)
```
If you wanted to create a new List<Int> that contains the same items multiplied by two, you could do so using the map function like this:
  
![Screen Shot 2021-08-02 at 5 51 35 PM](https://user-images.githubusercontent.com/7098685/127933303-db19915d-9f03-4469-8a94-834f634d370e.png)

And you can also use map to create a new List containing the name of each Grocery item in groceries:
 ![Screen Shot 2021-08-02 at 5 52 17 PM](https://user-images.githubusercontent.com/7098685/127933369-d9d711b4-bd11-42ca-985f-0412774d38d4.png)

  ![Screen Shot 2021-08-02 at 5 52 43 PM](https://user-images.githubusercontent.com/7098685/127933399-6710485f-f154-49db-86de-830071dcaaf1.png)

 
### You can chain function calls together 

  ![Screen Shot 2021-08-02 at 5 53 39 PM](https://user-images.githubusercontent.com/7098685/127933464-28991033-1b1e-434d-9954-e083099eb7eb.png)

## forEach works like a for loop

```kotlin 
for (item in groceries) { 
  println(item.name)
}
```

And here’s the equivalent code using the forEach function:
  
  ![Screen Shot 2021-08-02 at 5 54 59 PM](https://user-images.githubusercontent.com/7098685/127933577-e4679506-441b-4678-ac3e-3e37b8aa337f.png)

  
**As forEach is a function, you can use it in function call chains.**
Imagine that you want to print the name of each item in groceries whose unitPrice is greater than
3.0. To do this using a for loop, you could use the code:
```kotlin
for (item in groceries) {
  if (item.unitPrice > 3.0) println(item.name)
}
``` 
But you can do this more concisely using:

```kotlin
groceries.filter { it.unitPrice > 3.0 } .forEach { println(it.name) }  
 ```

## forEach has no return value

Unlike other functions, however, the lambda’s body has a Unit return value. This means that you can’t
use forEach to return the result of some calculation as you won’t be able to access it. There is, however, a workaround.
  

### Lambdas have access to variables 
  
As you already know, a for loop’s body has access to variables that have been defined outside the loop. The following code, for example, defines a String variable named itemNames, which is then updated in a for loop’s body:
  
 ![Screen Shot 2021-08-02 at 5 59 20 PM](https://user-images.githubusercontent.com/7098685/127933891-b005ef51-5bb5-4a70-9ce5-521a370a3729.png)

  When you pass a lambda to a higher-order function such as forEach, the lambda has access to these same variables, even though they’ve been defined outside the lambda. This means that instead of
using the forEach function’s return value to get the result of some calculation, you can update a variable from inside the lambda body. The following code, for example, is valid:

  ![Screen Shot 2021-08-02 at 6 00 00 PM](https://user-images.githubusercontent.com/7098685/127933936-36cb66b0-735a-4a5c-b623-47f13d556109.png)

  The variables defined outside the lambda which the lambda can access are sometimes referred to as
the lambda’s closure. In clever words, we say that the lambda can access its closure.
  
  <i> Closure means that a lambda can access any local variables that it captures.</i>
 
## Use groupBy to split your collection into groups
  
 This function lets you group the items in your collection according to some criteria, such as the value of one of its properties
  
The groupBy function accepts one parameter, a lambda, which you use to specify how the function should group the items in the collection.
  
  ![Screen Shot 2021-08-02 at 9 16 29 PM](https://user-images.githubusercontent.com/7098685/127947091-cd6f83c5-8d67-459d-b52c-39fd7c217c2f.png)

 groupBy returns a Map. It uses the criteria passed via the lambda body for the keys, and each associated value is a List of items from the original collection. The above code, for example, creates a Map whose keys are the Grocery item category values, and each value is a List<Grocery>:
  
  ![Screen Shot 2021-08-02 at 9 17 40 PM](https://user-images.githubusercontent.com/7098685/127947166-888c835d-9ec2-4b96-b017-e68ef2d6899d.png)

  ## You can use groupBy in function call chains
![Screen Shot 2021-08-02 at 9 18 09 PM](https://user-images.githubusercontent.com/7098685/127947215-a40bd8f3-067e-4b09-b78c-e624470d9dd4.png)

  As the groupBy function uses the Grocery category values for its keys, we can print them by passing the code println(it.key) to the forEach function in its lambda:
  
  ![Screen Shot 2021-08-02 at 9 18 56 PM](https://user-images.githubusercontent.com/7098685/127947277-ba27b541-1629-4d24-a90c-a02d1f64dd14.png)

  And as each of the Map’s values is a List<Grocery>, we can make a further call to forEach in order to print the name of each grocery item
  
![Screen Shot 2021-08-02 at 9 19 46 PM](https://user-images.githubusercontent.com/7098685/127947348-1e24ff31-68b8-42d9-943e-5fa94ef6ff1c.png)
  
## How to use the fold function
  The fold function is arguably Kotlin’s most flexible higher-order function. With fold, you can specify an initial value, and perform some operation on it for each item in a collection.
  ![Screen Shot 2021-08-02 at 9 21 03 PM](https://user-images.githubusercontent.com/7098685/127947476-ec53801d-ebf9-436c-9895-39f875324108.png)
  

