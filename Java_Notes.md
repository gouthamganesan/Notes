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
* Let us consider the reference variable to be a remote control. When the type of the reference is more down the inheritance tree, the more buttons it may have. For example, A Dog type (implicitly extends Object) reference variable has more buttons than a reference variable pointed to the Object type. A reference of type Dog has both the Dog-specific methods and the methods of the Object class, while a reference of Object type has only the methods of it's own class (Object). (Pg. 215: Nice Diagram to understand)
* We can cast a reference back to it's original type from Object using Casting.
* ALL THAT MATTERS IS THE TYPE OF THE REFERENCE. TO USE DOG-SPECIFIC METHODS CAST THE REFERENCE TO DOD TYPE AND THEN USE IT. All the way through this process, the original object on the **heap** is of the original type (Dog). The casting can be done when you are really sure of the type of the object on the heap. If not we can use the `instanceof` operator to check. Like,

  ```java
  if (o instanceof Dog) {
      Dog d = (Dog) 0;
  }
  ```

* Single point to take away: JAVA CARES A LOT ABOUT THE TYPE OF THE REFERENCE. You can call a method on an object only if the class of the reference variable has that method.  
* When you call a method on a reference variable, the compiler always looks at the reference type and checks that class to guarantee, the class has the method and that method take the argument you are passing and returns the type what you are expecting. The compiler does it, so that it doesn't blow up on your face, on runtime.
* Just remember that the compiler checks the class of the reference variable, not the class of the actual object at the other end of the reference variable.
* There is no "Multiple Inheritance in Java". There is `interface` for that matter. The multiple inheritance problem (bringing confusion if a class inherit's from two classes and both the classes have different definition for same method, The Deadly Diamond of Death). The solution for this problem is using `interface` and this solves it by making all the methods abstract. So that the first concrete class must implement all the inherited methods and so that at runtime, the JVM won't be confused on which method to call.
* To define an interface use the keyword like in class,

  ```java
  public interface Pet {
      ;
  }
  ```

* To implement an interface use the `implements` keyword.

  ```java
  public class Dog extends Canine implements Pet {
      ;
  }
  ```

* We can also extend a class while implementing an interface.
* Interface methods are implicitly public and abstract. Though we can maintain optionally type the keywords explicitly, it is not advised to do so.
* When we use a class as a polymorphic type, the object that can hold must be of the type of it's subclasses in the inheritance tree. But when we use an interface as the polymorphic type, the object can be from anywhere in the inheritance tree. The only requirement is that the class of the object must implement the interface.
* We can implement multiple interfaces on a same class like,

  ```java
  public class Dog extends Animal implements Pet, Savealbe, Paintable {
      ;
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

## Chapter 9: Life and death of an object

* There are two points to note about memory in Java.
  1. The heap: Where the objects of a class live.
  2. The Stack: Where method invocations and local variables live. (Also known as the garbage collectable heap)
* Local variables are also known as *stack* variable. They are declared inside a method. They are temporary and are alive only as long as they are on the stack. (In other words, they are alive until their method invocation is alive).
* Instance variables are variables which are declared inside a class. These variables can hold different values for different objects. They live inside the object they belong to (on the Heap).
* The method calls makes the method land on the stack and these method calls are stored in stack frames. The stack frame holds information such as the values of the local variables and which line it is executing.
* The method on the top is the current-executing method.
* When the local variable is a reference variable, then the reference alone is stored on the stack. No matter what, the object only lives on the heap.
* For an instance variable the values are stored in the object (to which they belong to) on the heap.
* On declaring the reference variable, only the space for the reference is reserved inside the Object on the heap. The space for the object pointed by the reference is created on the heap, only when it is being initialised. For example,

  ```java
  public class CellPhone {
      private Antenna ant;
  }
  ```

  During this, only the space for the reference variable `ant` is reserved inside   the object which lives on the heap.

  ```java
  public class CellPhone {
      private Antenna ant = new Antenna();
  }
  ```

  Only then, the Antenna object takes up space on the heap and links itself to the `ant` reference variable on the heap inside the `CellPhone` object.

* A constructor got the code to instantiate an object. It looks a lot like a method. but it's not. The only way to call a constructor is to use the keyword `new` followed by the name of the class and a `();`.
* A constructor runs before the object is being assigned to a reference. i.e. the `new Duck();` runs first in the `Duck tony = new Duck();`
* So before the user can use the object (before it gets assigned to a reference), the constructor can make the object ready to use.
* We can write our own constructor, just like a method, but without the return type,

  ```java
  public class Duck {
      public Duck () {
          ;           // This is the java equivalent of pass statement in python. An empty statement. It does nothing.
      }
  }
  ```

* A constructor lets you jump into the middle of the object creation - into the middle of `new`.
* Java lets you have a method with the same name as the class. The difference between the constructor and the method is identified by the _return type_. A method must have a return type while a constructor cannot.
* Constructors are not inherited.
* By default the compiler creates a no-argument constructor for you, ONLY if you didn't touch the constructor part itself. If you write a constructor that takes argument and still want a no-argument constructor, then you've to write it yourself.
* If you have more than one constructor, then they MUST have different argument list. That includes argument type, number of arguments and the order in which the arguments are given.
* Always try to make a no-argument constructor, to make it easy for the programmer to make a working object, by providing with the default values.
* More than one constructor in a class means the constructor is overloaded. The overloaded constructors must have different argument list.
* Making an object, fires up the chain reaction on the constructors over the whole inheritance tree.
* The super constructors runs to build out the superclass part of the object.
* Even when the instance variables are not inherited (marked as `private`), the sub-class depends on the methods of the superclass, which might use the private variables.
* When a constructor runs, it immediately calls its superclass's constructor, all the way up to the `Object` constructor.
* To make the constructor call the superclass's constructor, use the `super()` statement inside the subclass constructor. This calls the superclass's constructor.
* Even if we didn't call the `super()` constructor, the compiler puts one automatically for us. Thus mentioning the statement is optional.
* The superclass part of an object must be fully-formed before the subclass part of the object can be constructed.
* Since the superclass parts of the object must be fully-formed before the subclass part of the object is even begun to be constructed, the call to the superclass constructor (`super()`) must be the first statement in the constructor.
* We can also put argument in the `super(<args>)` constructor call to call the overloaded constructors.
* Similar to the keyword `super()`, which calls the constructor of the parent/superclass, the keyword `this()` calls the constructor of its own class. This `this()` call can be used to call an overloaded constructor from within the same class. This makes it easy when, all the overridden constructors do the same thing with minor changes. Thus we can put all the common stuff in a single constructor and call the overridden constructor from the same class.
* The keyword `this` is a reference to the current object. The statement (call) `this()` can be said only inside a constructor and that too, must be the first statement of the constructor.
* But the statement `super()` must also be the first statement of the a constructor, right. There is an option. Either the statement `super()` or `this()` must be the first statement of the constructor. But NEVER both.
* Since at least one constructor must have `super()` call, that constructor is The Real Constructor. There can be multiple ones. This does the Real Work of initialising the object.
* The object lives as long as the *reference variable* which refers to it lives. So how long does the *reference variable* lives? That depends on whether the variable is a local or an instance variable.
* A local variable lives as long as the method in which it is declared lives on the stack frame. Once the stack frame is removed from the stack, the variable goes out of existence.
* An instance variable lives as long as the object that contains it lives. Which in turn depends on the lifetime of the reference variable.
* There is a difference between *Scope* and *being alive*.
* Being alive means how long the variable can retain its value. A local variable can retain its value as long as the method in which it is declared is on the stack.
* Scope means when the variable is accessible. A local variable is accessible only when the stack frame (the method) in which it is contained (declared) is at the top of the stack. In other words, the local variable is accessible only when the variable's method is the one currently running.
* In case of Reference variables, the rules are same for both primitives and reference variables. The variable lives as long as the method is on the stack (for local variables) or (in case of instance variables) as long as its object lives.
* When the reference to an object dies and it is the *only* reference to it, then the object is eligible for *garbage collection*. So, when your program runs out of memory, the garbage collector (GC) collect all the un-referenced objects to reclaim memory to run the program.
* There are three ways to get rid of an objects reference,
  * When its method dies.
  * The reference is assigned to another new object. (Reprogrammed)
  * The reference is assigned to `null`. (Deprogrammed)