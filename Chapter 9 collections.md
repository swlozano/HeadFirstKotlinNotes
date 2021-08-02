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

## List, Set and Map

### List - when sequence matters
![Screen Shot 2021-08-01 at 11 57 01 AM](https://user-images.githubusercontent.com/7098685/127865126-718d0d43-005f-4782-ab6e-8f7da3350a80.png)

### Set - when uniqueness matters
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
