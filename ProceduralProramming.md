# Procedural Programming
Procedural Programming takes on applications by solving problems from the top of the code down to the bottom.

A program following this programming technique breaks a problem down into smaller sub-problems or sub-procedures. These sub-procedures are continually broken down in the process called functional decomposition until the sub-procedure is simple enough to be solved.

The issue that is obvious in Procedural Programming is that if an edit is needed to the program, the developer must edit every line of code that corresponds to the original change in the code. An example would be if at the beginning of a program a variable was set to equal the value of 1. If other sub-procedures of the program rely on that variable equaling 1 to function properly they will also need to be edited. As more and more changes may be needed to the code, it becomes increasingly difficult to locate and edit all related elements in the program.

## Swift
Swift does not support procedural programming.

## Kotlin
While Kotlin is a pure OOP language, it also supports procedural programming. With Kotlin, functions and variables can be defined without placing them explicitly in classes, unlike Java.

```Kotlin
val rectangle = mutableMapOf("Width" to 10, "Height" to 10, "Color" to "Red")
 
fun calcArea(shape : Map<String, Any>) : Int {
    return shape["Height"] as Int * shape["Width"] as Int
}
 
fun toString(shape : Map<String, Any>) : String {
    return "Width = ${shape["Width"]}, Height = ${shape["Height"]}, Color = ${shape["Color"]}, Area = ${calcArea(shape)}"
}
```
