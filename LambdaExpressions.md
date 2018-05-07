# **Lambda Expressions or Closures**


## **Swift**

In Swift, a lambda function is expressed as a closure.  The purpose of a closure is to allow for contained functionality to be easily transferred and used in your code.  They contain many functions and interactions that are shorten and contained for easy reuse and interpretation.

#### **The 3 Forms**
Closures can take on three forms:

-Global functions are closures that have a name and do not capture any values.

-Nested functions are closures that have a name and can capture values from their enclosing function.

-Closure expressions are unnamed closures written in a lightweight syntax that can capture values from their surrounding context.

#### **Example**

```swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}
var reversedNames = names.sorted(by: backward)
// reversedNames is equal to ["Ewa", "Daniella", "Chris", "Barry", "Alex"]
```

In this example it shows how a closure can be used to change functionality of library function to do a desired task.  Here a backward function is defined as a closure and then sent to swift library sorted function but used as its parameter providing it with additional functionality.  This shows the benefit of closures and how it can extend functionality and allow for easy code reuse and manipulation.


## **Kotlin**

Kotlin like it predecessor, Java, used the term Lambda to define its form of functional programming.  The first key to Kotlin lambdas is to understand what a higher order function is.

#### **Higher order function**

Kotlin facilitates its lambda expressions through the use of higher order functions.  A higher order function is simiply a function that can take another function as its parameter.  This feature allows for the concept of a lambda expression to emerge.

#### **Lambda Expressions**

The definition of a lambda function is a function that takes in a function that is never declared but instead immediately sent to the calling function for direct use.

```kotlin
//Here is an example of a function that will compare two strings written as a traditional function

fun compare(a: String, b: String): Boolean = a.length < b.length

//Now we will convert it to a lambda using a higher order function

max(strings, { a, b -> a.length < b.length })

```

This example shows the benefit of a lambda reducing the length of your code will still implementing the same functionality and having the same readability.
