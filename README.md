# recap-scala
* It runs on JVM.
* It can interoperate with Java.
* supports
    * OO programming.
    * Functional programming.
* simple and concise syntax.
* Type inference.
* Tool support.

#### Installation
* Runs on JVM.
* Statically typed. compiler tell error.
* Scalable from simple scripts to complex libraries.
* Runs on JVM.
* Scala sheets are interactive-- like sheel

#### Varaibale
* val is for immutable variable (final in java) ```val answer = 8+5+2```
* var is for mutable variable  ```var response=43; response=50```
* Strongly Typed - We can't change the data type of variable once a value is assigned to a variable
```
var i = 5
i ="String"  // will give compile error
```
* There are no primitive type in Scala.
* Specifying Data type is optional
   ```
   var greeting:String = null;
   ```
* Semicolon are optional at the end of statement.

###### Scala Types

* Int, Double, Byte, Char, Short, Long, Float, Boolean
* Everything is object eg ``` 1.to(10) ```
* Scala provides lot of additional method for java string eg
``` "Hello".intersect("world") // lo ```

``` "ABC".sum ``` 'A' + 'B' + 'C' - return type of same value ie character Ae
``` "ABC".sum.toInt will give integer value ```
* We can use regular arthemetic operators on big numbers
``` 
var x:BigInt = 103434;
x*x*x+67*7
```

* Two ways of writing method have single paramater
``` 1.to(10) === 1 to 10 ```

###### Scala also has functions and methods

* If method doesn't have any parameters then we can skip () ``` "Hello".length ```
``` "Hello(4)" gives o```
``` "Hello".apply(4) same as above ```

###### Imports
* Imports can be anywhere in the program.
* ``` * is replaced by _ in scala ```
* 1.to(10).map(sqtr(_)) will applu sqtr on the each element of range and will return a sequence.

###### Branching

* If expression always return a value
``` 
val x =4
val i = if (x > 1) 1 else 0
```
* If the if blocks have different data types, then data type will be super of both expressions eg ANY
* Unit is simillar to void.
* Blocks are expression. Blocks in scala returns the last value of block. If the last value is assignment, then return value will be Unit
```
val area = {
   val l = 1;
   val b = 2;
   val w = 3;
   l*b*w
}

```
##### Loops
###### For
```
val n =10
for (i <- 1 to n) print(i)
```

* It works with any collection
```
for (s <- "Hello") print(s)
```
###### Multiple generators
``` for (i <- 1 to 3; j <- 1 to 2) println (i+j)  // j will be executed 2 times each i iterations ```
###### Guards
``` for (i <- 1 to 3; j <- 1 to 2 if i!=j) println (i+j) ```
###### For Yield - for collecting results - similar to map functions
``` for (i <- 1 to 10) yield i % 3``` // returns a vector here

##### Functions
* return type is inferred
* = is used when a function returns a value, otherwise they are procedure. If = is not used Unit is returned from function
``` def sum(i:Int,j:Int) = i+j ```
``` def sum(i:Int,j:Int):Int = i+j ```
* We can have **named** parameters in a function. Simillar to Python
* We can have **default** parameter in a function. Simillar to Python
* Vargs in function
```
def sum(args: Int*) = {
   var result =0;
   for (arg <- args) result =+ arg
   result
}

Cant pass seq object in above function. to use seq do val s = sum(1 to 5 : _*)
```

##### Collections

###### Arrays
* val nums = new Array[Int](10); // All intialized to 0
* val stringArray = Array("Hello" , "World") // The type is inferred
* Assigning value to array ``` stringArray(0) = "Remove Hello" ```
* Assigning value to array ``` stringArray(0) ```
* Iterating array
```
for (arr <- stringArray) println arr
or 
for (arr <- 0 until stringArray.length) println arr
```
###### ArrayBuffer similar to ArrayList in java (Variable length arrays)
* import scala.collections.mutable.ArrayBuffer
* val list = new ArrayBuffer[Int]

```
import scala.collections.mutable.ArrayBuffer
var ab = ArrayBuffer('a','b','c', 'd')
ab += 'e'
ab += ('f','g','h')
ab.remove(3)
ab.insert(3,'x')
ab.trimEnd(5) // removes last 5 elements

val a = ab.toArray
val b = a.toBuffer
ab.sum
ab.sorted // returns new sorted array
ab.reverse // return new reversed array
Array(1,2,3).mkString("|") // return "1|2|3"
```

