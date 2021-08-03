# Chapter 3. functions: Getting Out of Main

## How you create functions

![Screen Shot 2021-08-03 at 11 00 45 AM](https://user-images.githubusercontent.com/7098685/128048109-ef0a8232-bee7-4775-8919-85e0665d8b4b.png)

### You can send things to a function
![Screen Shot 2021-08-03 at 11 01 30 AM](https://user-images.githubusercontent.com/7098685/128048198-00f1b6c0-2b18-4344-923b-dc6eaedec97e.png)
![Screen Shot 2021-08-03 at 11 02 04 AM](https://user-images.githubusercontent.com/7098685/128048290-3c99fd96-ddea-4dc3-a190-8c9ff63d8f1e.png)

## You can send more than one thing to a function

### Calling a two-parameter function, and sending it two arguments
![Screen Shot 2021-08-03 at 11 03 00 AM](https://user-images.githubusercontent.com/7098685/128048405-18d7ccc9-6dfd-4fc8-bf05-eda0a4b18c2b.png)

### You can pass variables to a function so long as the variable type matches the parameter type
![Screen Shot 2021-08-03 at 11 04 28 AM](https://user-images.githubusercontent.com/7098685/128048616-afd59016-80c3-4fc7-9a4f-e6251613ad72.png)

## You can get things back from a function
![Screen Shot 2021-08-03 at 11 05 08 AM](https://user-images.githubusercontent.com/7098685/128048719-60151c64-a0a6-466b-9714-d701b94fcd03.png)

If you declare that a function returns a value, then you must return a value of the declared type. As an example, the following code is invalid becuase it returns a String instead of an Int:
![Screen Shot 2021-08-03 at 11 05 37 AM](https://user-images.githubusercontent.com/7098685/128048818-c0b20ab9-458c-44fc-8c23-4026f6b6c987.png)

### Functions with no return value
![Screen Shot 2021-08-03 at 11 06 19 AM](https://user-images.githubusercontent.com/7098685/128048918-3bcd19c4-3861-477d-8f2b-f5498fbc5c6f.png)

## Functions with single-expression bodies

![Screen Shot 2021-08-03 at 11 07 07 AM](https://user-images.githubusercontent.com/7098685/128049039-7ee95c46-0aa3-46d3-9f9d-43389eecc8b4.png)

The function returns the result of a single if expression, which means that we can rewrite the function like so:

![Screen Shot 2021-08-03 at 11 07 16 AM](https://user-images.githubusercontent.com/7098685/128049068-2ddca3a3-76a8-4906-9692-f2ca7e9122b8.png)


## How for loops work

A for loop is useful in situations where you want to loop through a fixed range of numbers, or through every item in an array.

### Looping through a range of numbers

```kotlin
for (x in 1..10) {
  //Your code goes here
}
```

Note that the .. operator includes the end number in its range. If you wanted to exclude it, you would
replace the .. operator with until. As an example, the following code prints the numbers from 1 to 99, and excludes 100:
```kotlin
for (x in 1 until 100) 
  println(x)
```

### Use downTo to reverse the range
If you want to loop through a range of numbers in reverse order, you use downTo instead of .. or
until. As an example, you’d use the following code to print the numbers from 15 down to 1:
![Screen Shot 2021-08-03 at 11 11 17 AM](https://user-images.githubusercontent.com/7098685/128049638-8b53014e-0e1c-4e33-aa7f-efb909bffe13.png)

### Use step to skip numbers in the range

```kotlin
for (x in 1..100 step 2) 
  println(x)
```

### Looping through the items in an array

```kotlin
for (item in optionsParam) {
  println("$item is an item in the array")
}
```

You can even simplify the above loop by returning the array’s index and value as part of the loop:
![Screen Shot 2021-08-03 at 11 12 58 AM](https://user-images.githubusercontent.com/7098685/128049863-ae56fd77-adb1-41f2-ab44-dd72f67f922e.png)


### Use the readLine function to read the user’s input

```kotlin
val userInput = readLine()
```

### ‘And’ and ‘Or’ operators (&& and ||)

```kotlin
if (price <= 10 || price >= 1000) { 
  //Phone is too cheap or too expensive
}
```

If you want to use an “or” expression instead, you use the || operator:
```kotlin
if (price >= 200 && price <= 300) { 
  //Code to choose the phone
}
```

### Not equals (!= and !)
Suppose you wanted to run code for all phones except one model. To do this, you’d use code like the following:
```kotlin
if (model != 2000) {
  //Code that runs if model is not 2000
}
```
The != means “is not equal to”.<br>
Similarly, you can use ! to indicate “not”. As an example, the following loop runs while the isBroken variable is not true:
```kotlin
while (!isBroken) {
  //Code that runs if the phone is not broken
}
```

### Use parentheses to make your code clear

```kotlin
if ((price <= 500 && memory >= 16) || (price <= 750 && memory >= 32) || (price <= 1000 && memory >= 64)) { 
  //Do something   appropriate
}
```







