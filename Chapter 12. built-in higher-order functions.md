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
  
  
  