###### Map - It is a collection of pairs -> is a operator to assign value to key (By default maps are immutable)

```
val cricketScores = Map("Sachin" -> 100, "Dravid" -> 80, "Sehwag" -> 50)
or mutable map
import scala.collections.mutable.Map
val cricketScores

val sachinScore = cricketScores("Sachin");
val dhoni = cricketScores.getOrElse("Dhoni",0)
cricketScores("Dhoni") = 60 // Only in case of mutable maps
```
* Add map value with =+
* remove map values with -=
* Iterating array

```
for ((k,v) <- scores) yield (v,k) // result of yield is of same type .. here it will return map
```

###### Tuples - Simillar to Table - Aggregate values of different type // Useful when a method return more than one value
* tuples are 1 based. Tuple start with 1
* val t = ("Neeraj",25,"Male",5.6)
t._2 will give 25

* Usual way to use tuples
```
val t = ("Neeraj",25,"Male", 4.5)                 //> t  : (String, Int, String, Double) = (Neeraj,25,Male,4.5)

val (_, age, sex,_) = t     // This will create age and sex as new variables and intialize it will 25 , Male
```
* Word count in scala
```
val words = new java.util.Scanner() /// complete this line
var count = Map[String,Int]()
while (words.hasNext) {
val word = words.next()
count = count + (word -> (count.getOrElse(word,0) + 1))
}
```
##### Do exercise - 22,23,24 before  moving forward
* To remove all negative numbers excluding first
```
import scala.collection.mutable.ArrayBuffer
val ab = ArrayBuffer(1,3,4,56,-5,6,-4,-2)
val elementsToRemove = (for (i <- 0 until ab.length if (ab(i) < 0)) yield (ab(i))).drop(1)
var x = for(e <- ab; if !elementsToRemove.contains(e)) yield (e)
```
* Word Count
```
object sheet1 {
import scala.io.Source
import scala.collection.mutable.ArrayBuffer
val bs = Source.fromFile("data.txt")

var words = ArrayBuffer[String]()

bs.getLines().foreach { lines =>
	words ++= lines.split("\\s+")
}

val wordCount = new scala.collection.mutable.HashMap[String,Int];
words.foreach {word =>
wordCount(word) = wordCount.getOrElseUpdate(word, 0) + 1
}
wordCount.toSeq.sortBy(_._2)
}
```

##### Classess
* A class can have instance variables as parameters like in functions.
* Or it can have instance variable like defined in java
* if val is used, getters are provide and if var is used getters are automaically provided
* We can have companion object with same in the same source file to contain static methods.
* We can avoid new keyword to instantiate the object by instantiating through its companion object.
* If class method does take any parameter, we can skip the ().
* Due to above rule we can't find out whether method or instance variable is called on an object.
* normal code can be written inside the class, that will get executed whenever the object is created or constructor is called.
```
class Time(val h: Int, val m: Int = 0) {

	// def this(h:Int) {this(h,0) } auxillary constructor when only h is provided

  val x: Boolean = if (0.to(23).contains(h) && 0.to(59).contains(m)) true else false

  if (!x) { throw new IllegalArgumentException }

  def before(other: Time) = h <= other.h && m < other.m
  override def toString = f"${this.h}:${this.m}%02d"

}

val t = new Time(13,0)
val t2 = new Time(13,56)

println(t.before(t2))

val t3 = new Time(25,61)
```
```

object s2 {
  println("Welcome to the Scala worksheet") //> Welcome to the Scala worksheet

  class Time(h: Int, m: Int) {
    private var minutesSinceMidnight = h * 60 + m
    def hours = minutesSinceMidnight / 60
    def minutes = minutesSinceMidnight % 60
    def minutes_+(newValue: Int) { minutesSinceMidnight = hours * 60 + newValue: Int }

    val x: Boolean = if (0.to(23).contains(h) && 0.to(59).contains(m)) true else false

    if (!x) { throw new IllegalArgumentException }

    def before(other: Time) = minutesSinceMidnight < other.minutesSinceMidnight

    override def toString = f"${this.h}:${this.m}%02d"

  }

  val morning = new Time(9, 34) //> morning  : s2.Time = 9:34
  val afternoon = new Time(12, 45) //> afternoon  : s2.Time = 12:45
}

```

