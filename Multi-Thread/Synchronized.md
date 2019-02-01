# Synchronized

### Overview

Synchronized blocks in Java are marked with the synchronized keyword. A synchronized block in Java is synchronized on some object. All synchronized blocks synchronized on the same object can only have one thread executing inside them at the same time. All other threads attempting to enter the synchronized block are blocked until the thread inside the synchronized block exits the block. 

 The synchronized keyword can be used to mark four different types of blocks:

   - Instance methods
   - Static methods
   - Code blocks inside instance methods
   - Code blocks inside static methods

#### Instance methods

```java
public synchronized void add(int value){
      this.count += value;
  }
```
- A synchronized instance method in Java is synchronized on the instance (object) owning the method.
- Only one thread can execute inside a synchronized instance method
- If more than one instance exist, then one thread at a time can execute inside a synchronized instance method per instance. One thread per instance.

####  Static Methods

```java
public static synchronized void add(int value){
      count += value;
  }

```

- Synchronized static methods are synchronized on the class object of the class the synchronized static method belongs to.
- Since only one class object exists in the Java VM per class, only one thread can execute inside a static synchronized method in the same class. 

### Synchronized Blocks in Instance Methods
TBD
### Synchronized Blocks in Static Methods
TBD