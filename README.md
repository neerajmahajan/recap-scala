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
* 1.to(10).map(sqtr(_))


