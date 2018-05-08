# Inheritance and Extension

## Swift
A class can inherit methods, properties, and other characteristics from another class. When one class inherits from another, the inheriting class is known as a subclass, and the class it inherits from is known as its superclass. Inheritance is a fundamental behavior that differentiates classes from other types in Swift.

Classes in Swift can call and access methods, properties, and subscripts belonging to their superclass and can provide their own overriding versions of those methods, properties, and subscripts to refine or modify their behavior. Swift helps to ensure your overrides are correct by checking that the override definition has a matching superclass definition.

Classes can also add property observers to inherited properties in order to be notified when the value of a property changes. Property observers can be added to any property, regardless of whether it was originally defined as a stored or computed property.

Subclassing is the act of basing a new class on an existing class. The subclass inherits characteristics from the existing class, which you can then refine. You can also add new characteristics to the subclass.

To indicate that a subclass has a superclass, write the subclass name before the superclass name, separated by a colon:
```Swift
class SomeSubclass: SomeSuperclass {
    // subclass definition goes here
}
```
#### Overriding
A subclass can provide its own custom implementation of an instance method, type method, instance property, type property, or subscript that it would otherwise inherit from a superclass. This is known as overriding.

To override a characteristic that would otherwise be inherited, you prefix your overriding definition with the override keyword. Doing so clarifies that you intend to provide an override and have not provided a matching definition by mistake. Overriding by accident can cause unexpected behavior, and any overrides without the override keyword are diagnosed as an error when your code is compiled.

The override keyword also prompts the Swift compiler to check that your overriding class’s superclass (or one of its parents) has a declaration that matches the one you provided for the override. This check ensures that your overriding definition is correct.

##### Accessing Superclass Methods, Properties, and Subscripts
When you provide a method, property, or subscript override for a subclass, it is sometimes useful to use the existing superclass implementation as part of your override. For example, you can refine the behavior of that existing implementation, or store a modified value in an existing inherited variable.

Where this is appropriate, you access the superclass version of a method, property, or subscript by using the super prefix:

* An overridden method named someMethod() can call the superclass version of someMethod() by calling super.someMethod() within the overriding method implementation.

* An overridden property called someProperty can access the superclass version of someProperty as super.someProperty within the overriding getter or setter implementation.

* An overridden subscript for someIndex can access the superclass version of the same subscript as super[someIndex] from within the overriding subscript implementation.

##### Overriding Methods
You can override an inherited instance or type method to provide a tailored or alternative implementation of the method within your subclass.

The following example defines a new subclass of Vehicle called Train, which overrides the makeNoise() method that Train inherits from Vehicle:
```Swift
class Train: Vehicle {
    override func makeNoise() {
        print("Choo Choo")
    }
}
```
If you create a new instance of Train and call its makeNoise() method, you can see that the Train subclass version of the method is called:
```Swift
let train = Train()
train.makeNoise()
// Prints "Choo Choo"
```
##### Overriding Properties
You can override an inherited instance or type property to provide your own custom getter and setter for that property, or to add property observers to enable the overriding property to observe when the underlying property value changes.

##### Overriding Property Getters and Setters
You can provide a custom getter (and setter, if appropriate) to override any inherited property, regardless of whether the inherited property is implemented as a stored or computed property at source. The stored or computed nature of an inherited property is not known by a subclass—it only knows that the inherited property has a certain name and type. You must always state both the name and the type of the property you are overriding, to enable the compiler to check that your override matches a superclass property with the same name and type.

You can present an inherited read-only property as a read-write property by providing both a getter and a setter in your subclass property override. You cannot, however, present an inherited read-write property as a read-only property.

**NOTE**
If you provide a setter as part of a property override, you must also provide a getter for that override. If you don’t want to modify the inherited property’s value within the overriding getter, you can simply pass through the inherited value by returning super.someProperty from the getter, where someProperty is the name of the property you are overriding.
*****

The following example defines a new class called Car, which is a subclass of Vehicle. The Car class introduces a new stored property called gear, with a default integer value of 1. The Car class also overrides the description property it inherits from Vehicle, to provide a custom description that includes the current gear:
```Swift
class Car: Vehicle {
    var gear = 1
    override var description: String {
        return super.description + " in gear \(gear)"
    }
}
```
The override of the description property starts by calling super.description, which returns the Vehicle class’s description property. The Car class’s version of description then adds some extra text onto the end of this description to provide information about the current gear.

If you create an instance of the Car class and set its gear and currentSpeed properties, you can see that its description property returns the tailored description defined within the Car class:
```Swift
let car = Car()
car.currentSpeed = 25.0
car.gear = 3
print("Car: \(car.description)")
// Car: traveling at 25.0 miles per hour in gear 3
```
## Kotlin
All classes in Kotlin have a common superclass Any, that is the default superclass for a class with no supertypes declared:

```Kotlin
class Example // Implicitly inherits from Any
```
Code in a derived class can call its superclass functions and property accessors implementations using the super keyword:

```Kotlin
open class Foo {
    open fun f() { println("Foo.f()") }
    open val x: Int get() = 1
}

class Bar : Foo() {
    override fun f() { 
        super.f()
        println("Bar.f()") 
    }
    
    override val x: Int get() = super.x + 1
}
```
If the derived class has a primary constructor, the base class can (and must) be initialized right there, using the parameters of the primary constructor.

If the class has no primary constructor, then each secondary constructor has to initialize the base type using the super keyword, or to delegate to another constructor which does that. Note that in this case different secondary constructors can call different constructors of the base type:

```Kotlin
class MyView : View {
    constructor(ctx: Context) : super(ctx)

    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
```

#### Overriding Methods
As we mentioned before, we stick to making things explicit in Kotlin. And unlike Java, Kotlin requires explicit annotations for overridable members (we call them open) and for overrides:
```Kotlin
open class Base {
    open fun v() {}
    fun nv() {}
}
class Derived() : Base() {
    override fun v() {}
}
```

The override annotation is required for Derived.v(). If it were missing, the compiler would complain. If there is no open annotation on a function, like Base.nv(), declaring a method with the same signature in a subclass is illegal, either with override or without it. In a final class (e.g. a class with no open annotation), open members are prohibited.

A member marked override is itself open, i.e. it may be overridden in subclasses. If you want to prohibit re-overriding, use final:
```Kotlin
open class AnotherDerived() : Base() {
    final override fun v() {}
}
```

#### Overriding Properties
Overriding properties works in a similar way to overriding methods; properties declared on a superclass that are then redeclared on a derived class must be prefaced with override, and they must have a compatible type. Each declared property can be overridden by a property with an initializer or by a property with a getter method.
```Kotlin
open class Foo {
    open val x: Int get() { ... }
}

class Bar1 : Foo() {
    override val x: Int = ...
}
```

You can also override a val property with a var property, but not vice versa. This is allowed because a val property essentially declares a getter method, and overriding it as a var additionally declares a setter method in the derived class.

Note that you can use the override keyword as part of the property declaration in a primary constructor.
```Kotlin
interface Foo {
    val count: Int
}

class Bar1(override val count: Int) : Foo

class Bar2 : Foo {
    override var count: Int = 0
}
```
#### Calling the superclass implementation
Code in a derived class can call its superclass functions and property accessors implementations using the super keyword:
```Kotlin
open class Foo {
    open fun f() { println("Foo.f()") }
    open val x: Int get() = 1
}

class Bar : Foo() {
    override fun f() { 
        super.f()
        println("Bar.f()") 
    }
    
    override val x: Int get() = super.x + 1
}
```
