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
