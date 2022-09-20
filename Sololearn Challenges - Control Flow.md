```Kotlin 
fun main() {
    var age = 144
// fun main(args: Array<String>) {
//     var age = readLine()!!.toInt()
    val group = when {
        age >= 65 -> "Senior"
        age >= 18  -> "Adult"
        age >= 12 -> "Teen"
        age>= 0 -> "Child"
        else -> "Invalid age"
    }
    println(group)
}
```

## while loops

## using breaks


``` Kotlin
fun main(args: Array<String>) {
	var sum = 0
	var i = 1
	
	while (i<=100) {
		sum += i
		i++
		if(sum > 1000) {
		break
		}
	}
	println(sum)
}
```

output is 1035


// using **continue** 
``` Kotlin
fun main(args: Array<String>) {
var sum = 0
var i = 1
while (i<=100) {
i++
if(i%2 != 0) {
continue
}
sum += i
}
println(sum)
println(i)
}
```

The code above skips the odd numbers in the loop using the **i%2 != 0** condition.

It is important to increment the loop variable **i** before the **continue** statement. If we increment it after the **continue** statement, the loop will become infinite, as it will not change the value of **i** before skipping the iteration.



  
# Continuous Input
  
The given code uses an infinite while loop to take continuous user input.  
During each iteration a number is taken from the input.  
You need to fix the program to stop the loop when the user enters **0** and output the number of inputs taken before that.  
  
**Sample Input:**  
42  
1  
66  
0  
  
**Sample Output:**  
3  

**Hint**: Use a **break** statement to stop the loop when the user input is 0.


``` Kotlin 
fun main(args: Array<String>) {
	var count = 0
	while(true) {
		var input = readLine()!!.toInt()
		if(input == 0){
		break
		}
		count ++
	}
	println(count)
}

```

## Arrays

# Day of the Week

The given program declares an array of weekday names.  
You need to take a number as input and output the name of the day at that index.  
In case the input is out of the range, output "**Invalid day**".  
  
**Sample Input:**  
2  
  
**Sample Output:**  
Tuesday  

Check that the input is a valid index first, before accessing the corresponding element of the array.


```Kotlin
fun main(args: Array<String>) {
	val names = arrayOf("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday")
	var day = readLine()!!.toInt()

	if(day>=0 && day <7){
		println(names[day])
	}else {
		println("Invalid day")
	}
}
```


## For Loops

# Vertical Text

You need to make a string as input and output it vertically, each letter on a new line.  
  
**Sample Input:**  
hello  
  
**Sample Output:**  
h  
e  
l  
l  
o  

Use a **for** loop to iterate over the letters of the string.					  

```Kotlin
fun main(args: Array<String>) {
	var vertical = readLine()!!.toString()
	for (v in vertical) {
		println(v)
	}
}					  
```

# Ranges

### Sum in Range
  
You need to make an app that calculates the sum of all numbers in a given range.  
Take two numbers as input, defining the start and end of the range. Then, calculate the sum of all numbers in that range and output the result.  
  
**Sample Input:**  
5  
9  
  
**Sample Output:**  
35

```Kotlin
fun main(args: Array<String>) {
	val num1 = readLine()!!.toInt()
	val num2 = readLine()!!.toInt()
	var sum = 0

	for (nums in num1..num2){
		sum +=nums
	}
	println(sum)
}
```

# Parking Fee

You are making a car parking software that needs to calculate and output the amount due based on the number of hours the car was parked.  
The fee is calculated based on the following price structure:  
- the first 5 hours are billed at $1 per hour.  
- after that, each hour is billed at $0.5 per hour.  
- for each 24 hours, there is a flat fee of $15.  
  
This means, that, for example, if a car parked for 26 hours, the bill should be 15+(2*0.5) = **16.0**, because it was parked for 24 hours plus 2 additional hours.  
  
**Sample Input:**  
8  
  
**Sample Output:**  
6.5  
  
**Explanation**: The first 5 hours are billed at $1/hour, which results in $5. After that, the next 3 hours are billed at $0.5/hour = $1.5.  
So, the total would be $5+$1.5 = $**6.5**

The output should be a **Double**, even if the amount is a round number.

```Kotlin 
>fun main(args: Array<String>) {
`var hours = readLine()!!.toInt()
`var total: Double = 0.0
`
`if(hours <= 5) {
`total = hours * 1.0
`} else if(hours > 5 && hours < 24) {
`hours = hours -5
`total = 5 + (hours * 0.5)
`} else if(hours >= 24) {
`total = (15.0*(hours/24)) + ((hours%24) * 0.5)
`}
`println(total)
`}
```
**or:**
```kotlin
fun main(args: Array<String>) {
    var hours = readLine()!!.toInt()
    var total: Double = 0.0
 total = when {
        hours >= 24 -> (15 * (hours / 24)) + (0.5 * (hours % 24))
        hours > 5 -> 5 + ((hours - 5) * 0.5)
        else -> hours.toDouble()
    }
    println(total)
```


