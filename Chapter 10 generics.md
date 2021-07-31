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
 ![ch10_3](https://user-images.githubusercontent.com/7098685/127727187-05df1911-c896-4078-aae1-1a9230c2293d.png)
![ch10_4](https://user-images.githubusercontent.com/7098685/127727194-a57eb791-7bbb-4ba7-a35c-b32f8280d277.png)

  ## Define the Contest class
  
### Declare that Contest uses a generic type
  ![ch10_5](https://user-images.githubusercontent.com/7098685/127727208-873eac3b-2441-4e98-8e8f-21b87d3f366d.png)
  
The generic type name can be anything that’s a legal identifier, but the convention (which you should follow) is to use “T”. The exception is if you’re writing a collection class or interface, in which case the convention is to use “E” instead (for “Element”), or “K” and “V” (for “Key” and “Value”) if it’s a map.
  
**You can restrict T to a specific supertype**
  ![ch10_6](https://user-images.githubusercontent.com/7098685/127727245-e4e966f4-94af-4220-9585-deb8d7a0012e.png)

## Add the scores property
  
![ch10_7](https://user-images.githubusercontent.com/7098685/127727291-d1b50fb8-0d26-48b4-8458-27bb976e4c41.png)

 ### Create the addScore function
  ![ch10_8](https://user-images.githubusercontent.com/7098685/127727304-adf76c94-3f2d-4966-a60e-8a4775dfe93c.png)

##  Create the getWinners function

  ![ch10_9](https://user-images.githubusercontent.com/7098685/127727338-62e1a9c7-52d6-4831-9a00-5d030931335a.png)

 And here’s the code for the complete Contest class:
 
  ![ch10_11](https://user-images.githubusercontent.com/7098685/127727388-c2be188c-c780-47fd-b2e5-d38d8ddbe8ff.png)

 ## Create some Contest objects
 
  ![ch10_12](https://user-images.githubusercontent.com/7098685/127727411-818c6e6c-1226-423c-b46c-11f0fc756ec6.png)
![ch10_13](https://user-images.githubusercontent.com/7098685/127727426-dd7b8392-df5e-41b7-b65b-4712cbe47bc9.png)

  A Contest<Pet>, however, will accept any type of Pet, like this:
  
 ![ch10_14](https://user-images.githubusercontent.com/7098685/127727437-25cc7b11-5ba2-4544-b3be-6c30ba46402b.png)

 **The compiler can infer the generic type**
  ![ch10_15](https://user-images.githubusercontent.com/7098685/127727456-fc7d312a-d207-45b0-a711-f42b5c4578b0.png)

 Where appropriate, the compiler can also infer the generic type from its constructor parameters. If, for example, we’d used a generic type parameter in the Contest class primary constructor like this:<br>
  
class Contest<T: Pet>(t: T) {...}

  The compiler would be able to infer that the following code creates a Contest<Fish>:
 
![ch10_16](https://user-images.githubusercontent.com/7098685/127727496-0a5f55a9-b5b7-4ee7-b81e-e00fc16f0531.png)

  
## The Retailer hierarchy
  ![ch10_17](https://user-images.githubusercontent.com/7098685/127727587-5aeb9fcc-88fc-46e4-b546-e5dc9c9c7b3e.png)

## Define the Retailer interface
  
The Retailer interface needs to specify that it uses a generic type T, which is used as the return type for the sell function.
Here’s the code for the interface:

 ```kotlin
interface Retailer<T> { 
  fun sell(): T
}
```
  ![Screen Shot 2021-07-30 at 10 39 05 PM](https://user-images.githubusercontent.com/7098685/127727614-41e0ef4e-42dc-483c-828e-411e80045aaf.png)

  The CatRetailer, DogRetailer and FishRetailer classes need to implement the Retailer interface, specifying the type of object each one deals with.
  
  ![Screen Shot 2021-07-30 at 10 40 02 PM](https://user-images.githubusercontent.com/7098685/127727630-b9d2e6d6-d6b6-4eac-b8a4-e29423bc052b.png)

 Similarly, the DogRetailer class deals with Dogs, so we can define it like this:
  
  ![Screen Shot 2021-07-30 at 10 40 29 PM](https://user-images.githubusercontent.com/7098685/127727659-822d9751-f92c-4b30-9086-19b7e98d36b8.png)

 ## We can create CatRetailer, DogRetailer and FishRetailer objects...
  
```kotlin 
val catRetailer1 = CatRetailer()
val catRetailer2: CatRetailer = CatRetailer() 
  ```

  **...but what about polymorphism?**
  As CatRetailer, DogRetailer and FishRetailer implement the Retailer interface, we should be able to create a variable of type Retailer (with a compatible type parameter), and assign one of its subtypes to it. And this works if we assign a CatRetailer object to a Retailer<Cat> variable, or assign a DogRetailer to a Retailer<Dog>:
  ![Screen Shot 2021-07-30 at 10 45 04 PM](https://user-images.githubusercontent.com/7098685/127727754-545ff8c6-1f3d-4c24-a3d3-22ac42272441.png)
  
## Use out to make a generic type covariant
  If you want to be able to use a generic subtype object in a place of a generic supertype, you can do so
by prefixing the generic type with out. In our example, we want to be able to assign a Retailer<Cat> (a subtype) to a Retailer<Pet> (a supertype) so we’ll prefix the generic type T in the Retailer interface with out like so:
  ![Screen Shot 2021-07-30 at 10 46 52 PM](https://user-images.githubusercontent.com/7098685/127727784-02c65ab2-5fed-4910-a944-7e671bbe5311.png)

 
Making the above change means that a Retailer<Pet> variable can now be assigned Retailer objects that deal with Pet subtypes. The following code, for example, now compiles:
  
  ![Screen Shot 2021-07-30 at 10 48 06 PM](https://user-images.githubusercontent.com/7098685/127727802-0898b594-3923-460f-be9d-c580ce4cf991.png)

 In general, a class or interface generic type may be prefixed with out if the class has functions that use it as a return type, or if the class has val properties of that type. You can’t, however, use out if the class has function parameters or var properties of that generic type.
  
  ![Screen Shot 2021-07-30 at 10 48 39 PM](https://user-images.githubusercontent.com/7098685/127727820-1b87a74b-9d1d-4b5e-9058-3b6726fc1be5.png)

 ### Collections are defined using covariant types
 The List collection, for example, is defined using code like this: 
  <br>
 public interface List<out E> ... { ... }
 
This means that you can, say, assign a List of Cats to a List of Pets, and the code will compile:<br>
Now that you’ve seen how to make generic types covariant using out, let’s add the code we’ve written to our project.

```kotlin  
val catList: List<Cat> = listOf(Cat(""), Cat("")) 
val petList: List<Pet> = catList
```
 
## We need a Vet class
  ![Screen Shot 2021-07-30 at 10 52 28 PM](https://user-images.githubusercontent.com/7098685/127727905-aa45ecf7-0dff-4b36-bc69-c38bae5c9601.png)
**Assign a Vet to a Contest**
  ![Screen Shot 2021-07-30 at 10 53 43 PM](https://user-images.githubusercontent.com/7098685/127727932-62bf1d40-4462-455e-90e9-da8c65ed8787.png)
## Create Vet objects

```kotlin
val catVet = Vet<Cat>() 
val fishVet = Vet<Fish>() 
val petVet = Vet<Pet>()  
 ```
![Screen Shot 2021-07-30 at 10 55 30 PM](https://user-images.githubusercontent.com/7098685/127727957-877709c4-9570-4737-a7ce-76ddbe67017c.png)
 
 **Pass a Vet to the Contest constructor**
  
```kotlin 
val catContest = Contest<Cat>(catVet) 
val petContest = Contest<Pet>(petVet) 
```
  ![Screen Shot 2021-07-30 at 10 56 55 PM](https://user-images.githubusercontent.com/7098685/127727988-a3f67af4-2cca-47a9-8a99-7db74ca54dfa.png)
 So what should we do in this situation?
## Use in to make a generic type contravariant
 In our example, we want to be able to pass a Pet<Vet> to a Contest<Cat> in place of a Pet<Cat>. In other words, we want to be able to use a generic supertype in place of a generic subtype.
In this situation, we can solve the problem by prefixing the generic type used by the Vet class with
in. in is the polar opposite of out. While out allows you to use a generic subtype in place of a supertype (like assigning a Retailer<Cat> to a Retailer<Pet>), in lets you use a generic supertype in place of a subtype. So prefixing the Vet class generic type with in like this:
  
  ![Screen Shot 2021-07-30 at 10 58 10 PM](https://user-images.githubusercontent.com/7098685/127728001-04d17931-67bd-4422-9d1d-25cbab50bb70.png)
  
 ![Screen Shot 2021-07-30 at 10 58 44 PM](https://user-images.githubusercontent.com/7098685/127728008-1a51771d-f232-43a1-bf62-b533df3f3456.png)
  
## A generic type can be locally contravariant 

uppose, for example, that we want to be able to use a Vet<Pet> reference in place of a Vet<Cat>, but only where it’s being passed to a Contest<Cat> in its constructor. We can achieve this by removing the in prefix from the generic type in the Vet class, and adding it to the vet property in the Contest constructor instead.<br>
Here’s the code to do this:
  ![Screen Shot 2021-07-30 at 11 02 39 PM](https://user-images.githubusercontent.com/7098685/127728068-60786fbc-49e3-414a-bf3a-dba9d6161b98.png)

  ![Screen Shot 2021-07-30 at 11 03 08 PM](https://user-images.githubusercontent.com/7098685/127728078-e9ac8231-98fb-4b69-beeb-fc524f4b3e0f.png)


  
  


