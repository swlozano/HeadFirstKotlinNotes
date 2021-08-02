# Chapter 9. collections: Get Organized
## Arrays can be useful...
![Screen Shot 2021-08-01 at 11 48 49 AM](https://user-images.githubusercontent.com/7098685/127864533-1d06ff8e-34c2-4ee8-b3c5-809b5619833a.png)
![Screen Shot 2021-08-01 at 11 49 02 AM](https://user-images.githubusercontent.com/7098685/127864548-061d1de8-81a1-4eaf-84a7-fa4fec31eedf.png)

## ...but there are things an array can’t handle

### You can’t change an array’s size
When you create an array, the compiler infers its size from the number of items it’s initialized with. Its size is then fixed forever. The array won’t grow if you want to add a new item to it, and it won’t shrink if you want to remove an item.

### Arrays are mutable, so they can be updated

Another limitation is that once you create an array you can’t stop it from being amended. If you create an array using code like this:<br>
```kotlin
  val myArray = arrayOf(1, 2, 3)
```
there’s nothing to stop the array being updated like so:
```kotlin
  myArray[0] = 6
```
If your code relies on the array not changing, this may be a source of bugs in your application. So what’s the alternative?

## Collections

## List, Set and Map

### List - when sequence matters
![Screen Shot 2021-08-01 at 11 57 01 AM](https://user-images.githubusercontent.com/7098685/127865126-718d0d43-005f-4782-ab6e-8f7da3350a80.png)

### Set - when uniqueness matters
A Set doesn’t allow duplicates, and doesn’t care about the order in which values are held.
![Screen Shot 2021-08-01 at 11 57 57 AM](https://user-images.githubusercontent.com/7098685/127865227-6a7ede6f-25a9-4cf3-b19f-87df23ea8247.png)

### Map - when finding something by key matters
A Map uses key/value pairs. It knows the value associated with a given key. You can have two keys
that reference the same object, but you can’t have duplicate keys. 

![Screen Shot 2021-08-01 at 11 58 42 AM](https://user-images.githubusercontent.com/7098685/127865310-bdeafd28-b113-4fc6-a512-533fe24565f9.png)

Simple Lists, Sets and Maps are immutable, which means that you can’t add or remove items after the collection has been initialized. If you want to be able to add or remove items, Kotlin has mutable subtypes that you can use instead: MutableList, MutableSet and MutableMap.

## Fantastic Lists...
![Screen Shot 2021-08-01 at 12 00 23 PM](https://user-images.githubusercontent.com/7098685/127865989-7744ae55-e2f2-4931-bcd3-17cb4bb62f0f.png)

```kotlin
  val shopping: List<String>
  shopping = listOf("Tea", "Eggs", "Milk")
```

**...and how to use them**
![Screen Shot 2021-08-01 at 12 02 27 PM](https://user-images.githubusercontent.com/7098685/127866115-8c7b2920-0d1c-41f9-acba-78e968feacb1.png)

You can loop through all items in a List like so:
```kotlin
  for (item in shopping) println (item)
```
And you can also check whether the List contains a reference to a particular object, and retrieve its
index:

```kotlin
if (shopping.contains("Milk")) { 
  println(shopping.indexOf("Milk")) //Prints 2
}
```

As you can see, using a List is a lot like using an array. The big difference, however, is that a List
is immutable—you can’t update any of the references it stores.

## Create a MutableList...

you use the mutableListOf function instead:
```kotlin
  val mShopping = mutableListOf("Tea", "Eggs")
```
MutableList is a subtype of List, so you can call the same functions on a MutableList that you can
on a List. The big difference, however, is that MutableLists have extra functions that you can use to add or remove values, or update or rearrange existing ones.

![Screen Shot 2021-08-02 at 8 04 49 AM](https://user-images.githubusercontent.com/7098685/127866567-b4108b02-521b-4709-93c8-58ef4944bfe3.png)

**..and add values to it**

```koylin
mShopping.add("Milk")
mShopping.add(1, "Milk")
```
![Screen Shot 2021-08-02 at 8 06 21 AM](https://user-images.githubusercontent.com/7098685/127866752-00b08876-5b21-4b2c-a055-49fa9d8f7e00.png)

**You can remove a value...**
```kotlin
if (mShopping.contains("Milk")) { 
  mShopping.remove("Milk")
}
```

The second way is to use the removeAt function to remove the value at a given index.
```kotlin
if (mShopping.size > 1) { 
  mShopping.removeAt(1)
}
```
![Screen Shot 2021-08-02 at 8 08 55 AM](https://user-images.githubusercontent.com/7098685/127867060-c8cae27d-fa1e-4d6a-afac-90cd509cfb57.png)

**...and replace one value with another**
```kotlin
if (mShopping.size > 0) { 
  mShopping.set(0, "Coffee")
}
```
![Screen Shot 2021-08-02 at 8 10 11 AM](https://user-images.githubusercontent.com/7098685/127867203-94c83a88-4e64-4e53-a5a9-234629eeba78.png)

## You can change the order and make bulk changes...

![Screen Shot 2021-08-02 at 8 19 14 AM](https://user-images.githubusercontent.com/7098685/127868240-814651d1-c677-4f9f-8efa-2864d92aa17b.png)

Or you can use the shuffle function to randomize it: 
```kotlin
mShopping.shuffle()
```

And there are useful functions for making bulk changes to the MutableList too. You can, for example, use the addAll function to add all the items that are held in another collection. 

```kotlin
val toAdd = listOf("Cookies", "Sugar") 
mShopping.addAll(toAdd)
```

The removeAll function removes items that are held in another collection: 
```kotlin
  val toRemove = listOf("Milk", "Sugar")
  mShopping.removeAll(toRemove)
```

And the retainAll function retains all the items that are held in another collection and removes
everything else:
```kotlin
val toRetain = listOf("Milk", "Sugar") 
mShopping.retainAll(toRetain)
```

You can also use the clear function to remove every item like this:
![Screen Shot 2021-08-02 at 8 23 37 AM](https://user-images.githubusercontent.com/7098685/127868833-b93a172e-e6d2-4083-a579-59cd8166b7ac.png)

**...or take a copy of the entire MutableList**
It can sometimes be useful to copy a List, or MutableList, so that you can save a snapshot of its state. You can do this using the toList function. 

```kotlin
val shoppingCopy = mShopping.toList()
```

The toList function returns a List, not a MutableList, so shoppingCopy can’t be updated. 

## How to create a Set
If you need a collection that doesn’t allow duplicates, you can use a Set: an unordered collection with no duplicate values.
![Screen Shot 2021-08-02 at 8 34 38 AM](https://user-images.githubusercontent.com/7098685/127870252-07a5c5f9-292b-4fb3-8231-c387afca4049.png)

### How to use a Set’s values
A Set’s values are unordered, so unlike a List, there’s no get function you can use to get the value at a specified index. You can, however, still use the contains function to check whether a Set contains
a particular value using code like this:
![Screen Shot 2021-08-02 at 8 35 40 AM](https://user-images.githubusercontent.com/7098685/127870404-c108a8f7-9fa2-4176-9877-d06299c392c6.png)

And you can also loop through a Set like this:
```kotlin
  for (item in friendSet) println(item)
```

A Set is immutable, so you can’t add values to it, or remove existing ones. 

## How a Set checks for duplicates

1. The Set gets the object’s hash code, and compares it with the hash codes of the objects already in the Set.
![Screen Shot 2021-08-02 at 8 39 20 AM](https://user-images.githubusercontent.com/7098685/127870899-78b60fd2-add1-4b71-8ca6-40165b46393e.png)


2. The Set uses the === operator to compare the new value against any objects it contains with the same hash code.
![Screen Shot 2021-08-02 at 8 39 48 AM](https://user-images.githubusercontent.com/7098685/127870960-3d7ac40f-b502-4408-9d4d-125424a60462.png)

3. The Set uses the == operator to compare the new value against any objects it contains with matching hash codes.

![Screen Shot 2021-08-02 at 8 40 29 AM](https://user-images.githubusercontent.com/7098685/127871055-4fe13c6f-e3bf-433f-a992-3a5bfea8025a.png)

## Hash codes and equality

### Equality using the === operator
If you have two references that refer to the same object, you’ll get the same result when you call the hashCode function on each reference. If you don’t override the hashCode function, the default behavior (which it inherits from the Any superclass) is that each object will get a unique hash code.

![Screen Shot 2021-08-02 at 8 42 34 AM](https://user-images.githubusercontent.com/7098685/127871307-fe69d7ff-be75-4bd6-aaf2-09a9900bc363.png)

### Equality using the == operator
If you want a Set to treat two different Recipe objects as equal, or equivalent, you have two options: make Recipe a data class, or override the hashCode and equals functions it inherits from Any. Making Recipe a data class is easiest as it automatically overrides the two functions.

In the following example, one value will be added to the Set if Recipe is a data class:
```kotlin
val a = Recipe("Thai Curry") 
val b = Recipe("Thai Curry") 
val set = setOf(a, b)
```
![Screen Shot 2021-08-02 at 8 45 06 AM](https://user-images.githubusercontent.com/7098685/127871666-7023360d-2015-4c6f-a1a3-f97b6dfbf1fd.png)

## Rules for overriding hashCode and equals

If you decide to manually override the hashCode and equals functions in your class instead of using a data class, there are a number of laws you must abide by. Failure to do so will make the Kotlin
universe collapse because things like Sets won’t work properly, so make sure you follow them. Here are the rules:

- If two objects are equal, they must have matching hash codes.
- If two objects are equal, calling equals on either object must return true. In other words,
if (a.equals(b)) then (b.equals(a)).
- If two objects have the same hash code value, they are not required to be equal. But if
they’re equal, they must have the same hash code value.
- So, if you override equals, you must override hashCode.
- The default behavior of the hashCode function is to generate a unique integer for each object. So if you don’t override hashCode in a non-data class, no two objects of that type
can ever be considered equal.
- The default behavior of the equals function is to do a === comparison, which tests
whether the two references refer to a single object. So if you don’t override equals in a non-data class, no two objects can ever be considered equal since references to two different objects will always contain a different bit pattern.

<i>
a.equals(b) must also mean that a.hashCode() == b.hashCode()<br>
But a.hashCode() == b.hashCode() does not have to mean that a.equals(b)
</i>
