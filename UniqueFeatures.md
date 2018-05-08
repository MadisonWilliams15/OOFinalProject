# **Unique Features of the Language**

### **Does the language have any particularly unique features?**
* **Swift**

[**Closures unified with function pointers**](https://github.com/MadisonWilliams15/OOFinalProject/blob/master/LambdaExpressions.md#swift)

[**Null safety**](Null&nilReferences.md)

[**Optionals**](https://github.com/bradworthen/OOFinalProject/blob/master/Null%20%26%20nil%20References.md#optional-chaining)

[**Functional programming patterns.**](FunctionalProgramming.md)

**Generics**

Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner. 
```swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}
```
The above function can be used with any type because it uses generics.
```swift 
var someInt = 3
var anotherInt = 107
swapTwoValues(&someInt, &anotherInt)
// someInt is now 107, and anotherInt is now 3
 
var someString = "hello"
var anotherString = "world"
swapTwoValues(&someString, &anotherString)
// someString is now "world", and anotherString is now "hello"
```


**Multiple Return Values**

In Swift, we can use tuples to return more than one element from a function. We use the tuple type as return type, and return a tuple:
```swift
func okStatus() -> (code: Int, name: String, hasBody: Bool) {
    return (200, "OK", true)
}
let status = okStatus()
println(status.name) // Prints "OK"
```

* **Kotlin** 

[**Null safety**](Null&nilReferences.md)

[**Functional Programming**](FunctionalProgramming.md)

**Inter-operable with java**

Kotlin is designed with Java Interoperability in mind. Existing Java code can be called from Kotlin in a natural way, and Kotlin code can be used from Java rather smoothly as well. In this section we describe some details about calling Java code from Kotlin.

Pretty much all Java code can be used without any issues:
```kotlin
import java.util.*

fun demo(source: List<Int>) {
    val list = ArrayList<Int>()
    // 'for'-loops work for Java collections:
    for (item in source) {
        list.add(item)
    }
    // Operator conventions work as well:
    for (i in 0..source.size - 1) {
        list[i] = source[i] // get and set are called
    }
}
```

**High order function**

If your function accepts function as a parameter or returns function as a result than it’s called high order function. 
```kotlin
fun addValue(operation:(Int,Int) -> Int):Int {
    return operation(10,20)
}
addValue{num1,num2 -> num1 * num2} //This will print 200
addValue{num1,num2 -> num1 - num2} //This will print -10
```

**Defaulted parameters**

In Java, you often have to duplicate code in order to define different variants of a method or a constructor:
```java
public class OperatorInfoInJava {

    private final String uuid;
    private final String name;
    private final Boolean hasAccess;
    private final Boolean isAdmin;
    private final String notes;

    public OperatorInfoInJava(String uuid, String name, Boolean hasAccess, 
                              Boolean isAdmin, String notes) {
        this.uuid = uuid;
        this.name = name;
        this.hasAccess = hasAccess;
        this.isAdmin = isAdmin;
        this.notes = notes;
    }

    public OperatorInfoInJava(String uuid, String name) {
        this(uuid, name, true, false, "");
    }

    public OperatorInfoInJava(String name, Boolean hasAccess) {
        this(UUID.randomUUID().toString(), name, hasAccess, false, "");
    }
```
You can simply remove all of this when you switch to Kotlin by using default arguments.
```kotlin
class OperatorInfoInKotlin(val uuid: String = UUID.randomUUID().toString(),
                           val name: String,
                           val hasAccess: Boolean = true,
                           val isAdmin: Boolean = false,
                           val notes: String = "") {}
```
