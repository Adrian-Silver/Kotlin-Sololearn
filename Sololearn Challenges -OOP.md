# Buttons

You are making a user interface that needs to have buttons in a form.  
You decide to make a **Button** class, with **width** and **height** properties .  
Complete the given program so that the code in **main** works as expected.

Both **width** and **height** are Integers.

```Kotlin
// your code goes here
class Button {
	var width: Int = 0
	var height: Int = 0
}

fun main(args: Array<String>) {
	val b1 = Button()
	b1.width = readLine()!!.toInt()
	b1.height = readLine()!!.toInt()
	println(b1.width+b1.height)
}
```

---
## Buttons Constructor

You need to modify the **Button** class and add a default constructor to it, which initializes the **width** and **height** properties.  
Add the constructor so that the given code in main works as expected.

The given code takes the values from user input and passes them to the object's constructor.

```Kotlin
class Button {
	var width: Int = 0
	var height:Int = 0

	constructor(w: Int, h: Int){
		width = w
		height = h
	}
}

fun main(args: Array<String>) {
	val b1 = Button(readLine()!!.toInt(), readLine()!!.toInt())
	println(b1.width*b1.height)
}
```


```Kotlin
class Button (var width: Int, var height:Int) {

}

fun main(args: Array<String>) {
	val b1 = Button(readLine()!!.toInt(), readLine()!!.toInt())
	println(b1.width*b1.height)
}
```

---

## Button Setter

You continue working on the **Button** class.  
You need to have a minimum **height** for the Buttons - it cannot have a value below 50.  
You decide to create a setter for the **height** property so that if the provided value is less than 50, it is set as 50.

Create a valid setter for the **height** property so that the code works as expected.

```Kotlin
class Button {
	var width: Int = 0
	var height: Int = 0
	// your code goes here
	get() = field

	set(value) {
		if(value < 50) {
			field = 50
		} else{
			field = value
		}
	}
}

fun main(args: Array<String>) {
	val b1 = Button()
	b1.height = readLine()!!.toInt()
	b1.width = readLine()!!.toInt()

	println(b1.width+b1.height)
}
```

---

## Button Tap

Let's add some behavior to our **Button** class!  
You need to define a **tap**() function for the Button class. The function should output the message "**button was tapped**", where "button" is the **name** of the object. This means that you also need to add a **name** property to the Button class.  
The code in main takes the name of the Button as input, assigns it to the property, and calls the tap() function.  
  
**Sample Input:**  
Send  
  
**Sample Output:**  
Send was tapped  

Note that the constructor should include only the **width** and **height** properties.

```Kotlin
class Button(var width: Int, var height: Int) {
	//your code goes here
	var name: String = "Button"

	fun tap() {
		println(name + " was tapped")
	}
}

fun main(args: Array<String>) {
	val b1 = Button(200, 50)
	b1.name = readLine()!!

	b1.tap()
}
```

---

## Button as a Component

Your **Button** class looks pretty good!  
However, you also need to have images on the form.  
As the images have the same **width** and **height** properties, you decide to create a base class called **Component** and inherit the **Button** and **Image** classes from it.  
The Button class should have its own **name** property and **tap**() function, while the Image class should have a **draw**() function, outputting its height and width in the format: **width****height**. So for an image with width of 100 and height of 150, the output should be **100x150**.  
  
Complete the given code to define the **Image** class and inherit the **Button** and **Image** classes from the **Component** class.

Note, that **width** and **height** are Integers, so in order to concatenate them to a string you need to convert them using the **toString**() function: **width.toString()**

```Kotlin
open class Component(var width: Int, var height: Int) {
  
}
  
class Button(width: Int, height: Int): Component(width,height){
  
    var name: String = "Button"
    
    fun tap() {
        println(name + " was tapped")
    }
}

class Image(width:Int,height:Int): Component(width,height){
  
	var name:String = "Image"
  
	fun draw(){
		var x = width.toString()
		var y = height.toString()
		println(x+'x'+ y)
	}
  
fun main(args: Array<String>) {

    val b1 = Button(200, 50)  
    b1.tap()
    val img = Image(300, 500)
    img.draw()

}
```

## Visibility Modifiers -> 
## Restricting Access

Someone modified your code to restrict public access to the **width** and **height** properties. However, there are mistakes in the code and it does not run.  
Fix the given code, so that **width** and **height** are accessible only in the derived classes, and the class functions are accessible from **main**.

 ->It is common practice to restrict access to internal properties and allow users to get/set their values using class functions or getters/setters.

```Kotlin
open class Component(width: Int, height: Int) {
	protected var width = width
	protected var height = height
}

class Button(width: Int, height: Int): Component(width, height) {
	private var name: String = "Button"

	public fun tap() {
		println(name + " was tapped")
	}
}

class Image(width: Int, height: Int): Component(width, height) {
	public fun draw() {
		println(width.toString()+"x"+height.toString())
	}
}

fun main(args: Array<String>) {
	val b1 = Button(200, 50)
	b1.tap()

	val img = Image(300, 500)
	img.draw()
}
```

---
# Abstraction

You decide to make the **Component** class **abstract**, since you are not going to create objects of that type.  
You also add a **show**() function to it that the derived classes need to override.  
For a **Button**, the **show**() function should output: "Showing a Button", while for an **Image** it should output: "Showing an Image".

Implement the required **show**() function to generate the expected output.

```Kotlin
abstract class Component(width: Int, height: Int) {

	protected var width = width
	protected var height = height
	
	abstract fun show()
}

class Button(width: Int, height: Int): Component(width, height) {

	private var name: String = "Button"

	fun tap() {
		println(name + " was tapped")
	}

	override fun show() {
		println("Showing a Button")
	}
}

class Image(width: Int, height: Int): Component(width, height) {

	fun draw() {
		println(width.toString()+"x"+height.toString())
	}

	override fun show() {
		println("Showing an Image")
	}
}

fun main(args: Array<String>) {

	val b1 = Button(200, 50)
	b1.tap()
	b1.show()

	val img = Image(300, 500)
	img.draw()
	img.show()
}
```

## Module Quiz
```Kotlin
class Num(value: Int) {
        var v = value + 2
        set(value) {
            field = value + v
        }
    }
fun main() {
    val x = Num(3)
    x.v = 7
    println(x.v)
       
}
```

**Output:**
12

---
# Music Player

You are building a Music Player app.  
You need to implement the MusicPlayer class, which should hold the track names as Strings in an array. The array is already defined in the given code.  
The player should support the following functions:  
**add**: add the given argument track to the **tracks** array.  
**show**: output all track names in the player on separate lines.  
**play**: start playing the first track by outputting "Playing name" where name is the first track name.  
  
You can add a new item to an array using +=, for example: **tracks += track**

The code in **main** takes track names from user input and calls the player functions. Do not modify the code in main.

```Kotlin
class MusicPlayer {
	private var songs: Array<String> = arrayOf()
	//your code goes here
	fun add(song: String): Array<String>{
		// var song: Array<String> = arrayOf
		songs += song
		
		return songs
	}

	fun show(){
	
		for(song in songs) {
			println(song)
		}
	}

	fun play() {
		println("Playing " + songs[0])
	}
}

fun main(args: Array<String>) {
	val m = MusicPlayer()

	while(true) {
		var input = readLine()!!
		if(input == "stop") {
			break
		}
		m.add(input)
	}
	
	m.show()
	m.play()
}
```