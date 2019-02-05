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
