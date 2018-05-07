# **Multithreading**

## **Swift**

Swift contains thread like abilities similar to many other languages.  The goal for Apple in their development of Swift was to make sure that applications can have multiple paths of execution that can run at the same time as the main thread.  The benefits of multithreading is it can improve an applications perceived response time and can also can benefit the application's real time performance.

#### **Multitasking and Concurrency**

Multitasking and concurrency can be essential to a well run application but it comes with its positives and negatives. Having multitasking occurring in your application allows for more functionality to be available to the user at a touch of a button.  The downside of implementing this feature is synchronization has be to exact and perfect or a concurrent program will not function correctly at all.  The way Swift implements these features is through the old objective-C way.

Link for implementation: https://developer.apple.com/documentation/foundation/thread#symbols

Also it can be done through concurrent programing with GCD.  Apple does a tutorial to show its usage and power here -> https://www.youtube.com/watch?v=zfCZTnEZ6Dw


## **Kotlin**

In Kotlin the term for multithreading is __coroutines__.  The difference of a coroutine from your standard thread is it allows provides a way to avoid block a thread and instead implements a suspension feature.

#### **Suspension**

The idea behind implementing a suspension is when you have to block a thread it usually expensive and can cause a lot of stress in a high load operation.  When using a suspension the work load is almost free and does not stress the system.  They are easy to implement and their functionality can be user controlled by libraries. 

##### **Example**

```kotlin
fun main(args: Array<String>) {
    doSomething() // ERROR: Suspending function called from a non-coroutine context 
    
    async { 
        ...
        computations.forEach { // `forEach` is an inline function, the lambda is inlined
            it.await() // OK
        }
            
        thread { // `thread` is not an inline function, so the lambda is not inlined
            doSomething() // ERROR
        }
    }
}

/// how a suspension function is declared
suspend fun doSomething(foo: Foo): Bar {
    ...
}
```

Many api's implement suspension of coroutines for Kotlin allowing for easy implementation and all that is required is a slight tweaking to get the functionality you want out of the coroutine.

