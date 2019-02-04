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
###### Loops
```
val n =10
for (i <- 1 to n) print(i)
```

* It works with any collection
```
for (s <- "Hello") print(s)
```
