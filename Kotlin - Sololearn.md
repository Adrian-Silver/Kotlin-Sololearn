## Operators

#### NB:

Both, increment and decrement operators have **prefix** (before the name of the variable) and **postfix** (after the name of the variable) forms. The prefix form increments the variable and then uses it  
in the assignment statement. The postfix form uses the value of the variable first, before incrementing it.


## Comments

// for single-line comments

/* Insert commetn here */    - for multi-line comments

## Input
You can take values as input from the user using the **readline()** function.
 to convert to **Int** we need to use **toInt()**:

var a = readLine()!!.**toInt**()  
var b = readLine()!!.**toInt**()  
println(a+b)

!! is called the **not-null assertion operator**. - it defines that the expression on the left is not null, i.e., it has to have a valid value, which is not blank

## Conditionals

1. if Statement - 
   the condition in parenthesis should be a boolean expression. Code executes if condition is true
2. if else 
>
>
3.  else if 
   - You can have multiple else if statements but there can only be one else statement
   
#### Conditional Expressions
- Using if statements to assign a value to a variable

NB: If you only have one line of code, you can omot the curly braces for if/else

```Kotlin
val num = -7
val result = if (num > 0) "Positive" else "Negative"
println(result)`
```

4. when
   - Each branch in a **when** expression is represented by a condition, an arrow (->), and a result.

```Kotlin
val num = -7
val result = when {
	num > 0 -> "Positive"
	num < 0 -> "Negative"
	else -> "Zero"
}
println(result)
```

   - are easier and shorter to read.


#### Combining Conditions

&& and ||

5. while loops

- repeats a block of code as long as a given condition is true

```Kotlin
var i =1
while (i <=5) {
	println("Hello")
	i ++
}
```

6. breaks - can be used to stop infinite loops when a certain condition is met.
7. continue


## Arrays

- Allow storage of multiple values in asingle variable.

e.g., `var contacts = arrayOf("John", "James", "Amy")`

index - used to access array elements `println(contacts[2]`

`contacts[1] = "Dave"`  


## For Loops

```Kotlin 
fun main(args: Array<String>) {
	var nums = arrayOf(2, 4, 6)
	for (x in nums) {
		println(x)
	}
}
```

- During each iteration of the **for** loop the **x** variable represents the current element of the **nums** array.

- can also be used to iterate over characters of a string
```Kotlin
fun main(args: Array<String>) {
	val name = "James"
	for (x in name) {
		println(x)
	}
}
```

```Kotlin
fun main(args: Array<String>) {
	val name = "James"
	println(name[1])
}
```

## Ranges
```Kotlin
fun main(args: Array<String>) {
	for (x in 'a'..'e') {
		println(x)
	}
}
```

- Note that both the starting and ending values are included in the range.
- You can check if a value is present in a range using the **in** operator:

```Kotlin
val x = 42
if(x in 15..100) {
	println("Yes")
}
```
- The **in** operator can also be used to check if a value is present in an array:

```Kotlin 
val x = arrayOf(8, 9, 42, 111)  
if(42 in x) {  
	println("Yes")  
}
```
- To iterate a number range which does not include its end element, use the **until** function: for (i in 1 **until** 5). In this case 5 is excluded.

---
# Functions
- Is a group of related code that is used to perform a task.
- The name in front of the parentheses is the function name, and the comma-separated values inside the parentheses are function **arguments**.
- **Arguments** provide input to our functions.
- The arguments are passed to the function in the same order as they are declared.

#### Returning from Functions

``` Kotlin
fun sum(x: Int, y: Int): Int {
return (x+y)
}

fun main(args: Array<String>) {
var result = sum(8, 42)
println(result)
}

```

- Note, that the return type is provided after the parentheses, but before the body of the function.


### Anonymous Functions
```Kotlin
val f: (Int, Int) -> Int = {a,b -> a+b}
```

- The parentheses define the input type, while the arrow defines the return type.

```Kotlin
fun main(args: Array<String>) {
	val f: (Int, Int) -> Int = { a, b -> a+b }
	var result = f(8, 42)
	println(result)
}
```

- The anonymous function can be shortened as: **val f = { a:Int, b:Int -> a+b }** because Kotlin automatically understands the return type from the arguments.

```Kotlin
val f = {a:Int, b:Int -> a+b}
```


### forEach Loop
- Kotlin provides a **forEach** loop, which takes a function, defining the action to perform with each of the array elements.

```Kotlin
fun main(args: Array<String>) {
	var arr = arrayOf(1, 3, 5)
	arr.forEach {
		item -> println(item * 4)
	}
}
```
Output is :
4
12
20

- Kotlin provides an **it** keyword for the name of the elements in **forEach**. This allows you to shorten the code to the following:  
arr.forEach {  
println(**it** * 4)  
}

## Higher-Order Functions
- A function that can take another function as an argument.
- Are useful when you want tp change the behaviour of a function.

```Kotlin
fun apply(x:Int, action: (Int) -> Int): Int {  
	return action(x)  
}
```

- **apply** is a higher-order function which takes an integer and a function named **action** as its arguments.

``` Kotlin
fun apply(x:Int, action: (Int) -> Int): Int {
	return action(x)
}
fun main(args: Array<String>) {
	println(apply(4, {x -> x*2}))
	println(apply(4, {x -> x/2}))
}
```
**output**
8
2

**Note:**
As you can see, our anonymous functions don't need to define the type of its argument, because Kotlin automatically guesses it.

**Examples of Higher-order functions**

Kotlin has many higher-order functions.  
For example, the **filter**() function of an array takes a Boolean function and returns the elements that match the given condition.

```Kotlin
fun main(args: Array<String>) {
val arr = arrayOf(42, 3, 10, 4, 6, 1)

val res = arr.filter({ it > 5 }) // results in only elements greater than 5
println(res)  // [42, 10, 6]
}
```

---

# Object-Oriented Programming (OOP)

**Objects** can hold data and have function to model behaviour.
- A **class** is like a blueprint -( it defines the details of the house we will be building).
- Multiple objects can be built from a defined class.
- A property is a variable defined inside of a class.

```Kotlin
class User {
	var name = ""
	var age = 0
}

fun main(args: Array<String>) {
	val u1 = User()
	u1.name = "James"
	u1.age = 42
	println(u1.name)
}
```

### Constructors
- Constructors allow you to initialize properties when objects are created.  
- The constructor is defined using parentheses after the class name and includes the properties we want.

```Kotlin
class User(val name:String, val age:Int) {

}
fun main(args: Array<String>) {
	val u1 = User("James", 42)
	println(u1.name)
}
```

--> We can provide default values for the arguments

##### Constructor Keyword
- Kotlin allows you to create multiple constructors using the **constructor** keyword.
--> The constructors are like functions, taking arguments

```Kotlin
class User {
	var name = ""
	var age = 0

	constructor(nm: String) {
		name = nm
	}

	constructor(nm: String, a: Int) {
		name = nm
		age = a
	}
}

fun main(args: Array<String>) {
	val u1 = User("James", 42)
	val u2 = User("Amy")
	println(u1.name)
	println(u2.name)
}
```
**NB** The class has no ==***arguments***==
The arguments(parameters)  are in the constructors.


## Getters and Setters
- **Getter** - defines how the value is accessed
- **Setter** - defines how a new value is set.

```Kotlin
class User {  
	var name = ""  
  
	var age = 0  
	get() = field  
  
	set(value) {  
	field = value  
	}  
}
```


- The **get**() function defines how the value of the age property is accessed: it simply returns the current value using the **field** keyword.  
- The **set**() function sets the provided value using the **value** keyword.

```Kotlin
class User {
	var name = ""

	var age = 0
	get() = field-1

	set(value) {
		if(value < 0) {
			field = 18
		}
		else {
			field = value
		}
	}
	
}

fun main(args: Array<String>) {
	val u = User()
	u.age = -4
	println(u.age)
}
```

-->**Output is 17**


## Class Functions
- Can be called using dot syntax.

```Kotlin
class User(var name: String, var age: Int) {

	fun login() {
		println("Login from user " + name + " of age " + age)
	}
}

fun main(args: Array<String>) {
	var u = User("James", 42)
	u.login()
}
```
--> Login from user James of age 42

```Kotlin
class User(var name: String, var age: Int) {

	fun isAdult(): Boolean {
		if(age >= 18)
			return true
		else
			return false
	}
}

fun main(args: Array<String>) {
	var u = User("James", 42)
	println(u.isAdult())
}
```
--> true


## Inheritance
- Allows creation of classes based on other classes, inheriting their features.

```Kotlin
open class User(var name: String, var age: Int) {  
}  
  
class Admin(name: String, age: Int): User(name, age) {  
}  
  
class Moderator(name: String, age: Int): User(name, age) {  
}
```

**Note:**  the ***open*** keyword  -> allows inheriting from the class.
- By default, all classes are final and do not allow inheriting from them.
- The class you inherit from is called the **base class**, while the classes that inherit from the base class are called **derived**.

The inherited classes can have their own properties and functions: 

```Kotlin
open class User(var name: String, var age: Int) {
}

class Admin(name: String, age: Int): User(name, age) {
}

class Moderator(name: String, age: Int, var country: String): User(name, age) {
}

fun main(args: Array<String>) {
	val b = Moderator("Amy", 23, "USA")
	println(b.country)
}

```

**Note:**
When working with inheritance, each derived class should have an "**is a**" relationship with the base class. In our example, Moderator **is a** User, Admin **is a** User.  
However, you cannot have something like **Student** is a **Color**, so, in that case, inheritance should not be applied.


## Visibility Modifiers
- Kotlin provides visibility modifiers to restrict access to properties and methods.  
- Here are the common modifiers:  
	**public**: visible everywhere  
	**protected**: visible to the subclasses only  
	**private**: not visible from the outside   -> This allows to secure the property from direct modifications.
	**Internal**: visible inside its module only

- By default, all properties and methods are **public**, meaning you can access them using the dot syntax from anywhere in the code.


Now, when our **age** is **private**, we can define functions to access and modify its value:

```Kotlin
class User(var name: String, private var age: Int) {
	fun getAge():Int {
		if(age < 18)
			return 18
		else
			return age
	}

	fun setAge(a: Int) {
		if(a < 0)
			age = 18
		else
			age = a
	}
}

fun main(args: Array<String>) {
	val u1 = User("Amy", 23)
	u1.setAge(42)
	println(u1.getAge())
}
```

- Visibility modifiers can also be applied to class functions, as well as getters and setters.


## Abstract Classes
- In some cases the base class is only needed for its derived classes and you will not create any objects of the base class type.  
->For example, let's say all of our users are **Moderators** or **Admins**. In that case, we will never need to create an object of type **User**.  

In this situations we can define the base class as **abstract**:

```Kotlin
abstract class User(var name: String, var age: Int) {
}

class Admin(name: String, age: Int): User(name, age) {
}

class Moderator(name: String, age: Int, var country: String): User(name, age) {
}

fun main(args: Array<String>) {
	val a = Moderator("James", 42, "USA")
	println(a.age)
}
```
Now, we cannot create any **User** objects. Instead, we need to use **Admin** or **Moderator** types.

**Note:** Abstract classes are always **open**, so you do not need to use the **open** keyword.

- Abstract classes can also contain **abstract functions** - functions without any definition that the derived classes need to implement.
**NB:** All abstract functions must be implemented in the derived classes.

```Kotlin
abstract class User(var name: String, var age: Int) {
	abstract fun display()
	
}  

class Admin(name: String, age: Int): User(name, age) {

	override fun display() {
		println(name + " is " + age + " years old")
	}
}

class Moderator(name: String, age: Int, var country: String): User(name, age) {

	override fun display() {
		println(name + " is from " + country)
	}
}

fun main(args: Array<String>) {
	val a = Moderator("James", 42, "USA")
	a.display()
	val b = Admin("Amy", 19)
	b.display()
}
```