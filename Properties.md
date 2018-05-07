# **Properties**

## **Swift**

#### **Computed vs Stored**

In Swift properties are divided into two categories, stored properties and computed properties.
In general, a property is defined as a value that associates with a particular class, structure, or enumeration.
Stored properties store constant and variable values to a defined instance where as a computer property will calculate the value.

#### **Stored Properties**

Stored properties are either a constant or a variable that is stored as part of an instance the two ways to do that are by the var and let keyword.

```swift
var example1: int //stored as variable
let example2: int //stored as constant
```

These properties function just like a normal constant or variable would in any other language holding the value it is assigned to at that instance.

 #### **Computed Properties**
 
 Computed properties are very similar to stored properties except when they are referred to they do not actual store value but instead calculate and provide a getter function and an optional setter function to the property.
  
  ```swift
  struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
                  size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
// Prints "square.origin is now at (10.0, 10.0)"
```
The documentation provided by apple explains how a computed property works extremely well.  As you can see in this example the struct rect has a computed property for its center where it takes in the other information and computes at runtime.  It uses getters and setters to be able to update and change with in an instant and allows for dynamic functionality and applications to be able to react to state and data changes and to not be static or constant.


## **Kotlin**

Properties and Kotlin are differentiated by two keywords var which defines a mutable or can be changed property or with val which defines a read only property.

```kotlin
var name: String =
var score: Int? =
val speed: Double =
```

For val type properties a default getter is constructed on initialization but does not allow for a setter since these properties are read only

```kotlin
val simple: Int? // has type Int, default getter, must be initialized in constructor
val inferredType = 1 // has type Int and a default getter
```

For a default var property a getter and setter are initialized by default but for a var? property they are implied but must be implemented by the programmer.

```kotlin
var allByDefault: Int? // error: explicit initializer required, default getter and setter implied
var initialized = 1 // has type Int, default getter and setter
```

Kotlin does allow for manipulation of the getter and setter functions which allows you to add or remove functionality from the default getter and setter provided by the language.

```koltin
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(value) // parses the string and assigns values to other properties
    }
```

#### **Backing Properties**

Kotlin does allow for a backing property similar to Java so you can manipulate and access public and private properties over many methods.  The way this is implemented is shown below.

```kotlin
private var _table: Map<String, Int>? = null
public val table: Map<String, Int>
    get() {
        if (_table == null) {
            _table = HashMap() // Type parameters are inferred
        }
        return _table ?: throw AssertionError("Set to null by another thread")
    }
```
