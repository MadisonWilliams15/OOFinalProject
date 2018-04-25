# **Errors and exception handling**
* **Swift:**

In Swift, errors are represented by values of types that conform to the Error protocol. This empty protocol indicates that a type can be used for error handling.

Swift enumerations are particularly well suited to modeling a group of related error conditions, with associated values allowing for additional information about the nature of an error to be communicated. For example, here’s how you might represent the error conditions of operating a vending machine inside a game:

```swift
enum VendingMachineError: Error {
    case invalidSelection
    case insufficientFunds(coinsNeeded: Int)
    case outOfStock
}
```

Throwing an error lets you indicate that something unexpected happened and the normal flow of execution can’t continue. You use a throw statement to throw an error. For example, the following code throws an error to indicate that five additional coins are needed by the vending machine:

```swift
throw VendingMachineError.insufficientFunds(coinsNeeded: 5)
```
Handling Errors Using Do-Catch:

You use a do-catch statement to handle errors by running a block of code. If an error is thrown by the code in the do clause, it is matched against the catch clauses to determine which one of them can handle the error.

Here is the general form of a do-catch statement:
```swift
do {
    try expression
    statements
} catch pattern 1 {
    statements
} catch pattern 2 where condition {
    statements
} catch {
    statements
}
```

* **Kotlin:**

All exception classes in Kotlin are descendants of the class Throwable. Every exception has a message, stack trace and an optional cause.

To throw an exception object, use the throw-expression:
```kotlin
throw MyException("Hi There!")
```

To catch an exception, use the try-expression:
```kotlin
try {
    // some code
}
catch (e: SomeException) {
    // handler
}
finally {
    // optional finally block
}
```
There may be zero or more catch blocks. 

try is an expression, i.e. it may have a return value and a try catch can be written as:

```kotlin
val a: Int? = try { parseInt(input) } catch (e: NumberFormatException) { null }
```
