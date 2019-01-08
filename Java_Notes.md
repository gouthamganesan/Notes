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
* Interface methods are implicitly public and abstract. Though we can maintain optionally type the keywords explicitly, it is not advised to do so.
* When we use a class as a polymorphic type, the object that can hold must be of the type of its subclasses in the inheritance tree. But when we use an interface as the polymorphic type, the object can be from anywhere in the inheritance tree. The only requirement is that the class of the object must implement the interface.
* We can implement multiple interfaces on a same class like,

```java
public class Dog extends Animal implements Pet, Savealbe, Paintable {
    pass;
}
```

* Java weighs on family values. There can be only one Parent to a class. They define who you are. But we can implement multiple interfaces. Those are the roles you can play.
* How to figure out what you want?
  * **A Class**: It doesn't extend anything (other than Object, that too implicitly).
  * **A SubClass** (Extend a class) : Only when you need a more specific version of a class or when there is a need to override or add new behaviours.
  * **Abstract Class**: Use an abstract class,
    1. When there is a need to create a *template* for a group of subclasses.
    2. When you have some implementation code that all the subclasses use.
    3. When you've to make sure that no one can instantiate the type.
  * **Interface**: Use an interface when you want to define a *role* that other classes can play, regardless of where those classes are in the inheritance tree.

* The keyword `super` is used to call the method from the superclass of the inherited class. We can put the part of the implementation code, which is generic enough for all the sub-classes and then we can call the method from the superclass and do the thing and then continue the stuff which are specific to the derived class in it. In simple words, to call the method from the super class, use the keyword `super`. It allows you to call the superclass version of the *overridden* method, from **within** in the subclass.
* The `super` keyword is a reference to the super class portion of an object.
