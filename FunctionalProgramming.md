# **Functional Programming**

### **Does the language support functional programming?**
* **Swift:**

Swift supports functional programming. Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.
In terms of Swift, functional programming means using lets instead of vars when dealing with data. This has its benefits, mainly that functional code is less prone to bugs and easier to understand than imperative code. Imperative programming is the opposite of functional programming — it’s a paradigm that uses statements that change a program’s state.
A key practice in functional programming is breaking code down into smaller, pure functions, which can be used several times throughout the project. Pure functions are functions that have no side effects on the program as a whole, meaning they exist solely to help other functions which do participate in the program.

A program that takes an array of numbers and creates an array of only the numbers taht are even can be written a few ways in swift. 

Imperative Approach:
```swift
let numbers = [1, 2, 3, 4, 5]
var evenNumbers = [Int]()
for i in 0..<numbers.count {
    let number = numbers[i]
    if number % 2 == 0 {
        evenNumbers.append(number)
    }
}
```
Functional Approach:
```swift
let evenNumbers = [1, 2, 3, 4, 5].filter { (number) -> Bool in
    if number % 2 == 0 {
        return true
    } else {
        return false
    }
}
```

OR

```swift
let evenNumbers = [1, 2, 3, 4, 5].filter { $0 % 2 == 0 }
```

* **Kotlin:**

Kotlin also supports functional programming. A combination of lambda expression and the Kotlin library makes our life easier when working with collections. For example a program that takes an array and keeps only the positive numbers can be written as:
```kotlin
val numbers = arrayListOf(10 ,5 , -9, 9, 11, 5, -6)
val nonNegative = numbers.filter { it >= 0}

println(nonNegative) // [10, 5, 9, 11, 5]
```
