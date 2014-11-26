# Essential Essential Essential Scala

## Basic expressions

An *expression* evaluates to a *value*

### Literals

Literal expressions evaluate to "themselves".

~~~ scala
"Hello world" // evaluates to the String "Hello world"
1 // Evaluates to the Int 1
~~~

### Method Calls

A method call is an expression that evaluates to the result of the call

~~~ scala
1 + 2 // Evaluates to the Int 3
"Hello".toUpperCase // Evaluates to the String "HELLO"
~~~

Remember operator syntax means `a.b(c)` can be written as `a b c`

### Blocks

A block expression is used to group a number of expressions and declarations. Its type and result is that of the last expression in the block.

~~~ scala
{
  1 + 2
  3 + 4 
} // This entire block evaluates to 7 and has type Int
~~~

### Conditionals

Conditionals are also expressions. The syntax is

~~~ scala
if(2 < 3)
  "Yes"
else
  "No"
~~~

or

~~~ scala
if(2 < 3) {
  "Yes"
} else {
  "No"
}
~~~

## Classes

A *class* declares a new type. The syntax is

~~~ scala
case class Person(firstName: String, lastName: String)
~~~

We construct an instance (an object) from a class by providing values for the constructor arguments

~~~ scala
Person("Joe", "Citizen")
~~~

A class can contain methods and fields. The body of a method is an expression, and the result of a method is the result of evaluating its body.

~~~ scala
case class Person(firstName: String, lastName: String) {
  val awesome = true

  def name: String =
    s"$firstName $lastName"
}
~~~

Methods can take parameters. 

~~~ scala
case class Person(firstName: String, lastName: String) {
  def name: String =
    s"$firstName $lastName"

  def great(other: Person): String = {
    val otherName = other.name 
    s"$name says hi to $otherName"
  }
}
~~~

## Pattern Matching

Pattern matching is another kind of expression that provides an alternative to calling methods for interacting with objects.

~~~ scala
Person("Joe", "Citizen") match {
  case Person(first, _) => s"Hey $first, what's up?"
}
~~~

## Objects

Can we define literal objects, which are just like classes but there is only a single instance.

~~~ scala
object BritishMuseum {
  val free = true
  val awesome = true
  val fullOfLootedTreasure = true
  def greet(visitor: Person): String =
    s"Welcome to the British Museum, ${visitor.name}"
}
~~~

## Traits

Traits abstract over classes.

~~~ scala
trait Visitor {
  def id: String
}
case class Anonymous(id: String) extends Visitor
case class User(id: String, name: String) extends Visitor
~~~
