# Java notes

Head First Java Book notes

## Chapter 8: Serious Polymorphism

* Interfaces means 100% abstract classes. Abstract classes are classes which cannot be instantiated.
* Abstract methods can have no body. They must be overridden.
* An abstract method must always be inside an abstract class.
* abstract methods are there to make the methods a must for the classes that extend from this parent abstract class. This is to define a protocol for the group of sub-classes (sub-types)
* The abstract methods must be implemented as they don't have a body.
* THE COMPILER DECIDES WHETHER YOU CAN CALL A METHOD BASED ON THE TYPE OF THE **REFERENCE** NOT THE ACTUAL OBJECT TYPE.
* AGAIN, The compiler checks the type of the reference - not the type of the Object to see if you can call a method using that reference.
* Let us consider the reference variable to be a remote control. When the type of the reference is more down the inheritance tree, the more buttons it may have. For example, A Dog type (implicitly extends Object) reference variable has more buttons than a reference variable pointed to the Object type. A reference of type Dog has both the Dog-specific methods and the methods of the Object class, while a reference of Object type has only the methods of its own class (Object). (Pg. 215: Nice Diagram to understand)
* We can cast a reference back to its original type from Object using Casting.
* ALL THAT MATTERS IS THE TYPE OF THE REFERENCE. TO USE DOG-SPECIFIC METHODS CAST THE REFERENCE TO DOD TYPE AND THEN USE IT. All the way through this process, the original object on the **heap** is of the original type (Dog). The casting can be done when you are really sure of the type of the object on the heap. If not we can use the `instanceof` operator to check. Like,

```java
if (o instanceof Dog) {
    Dog d = (Dog) 0;
}
```

* Single point to take away: JAVA CARES A LOT ABOUT THE TYPE OF THE REFERENCE. You can call a method on an object only if the class of the reference variable has that method.  
* When you call a method on a reference variable, the compiler always looks at the reference type and checks that class to guarantee, the class has the method and that method take the argument you are passing and returns the type what you are expecting. The compiler does it, so that it doesn't blow up on your face, on runtime.
* Just remember that the compiler checks the class of the reference variable, not the class of the actual object at the other end of the reference variable.
* There is no "Multiple Inheritance in Java". There is `interface` for that matter. The multiple inheritance problem (bringing confusion if a class inherits from two classes and both the classes have different definition for same method, The Deadly Diamond of Death). The solution for this problem is using `interface` and this solves it by making all the methods abstract. So that the first concrete class must implement all the inherited methods and so that at runtime, the JVM wont be confused on which method to call.
* To define an interface use the keyword like in class, 

```java
public interface Pet {
    pass;
}
```

* To implement an interface use the `implements` keyword.

```java
public class Dog extends Canine implements Pet {
    pass;
}
```

* We can also extend a class while implementing an interface.