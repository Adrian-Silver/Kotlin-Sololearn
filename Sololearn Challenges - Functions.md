# Functions

## Letter Counter

You need to define a function, which takes a letter and a text as arguments, and **returns** the number of times the given letter appears in the given text.  
  
**Sample Input:**  
e  
awesome  
  
**Sample Output:**  
2

The given code takes the letter and the text as input and passes them to the **letter_count**() function. Define the **letter_count**() function so that the given code works as expected.

``` Kotlin
fun main(args: Array<String>) {
	val letter: Char = readLine()!![0]
	val text: String = readLine()!!
	val result = letter_count(letter, text)
	println(result)
}

fun letter_count(ch: Char, txt: String) : Int {
	var countL = 0
	for(c in txt) {
		if(ch==c){
		countL ++
		}
	}
	return countL
}
```


## Anonymous Functions

## First Letters

You are given code that should iterate through an array and output the first letters of each element.  
However, the code has errors.  
Fix the code to result in the expected output.

The first letters should be combined on the same line without any line breaks.

```Kotlin
fun main(args: Array<String>) {
	var arr = arrayOf("James", "Amy", "Sam", "Olie", "Bob")
	var res = ""
	
	arr.forEach() {
		item -> print(item[0])
		// print(it[0])
	}
	print(res)
}
```

## Filtering Names

You are given an array of names and need to output only the names that start with the given letter.  
The letter should be taken from user input.  
Each of the resulting names should be output on a separate line.

The given code takes the **letter** as input.

```Kotlin

fun main(args: Array<String>) {
	var letter = readLine()!![0]
	val names = arrayOf("John", "David", "Amy", "James", "Amanda", "Dave", "Bob", "Billy", "Bobby", "Diana", "Lenny", "Gina")

	names.forEach{
		jina ->
		if( jina[0] == letter){
			println(jina)
		}
	}
}

```


# Shipping Calculator

You are working on a eCommerce website and need to make a shipping cost calculator based on the order amount.  
The store uses the following cost structure:  
For orders in the US:  
- $75+ orders have free shipping  
- orders less than $75 have a shipping fee of 10% of the total order amount.  
  
For international orders, there is a 15% shipping fee, with a maximum of $50. This means that the maximum shipping fee for an international order is $50.  
  
You need to complete the given **shippingCost**() function, which takes the order amount and a Boolean indicating whether the order is international or not, and returns the shipping cost for that order.  
The return amount should be a **Double**.  
  
**Sample Input:**  
140.0  
true  
  
**Sample Output:**  
21.0

The order is for $140 and is international. So, the shipping cost would be 15%, which is **$21**.

```Kotlin
fun shippingCost(amount: Double, international: Boolean): Double {

	var cost: Double = 0.0
	
	if( international == false && amount >= 75.0) {
		cost = 0.0
	} else if(international == false && amount <75.0) {
		cost = amount * 0.10
	} else if( international == true) {
		cost = amount * 0.15
		if(cost > 50.0){
			cost = 50.0
		}
	}
	return cost
}

fun main(args: Array<String>) {
	val total = readLine()!!.toDouble()
	val international = readLine()!!.toBoolean()
	println(shippingCost(total, international))
}
```