```
object s2 {
  println("Welcome to the Scala worksheet")       //> Welcome to the Scala worksheet

  class Time(h: Int, m: Int) {
    private var minutesSinceMidnight = h * 60 + m
    def hours = minutesSinceMidnight / 60
    def minutes = minutesSinceMidnight % 60
    def minutes_+(newValue: Int) { minutesSinceMidnight = hours * 60 + newValue: Int }

    val x: Boolean = if (0.to(23).contains(h) && 0.to(59).contains(m)) true else false

    if (!x) { throw new IllegalArgumentException }

    def <(other: Time) = minutesSinceMidnight < other.minutesSinceMidnight

    override def toString = f"${this.h}:${this.m}%02d"
  }

  object Time {

    def apply(h: Int, m: Int) = {
      new Time(h, m)
    }
  }

  val morning = Time(9, 34)                       //> morning  : s2.Time = 9:34
  val afternoon = Time(12, 45)                    //> afternoon  : s2.Time = 12:45
  morning < afternoon                             //> res0: Boolean = true
}
```
##### Packages
* In scala packages are nested. eg com.mahajan.scala means package com contains package mahajan, package mahajan contains package scala.
* In scala package structure doesn't need to have simillar directory structure we have in java
* declaring com.mahajan.scala at top is shortcut to below structure

```
package com {
	package mahajan{
		package scala{
			class Employee {
			}
		}
	}
}
```

##### Imports
* In scala we use _ instead of * to import all classes inside a package
* In scala we don't need to use static while importing static methods/fields from a class.
* We can import multiple classes from same package in single statement ``` import java.awt.{Color,Font} ```
* We can define an alias for a class name while importing it ``` import java.util.{HashMap => JavaHashMap} ```
* We can hide a specific class while import ``` import java.{HashMap => _, _} ```
* Imports can be put anywhere in a class,method,block or outside class.

##### Inheritacnce
* Similar to Java

###### Traits - like interfaces
* Traits can have concrete methods.
* Traits can have concrete fields.
* Traits can have abstract fields.
* Traits are used with **extend** instead of implements.
* Traits cannot have construction parameter.
* Mixins - advance feature of mixing multiple traits
```
object s3 {

  trait Logger {
    def log(message: String) { println("No Logging") }
  }

  trait ConsoleLogger extends Logger {
    override def log(message: String) { println("ConsoleLogger " + message) }
  }

  trait FileLogger extends Logger {
    override def log(message: String) { println("FileLogger " + message) }
  }

  class HelloWorld extends Logger {
    def setName() {
      log("Hello World")
    }
  }

  var hw = new HelloWorld()                       //> hw  : s3.HelloWorld = s3$HelloWorld@1a86f2f1
  hw.setName()                                    //> No Logging

  hw = new HelloWorld() with ConsoleLogger
  hw.setName()                                    //> ConsoleLogger Hello World

  hw = new HelloWorld() with FileLogger
  hw.setName()                                    //> FileLogger Hello World
}

```
* We can add multiple layers in traits using mutiple **with** - In this super method is chossen based on the layering defined. In below example ShortLogger will called first, it will do something and call TimpeStampLogger using super and TimpeStampLogger will call   FileLogger

```
hw = new HelloWorld() with FileLogger with TimpeStampLogger with ShortLogger
```

#### Functional Programming
* Give function a name if used multiple times.
* Map is a fucntion that get applied to the each element of collection and returns a new collection.

```
object s3 {

 val tripple = (x:Int) => x * 3                   //> tripple  : Int => Int = s3$$$Lambda$3/2093176254@799f7e29
 def trippleUsingDef(x:Int) = x * 3               //> trippleUsingDef: (x: Int)Int
 
 Array(1,2,3,4).map(tripple)                      //> res0: Array[Int] = Array(3, 6, 9, 12)
 Array(1,2,3,4).map(trippleUsingDef)              //> res1: Array[Int] = Array(3, 6, 9, 12)
 Array(1,2,3,4).map(x => x * 3)                   //> res2: Array[Int] = Array(3, 6, 9, 12)
 Array(1,2,3,4).map((x:Int) => x * 3)             //> res3: Array[Int] = Array(3, 6, 9, 12)
 Array(1,2,3,4).map(_ * 3)                        //> res4: Array[Int] = Array(3, 6, 9, 12)
}
```
* Higher order function - function which consume other function
