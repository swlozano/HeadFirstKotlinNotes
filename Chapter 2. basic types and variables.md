# Chapter 2. basic types and variables: Being a Variable

## Your code needs variables

### A variable is like a cup
![Screen Shot 2021-08-02 at 10 39 44 PM](https://user-images.githubusercontent.com/7098685/127954006-b2e831eb-581e-4287-af23-ae9589019757.png)

In order to create a variable, the compiler needs to know three things:
- What the variable’s name is.<br>
This is so we can use that name in our code.
- Whether or not the variable can be reused.<br>
If we initially set your variable to 2, for example, can we later set it to 3? Or should it
remain 2 forever?
- What type of variable it is.<br>
Is it an integer? A String? Or something more complex?

## What happens when you declare a variable
For this type-safety to work, the compiler needs to know the type of the variable. And the compiler
can infer the variable’s type from the value that’s assigned to it.

<i>To create a variable, the compiler needs to know its name, type and whether it can be reused.</i>


### The value is transformed into an object...
```kotlin
var x = 5
```

the value you’re assigning to the variable is used to create a new object. In this example, you’re assigning the number 5 to a new variable named x.

### ...and the compiler infers the variable’s type from that of the object
![Screen Shot 2021-08-02 at 10 42 58 PM](https://user-images.githubusercontent.com/7098685/127954300-b4575ce1-09d9-4490-9e39-b2c39ed3aea5.png)

## The variable holds a reference to the object
When an object is assigned to a variable, the object itself doesn’t go into the variable. A reference to the object goes into the variable instead:
![Screen Shot 2021-08-02 at 10 43 34 PM](https://user-images.githubusercontent.com/7098685/127954351-badd1d24-cc67-4b81-b728-319cd3617a4e.png)

### val vs. var revisited
![Screen Shot 2021-08-02 at 10 44 54 PM](https://user-images.githubusercontent.com/7098685/127954471-69348b39-c1f0-46f5-b50b-12b8a65c6b2c.png)

## Kotlin’s basic types

### Integers

Kotlin has four basic integer types: Byte, Short, Int and Long. Each type can hold a fixed number of bits. Bytes can hold 8 bits, for example, so a Byte can hold integer values from -128 to 127. Ints, on
the other hand, can hold 32 bits, so an Int can hold integer values from -2,147,483,648 to 2,147,483,647.

![Screen Shot 2021-08-02 at 10 46 11 PM](https://user-images.githubusercontent.com/7098685/127954565-e0ee5b26-4248-4517-bcef-7228447b07e3.png)

### HEXADECIMAL AND BINARY NUMBERS

- Assign a binary number by prefixing the number with 0b.<br>
x = 0b10
- Assign a hexadecimal number by prefixing the number with 0x.<br>
y = 0xAB
- Octal numbers aren’t supported.

### Floating points

There are two basic floating-point types: Float and Double. Floats can hold 32 bits, whereas Doubles can hold 64 bits.
By default, if you declare a variable by assigning a floating-point number to it using code like:<br>
var x = 123.5

you will create an object and variable of type Double. If you add an “F” or “f” to the end of the number, a Float will get created instead:<br>
var x = 123.5F

### Booleans
var isBarking = true 
var isTrained = false

### Characters and Strings
There are two more basic types: Char and String.<br>
Char variables are used for single characters. You create a Char variable by assigning a character in
single quotes like this:
```kotlin
var letter = 'D'
```

You create a String variable
by assigning the characters enclosed in double quotes:
```kotlin
var name = "Fido"
```
<i>Char variables are used for single characters. String variables are used for multiple characters strung together.</i>

## How to explicitly declare a variable’s type

```kotlin
var smallNum: Short
```

### Declaring the type AND assigning a value
```kotlin
var z: Short = 6
```

## Use the right value for the variable’s type

```kotlin
var x: Int = 3.12
//This won't work
var tinyNum: Byte = 500
```

<i>The Kotlin compiler will only let you assign a value to a variable if the value and variable are compatible. If the value is too large or it’s the wrong type, the code won’t compile.</i>

## Assigning a value to another variable
```kotlin
var x = 5
var y = x
var z: Long = x
```

## We need to convert the value

An object has state and behavior<br>
Being an object means that it has two things: state and behavior.

### How to convert a numeric value to another type
![Screen Shot 2021-08-02 at 10 55 22 PM](https://user-images.githubusercontent.com/7098685/127955284-0717c98b-5158-43cb-bc41-343e599d83eb.png)

## Store multiple values in an array

### How to create an array
![Screen Shot 2021-08-02 at 10 57 23 PM](https://user-images.githubusercontent.com/7098685/127955412-ef718196-60cc-4058-a199-08e164b384aa.png)

println(myArray[0])
And if you want to get the size of the array, use<br>
myArray.size

### How to explicitly define the array’s type

```kotlin
var myArray: Array<Byte> = arrayOf(1, 2, 3)
```

## var means the variable can point to a different array
![Screen Shot 2021-08-02 at 11 00 45 PM](https://user-images.githubusercontent.com/7098685/127955635-3ec1d8f8-9324-4418-86c0-4d4ddab08106.png)

![Screen Shot 2021-08-02 at 11 01 20 PM](https://user-images.githubusercontent.com/7098685/127955676-0d728a1d-5503-4648-93c3-9fdd54adc06e.png)

## val means the variable points to the same array forever...
![Screen Shot 2021-08-02 at 11 01 57 PM](https://user-images.githubusercontent.com/7098685/127955712-98fc1ee0-0d6d-474d-9ec3-29f04f1f1341.png)

<i>Declaring a variable using val means that you can’t reuse the variable for another object. You
can, however, still update the object itself.</i>

### ...but you can still update the variables in the array
When you declare a variable using val, you’re telling the compiler that you want to create a variable that can’t be reused for other values. But this instruction only applies to the variable itself. If the variable holds a reference to an array, the items in the array can still be updated.

![Screen Shot 2021-08-02 at 11 03 13 PM](https://user-images.githubusercontent.com/7098685/127955798-e5fd7f00-d8af-4424-9577-654ba8bc33fa.png)
![Screen Shot 2021-08-02 at 11 03 48 PM](https://user-images.githubusercontent.com/7098685/127955864-57c218b8-20dc-413f-bb85-605db5932cfd.png)

