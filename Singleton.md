# **Singleton**

## **Swift**

Apple decided to inherit a lot of the concepts of how to singleton was designed in objective-c and implement it into Swift.  Their goal in the singleton was to provide a global access shared instance of an object.  With this it allows for the programmer to a create a unified access point for resources within their code.

#### **Implementation**

```swift
class Singleton {
    static let sharedInstance = Singleton()
}
///this is guaranteed to be lazily intiliazed once
```

In swift you can also manually do a lazy singleton to lessen the load since the idea behind lazy properties is they are not calculated until the first time they are used.  The way you do that with a singleton is like this.

```swift
class Singleton {
    static lazy let sharedInstance = Singleton()
    private init() {}
}
```

#### **Thread Safety**

Even though Swift makes singletons seem incredibly easy they leave a lot of information out on how to correctly write one. They do talk about thread safety and the way you implement a thread safe singleton is to wrap you code in a __dispatch_once__ block to ensure it while only execute once in its lifetime.

```swift
//Thread safe singelton
+ (instancetype)sharedInstance {
    static id _sharedInstance = nil;
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        _sharedInstance = [[self alloc] init];
    });
 
    return _sharedInstance;
}
```

To find out more on how to write singletons this [blog post](https://krakendev.io/blog/the-right-way-to-write-a-singleton) covers many ways on the right and wrong ways to implement singletons.


## **Kotlin**

Kotlin does their form of a singleton in versions after Scala in a way called an __object declaration__.  With this they are very easy and are thread safe.  With object declaration it is implied that it is a lazy property and won't be calculated until execution.

```kotlin
object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {
        // ...
    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```

The only downside to this method is that object declaration cannot be local but they can be nested.
