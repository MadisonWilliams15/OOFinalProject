# Memory Management

## **Kotlin**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Kotlin uses the same memory management that Java uses or any other JVM like language uses.  With this it comes with the same garbage collection system that Java uses as well.  This provides a semi safe runtime environment that should usually be without memory leaks.  Although the garbage collection system catches most unused references memory leaks can still occur.  The best way to prevent this in Kotlin is to make sure you still set references to null once you are done using them.  The reason the Kotlin memory management system almost identically reflects Java's memory management is to allow for easy code transfer between languages since Kotlin is the successor to Java.

#### **Kotlin/Native**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;In Kotlin/Native the newer platform developed by jet brains to allow Kotlin to run on many modern applications.  In this platform automatic reference counting is planned to be implemented to address the Null pointer issue that many java applications can run into.  With this it will remove the garbage collector similar to the JVM and will handle memory management in a similar way as Swift.

  
## **Swift**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Swift handles memory management through a proccess called ARC or Automatic Reference Counting.  This process allows for easy memory management for the programmer because Swift will do deallocates and allocates for you.  Swift will not deallocate an object unless it leaves the scope that it is contained in.

**For Example:**
```swift
let test = Test(number: 1)   // Will not be deallocated until main program is over

vs

while(counter!= 2){
  let test = Test(number: 1)  // Will be deallocated after the while loop is over
}
```
#### **The Process**
Objects in swift go through a 5 stage process after allocation.  The 5 steps are:

&nbsp;&nbsp; -Allocation (memory taken from stack or heap)

&nbsp;&nbsp; -Initialization (init code runs)

&nbsp;&nbsp; -Usage (the object is used)

&nbsp;&nbsp; -Deinitialization (deinit code runs)

&nbsp;&nbsp; -Deallocation (memory returned to stack or heap)

#### **The good**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The advantages of the ARC cycle is the developer does not have to worry about memory leaks because as soon as something leaves its scope the reference count will be updated for the current scope of the program.  With this as soon as the reference counter hits 0 Swift will automatically deinitalize the object and return the memory back to the stack or heap.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Swift’s automatic reference counting allows for easy garbage collection because as soon as the reference count hits 0 it will be marked as garbage and the memory will be returned.

#### **The Bad**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The ARC cycle has issues when multithreading occurs and objects are shared across many threads. Deinitalizing objects from multiple threads introduces a whole lot of complexity since the references are split across many threads and the ARC cycle has trouble tracking and keeping up with the references as some are dereferenced at the same time.

