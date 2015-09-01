# Useful Scala Stuff

A number of useful Scala things

### Table of contents

- [Documentation](#docs)
- [Tips](#tips)
- [Case Class](#case_class)
- [Collections](#collections)
- [Conversion](#conversion)
- [Default Parameters](#default_parameters)
- [flatMap](#flatmap)
- [for comprehension](#for_comprehension)
- [Formatting](#formatting)
- [function](#function)
- [Implicit](#implicit)
- [Intellij Shortcuts](#intellij_shortcuts)
- [map](#map)
- [Map Construct](#map_construct)
- [Pattern Matching](#pattern_matching)
- [Play View](#play_view)
- [Regex](#regex)
- [Return Type](#return_type)
- [Reverse Routing](#reverse_routing)
- [Tuple](#tuple)
- [Types](#types)
- [Val](#val)



<a name="docs">
## Docs
- [http://docs.scala-lang.org](http://docs.scala-lang.org)
- [http://www.scala-lang.org/api/current](http://www.scala-lang.org/api/current)
- [https://twitter.github.io](https://twitter.github.io)
- [http://nerd.kelseyinnis.com/blog/2013/01/07/resources-for-getting-started-with-functional-programming-and-scala](http://nerd.kelseyinnis.com/blog/2013/01/07/resources-for-getting-started-with-functional-programming-and-scala)



<a name="tips">
## Tips
- If a value doesn't change then make it a val, otherwise make it a method.
- Use the convention of appending `Opt` to options in views.
- If you have a string which is optional send it in as `stringOpt: Option[String] = None`.
- Use `stringOpt.isDefined` to check or use a `for comprehension` to extract the value out of an `Option`.
- Use `List.isEmpty` to see if List has content or use a `map` to extract out values.
- Send optional CSS classes in as `classes: Seq[String] = Nil` and use `classes.mkString(" ")` to pull out and create CSS class string.
- If no user input is needed then this page can be cached.
- Setup and use the scala repl it is a great way of working through things.
- Use IntelliJ it is your friend. 
- In IntelliJ Hovering over variables and using the `⌘` key will give you detailed information. 
- In IntelliJ pressing `.` at the end of a variable will give you hints as to what properties and methods are available.



<a name="case_class">
## Case class
Case classes are great for using as a transport or data transfer objects.

```java
case class Animal(breed: String, color: String, eyes: Int, owners: List[String] = Nil) {
    lazy val hasEyes = eyes > 0
    def hasOwner(owner: String) = owners.contains(owner)
}

val dog = Animal("barsha", "black", 2)
dog.hasEyes // true

val cat = Animal("siamese", "white", 1, List("ben", "danny"))
cat.hasEyes // true
cat.hasOwner("ben") // true
cat.hasOwner("george") // false
```

#### Abstract case classes
Setting up an error and success partially applied/curried case class 

```java
package message

abstract case class Message(category: String, message: String)

object Message {
  def error(message: String) = new Message("error", message) {}
  def success(message: String) = new Message("success", message) {}
}
```

Use `map` to add the request flash error message `Option[String]` to the `Message.error` case class

```java
val message = request.flash.get("error").map(Message.error)
```
>
request.flash.get("error"): Option[String]  
flashMsg: Option[FlashMessage]



#### Case class as argument for case class
```java
case class Owner(name: String, age: Int)

case class Pet(name: Option[String] = None, breed: String, owners: Seq[Owner]) {
  val showOwners = owners.map { owner =>
    s"${owner.name} is ${owner.age}"
  }.mkString(", ")
}

val zed = Pet(Some("zed"), "black cat", Seq(Owner("ben", 38), Owner("danny", 33)))
zed.showOwners // ben is 38, danny is 33
```



<a name="collections">
## Collections

#### Head
Get the `head` or first item in a collection

```java
val numbers = List(1,2,3,4,5)

numbers.head // List(1)
```

#### Tail
Select all elements except the first.

```java
numbers.tail // List(2,3,4,5)
```



<a name="conversion">
## Conversion
#### Int to float
Convert Int to float 

```java
52f
```



<a name="default_parameters">
## Default parameters

```java
case class Robot(
    name: String = "generic", 
    skills: List[String] = Nil, 
    isFriendly: Boolean = false, 
    hasWings: Option[Boolean] = None) 
    
val roboCop = Robot() // Robot(generic,List(),false,None)
```



<a name="flatmap">
## flatMap

`flatMap` will operate if the Option `ben.hair` is nonempty. The Option `ben.hair.style` is then returned from the flatMap. The flatMap will flatten to the original `Option[String]` providing either an Option `ben.hair.style` or `None` dependant on the value of `Option[String]` `ben.hair.style`.  
If `ben.hair` or `ben.hair.style` is None the else clause in the `getOrElse` will be used, otherwise the get will extract the `String` from the returned `Option[String]`.

```java
case class Hair(style: Option[String])
case class Person(name: String, hair: Option[Hair])

val ben = Person("ben", Some(Hair(Some("mohican"))))
val phil = Person("phil", Some(Hair(None)))
val danny = Person("danny", None)

ben.hair.flatMap(_.style).getOrElse("No Hair Style!") // mohican
phil.hair.flatMap(_.style).getOrElse("No Hair Style!") // No Hair Style!
danny.hair.flatMap(_.style).getOrElse("No Hair Style!") // No Hair Style!
```

## fold with flatMap

`flatMap` will operate if the Option `ben.hair` is nonempty. The Option `ben.hair.style` is then returned from the flatMap. The flatMap will flatten to the original `Option[String]` providing either an Option `ben.hair.style` or `None` dependant on the value of `Option[String]` `ben.hair.style`.  
If `ben.hair` or `ben.hair.style` is None the first clause in the `fold` will be evaluated, otherwise the `fold` will evaluate the second clause the `Implicit` `property` available on the `ben.hair.style` `String`.

```java
object Helper {
    implicit class RichString(s: String) {
        lazy val displayHair = s"You have the hair style: $s"
        def withName(name: String) = s"$name, ${displayHair.toLowerCase}"
    }
    def weLoveYourHair(s: String) = s"We love your $s hair style!"
}
```

```java
import Helper._

case class Hair(style: Option[String])
case class Person(name: String, hair: Option[Hair])

val ben = Person("ben", Some(Hair(Some("mohican"))))
val phil = Person("phil", Some(Hair(None)))
val danny = Person("danny", None)

ben.hair.flatMap(_.style).fold("No Hair Style!")(_.displayHair) // You have the hair style: mohican
phil.hair.flatMap(_.style).fold("No Hair Style!")(_.displayHair) // No Hair Style!
danny.hair.flatMap(_.style).fold("No Hair Style!")(_.displayHair) // No Hair Style!
```

#### Calling an Implicits method

```java
ben.hair.flatMap(_.style)
        .fold("No Hair Style!")(_.withName("ben")) // ben, you have the hair style: mohican
```

#### Calling a Helper method
A `fold` ran on a `nonEmpty` `Option` will send the `flatMap` argument as the first argument to the method in the folds second clause
```java
ben.hair.flatMap(_.style).fold("No Hair Style!")(weLoveYourHair) // We love your mohican hair style!
```



<a name="for_comprehension">
## for comprehension
Extract a value out of an option with a `for` comprehension

```java
val personOpt = Some("danny")

@for(person <- personOpt){
   @person
}
```

#### for comprehension with conditional 

```java
@for(person <- personOpt if (Config.stage == "PROD") {
    @person
}
```

#### for comprehension on a Map 
```java
case class Person(age: Int, gender: String)

val people = Map(
    "Ben" -> Person(38, "male"), 
    "Danny" -> Person(33, "male"), 
    "Naomi" -> Person(35, "female")
)
 
for ((name, person) <- people) {
    println(s"$name is ${person.gender} and is ${person.age} years old")
}

// Ben is male and is 38 years old
// Danny is male and is 33 years old
// Naomi is female and is 35 years old
```

#### for yield

```java
case class Friend(name: String, age: Int)

val friends = List(
    Friend("matt", 40), 
    Friend("jo", 41), 
    Friend("pete", 39),
    Friend("john", 39)
)

val friendDetails = for {
  friend <- friends
} yield s"${friend.name} is ${friend.age}"

// List(matt is 40, jo is 41, pete is 39, john is 39)
```

#### for yield with conditional

```java
val friends = List(
    Friend("matt", 40), 
    Friend("jo", 41), 
    Friend("pete", 39),
    Friend("john", 39)
)

val friendsUnder40 = for {
  friend <- friends
  if (friend.age < 40)
} yield s"${friend.name} is ${friend.age}"

// List(pete is 39, john is 39)
```

#### for yield extract and use Options
```java
case class Location(town: String, country: String)

val nameOpt = Some("ben")
val locationOpt = Some(Location("London", "United Kingdom"))

val detailOpt = for {
    name <- nameOpt
    location <- locationOpt
} yield  s"$name can be found in ${location.town} which is in the ${location.country}"

// Some(ben can be found in London which is in the United Kingdom)
```


<a name="formatting">
## Formatting

#### Number formatting

```java
val price = 345.679
f"$price%.2f" // 35.68
```

#### String interpolation

```java
val welcome = "Hi there"
val name = "ben"

s"$welcome ${name.toUpperCase}" // Hi there BEN
```



<a name="function">
## Function

```java

def predictWeather(day: String, country: String) = "rain"

predictWeather("wednesday", "United kingdom") // rain
```

Multiline
```java

def predictWeather(day: String, country: String) = {
    "rain"
}

```

With return type
```java

def predictWeather(day: String, country: String): String = {
    "rain"
}

```


<a name="implicit">
## Implicit class
Add properties and methods to a type. 

```java
object Helpers {
    implicit class RichInt(i: Int) {
        lazy val addTwo = i + 2
    }
}
```

```java
import Helpers._

4.addTwo // 6
```



<a name="intellij_shortcuts">
## Intellij shortcuts
#### Create scala test (place cursor on class name)
```
cmd + shift + t
```

#### Find call hierarchy (place cursor on class name)
```
cmd + alt + h
```



<a name="map">
## map

```java
Some("hello").map(string => string.toUpperCase) // SOME("HELLO")
```

shorthand
```java
Some("hello").map(_.toUpperCase) // SOME("HELLO")
```

multiline
```java
Some("hello").map { text =>
    text.capitalize
}

// SOME("Hello")
```

#### Underscore
Here you can see the underscore being used as the variable when iterating over the List
```java
List(1,2,3).map(_ * 2) // List[2,4,9]
```



<a name="map_construct">
## Map construct
You can use a Map and key to refer to a value by type

```java
@Config.genderDetails(gender)
```

```java
val genderDetails = Map(
  Female -> config.getString("gender.female.details"),
  Male -> config.getString("gender.male.details")
)
```



<a name="pattern_matching">
## Pattern Matching

#### Matching values

```java
val name = "anya"

name match {
    case "ben" => "Hello chap"
    case "anya" => "Hello chapess"
    case _ => "Hello" // wildcard
}

// Hello chapess
```

#### Using conditionals

```java
val person = "ben"
val age = 38

person match {
    case "ben" if age < 38 => "Hello young man"
    case "ben" if age == 38 => "Hello youngish man"
    case "ben" if age > 40 => "Hello old man!"
    case _ => "Hello"
}

// Hello youngish man
```



<a name="play_view">
## Play view

#### Fragment
If you wish to send in html as a parameter use currying

```java
@fragmentName(name: String)(content: Html)

Hello @name
<div>@content</div>
```

```java
@fragmentName("ben"){
    <p>some html and content</p>
}
```

#### fold 
With an `Option` you can use a `fold` in the view. First clause evaluated if `Option` is `None`, second if `Option` is nonEmpty

```java
val hello = Some("hello all")

@hello.fold {
    <div>Nothing to see here</div>
} { text =>
    <div>@text</div>
}
```

#### fold with match/case statement
You can use match/case statements on a type to define a return value from a fold

```java
@header = @{
    @personOpt.fold {
        "You are neither Male or Female (Default Value)"
    } { 
    case _: Female => "You are a female"
    case _: Male => "You are a male"
    }
}
```

#### fold on an Option
Use a fold to extract an options value and run a method (`toString`) on it

```java
val personOpt = Some("ben")

@personOpt.fold("no value")(._toUpperCase) // BEN
```

#### map
You can use a map

```java
val personOpt = Some("phil")

@personOpt.map { person =>
   do something with @person
}
```



<a name="regex">
## Regex

#### replace
```java
val story = "ben was jumping the hedge and landed on Danny who was sunbathing next to Anya"
"(ben)".r.replaceAllIn(story, "fred")
// fred was jumping the hedge and landed on Danny who was sunbathing next to Anya
```

#### firstMatch
```java
val rhyme = "Baa, baa, black sheep, Have you any wool? Yes, sir, yes, sir, Three bags full"

for (m <- "(s[^h,]+)".r.findFirstMatchIn(rhyme)) yield m  // Some(sir)
```



<a name="return_type">
## Return Type

#### Specify return type
```java
val hello: String = "hi there!"
def sayHello(text: String, name: String): String = {
    s"$text $name"
}

sayHello(hello, "fred") // hi there! fred
```



<a name="reverse_routing">
## Reverse Routing

routes.conf
```java
GET    /contact    controllers.Contact.index
```

To get a route in play you can use

```java
@routes.Contact.index // /contact
```



<a name="traits">
## Traits
You can use traits like interfaces, used to define a signature of an object or class. 
You can provide abstract and concrete implementations.
>
further reading on [traits](http://www.artima.com/pins1ed/traits.html#12.7)

```java
object Vehicle {
    
    trait Vehicle {
        val name: String // abstract
        val colour: String // abstract
        val wheels: Int // abstract
        def isBicycle = wheels == 2 // concrete
    }

    case class Car(name: String, colour: String, wheels: Int) extends Vehicle
    case class Bicycle(name: String, colour: String, wheels: Int) extends Vehicle
}

val fixie = Bicycle("fixie", "red", 2)
fixie.isBicycle // true

val polo = Car("polo", "black", 4)
fixie.isBicycle // false
```



<a name="tuple">
## Tuple 
Extract a tuple into variables

```java
val (secureFile, width) = imageDetails
```



<a name="types">
## Types

#### Option
`Option[String]` to populate either `Some("string")` or `None`

```java
val exampleOpt = Some("hi there")  
val exampleOpt = None
```



<a name="val">
## Val
#### Lazy val 
Is a val that is only calculated and stashed when needed

```java
lazy val userName = "ben"
```