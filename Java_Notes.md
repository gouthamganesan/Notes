# Java notes

Head First Java Book notes

## Chapter 8: Serious Polymorphism

* Interfaces means 100% abstract classes. Abstract classes are classes which cannot be instantiated.
* Abstract methods can have no body. They must be overridden.
* An abstract method must always be inside an abstract class.
* abstract methods are there to make the methods a must for the classes that extend from this parent abstract class. This is to define a protocol for the group of sub-classes (sub-types)
* The abstract methods must be implemented as they don't have a body.
* THE COMPILER DECIDES WHETHER YOU CAN CALL A METHOD OR NOT, BASED ON THE TYPE OF THE **REFERENCE** NOT THE ACTUAL OBJECT TYPE.
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

## Chapter 10: Number matters

* There are cases where the instance variable of a class has no effect over one of the methods of the class. In other words, the only data involved with such methods are the ones that come as a parameter and the one that it returns.
* These methods are declared as `static` and they can be access by mentioning the class name and not the object name. For example, to access the methods like `min()` or `max()` from the `Math` class, all you need is the class name. In fact Math class doesn't have any instance variables. And moreover, we can't make an instance of the class Math.
* A normal object has an instance of the method (a copy of the method and the instance variable bundled - Encapsulation). So, a normal non-static method runs with an instance of the class.
* The keyword `static` lets the method run without an instance of the class. Which essentially tells that the behaviour of the method is not dependent of the instance variables of the class.
* So, while a normal method is accessed by mentioning the instance name using the dot operator, a static method is called using the dot operator on the class name.
* The reason the Math class can't have an object is that the constructor of the class is marked as `private`. So only code from inside the Math class can invoke that constructor. (Another way to restrict the class from being instantiated is marking the class `abstract`, Chapter 8)
* Static methods run without knowing about any particular instance of the static method's class.
* Since a static method is called using the class's name as opposed to the instance's name, it cannot access any instance variable.
* This is because, the static method doesn't know about any of the instances (objects) of the class. Thus, it won't know who's instance variable to look for.
* For the exact same reason, the static methods cannot call a non-static method. The compiler won't know on which object the method is to be called.
* Calling a static method with any instance variable of the class, will work. But it makes the code *less readable*.
* Making a variable static makes it available for all the instances of the class. It won't belong to any object. All the objects share the same value of the static variable.
  * Instance variables = 1 per instance
  * Static variable = 1 per class
* A static variable is initialised when the class is loaded. (The JVM loads a class, when the program is gonna access it)
* Two guarantees about static initialisation: Static variables in a class are initialised before
  * any *object* of that class is created.
  * any *static method* of that class runs.
* We can access a static variable just like we do with the static method. Using the class name, provided the access modifier is set to accessible.
* A variable marked as `final` means it is a constant and its value cannot be changed.
* `public static final double PI = 3.141592653589793;` lies in the `Math.PI`. Its marked `static`, so that you don't need an instance to access it.
* Convention: Name a constant with a ALL-CAPS variable name.
* A **static initializer** is a block of code which runs when a class gets loaded. It is a nice place to initialize all static variables.

```java
class Foo {
    final static int X;
    static
    {
        X = 42;
    }
}
```

* A final variable can be initialized in two places.
  * As soon as it is created.
  * In the static initializer.
* If it is not initialized with these two, then the compiler throws an error.
* A static initializer runs before any static methods run or even before any of the static variables can be used.
* Final keyword can be used for others too...
  * All final variables (local, parameters, instance) means they cannot be changed.
    * When an instance variable is declared as final, its value can be initialized when it is declared or in the constructor.
    * When a variable is marked just as `final` then it is a constant instance variable. To make a constant variable, mark it as both `final` and `static`. This is equivalent to making a global constant in functional programming.
  * A final method means the method cannot be *overridden*.
  * A final class means the class cannot be *extended*.
* If a class is marked final, then it can't be sub-classed. So none of its methods can be overridden.
* So for this reason, when a class is marked final, there is no need to mark the method final.
* But, when there is only need to make some of the methods overridable, and you need to make a subclass, mark only the method that are not supposed to be overridden final.
* If you have a class that only has static methods, you do not want the class to be instantiated. This can be achieved by marking the constructor `private`.
* A final instance variable is not automatically initialized to a default value (for the obvious reasons).
* Some of the static methods of Math class,
  * random
  * abs
  * round
  * min
  * max
* Wrapping a primitive type in Java.

```java
int i = 28;
Integer iWrap = new Integer(i); // Wrapping
int unWrapped = iWrap.intValue(); // All unwrapping is similar to this, charValue(), booleanValue()...
```

* Wrapping is done to treat a primitive like an object.
* Before Java 5.0, we've to convert the primitive to object references using the wrappers manually. Now, the Autoboxing feature does the conversion of primitive to wrapper object automatically.
* [Difference between int and Integer in Java](https://stackoverflow.com/questions/8660691/what-is-the-difference-between-integer-and-int-in-java)
* Now after Java 5.0, we can add both int (primitive) or Integer (Object references) to ArrayList and the compiler does the wrapping (boxing) automatically.
* The rule for generic types is that, we can specify only class or interface types, not *primitives*.
* The wrapper classes have some static utility methods too. ex.
  * `int i = Integer.parseInt("3");`
  * `double d = Double.parseDouble("420.420");`
  * `boolean b = Boolean.parseBoolean("True");`
* There are many ways to turn a primitive number into a string.
  * Simplest of all is to just concatenate with a string.

    ```java
    double d = 20.5;
    String strDouble = "" + d;
    ```

  * Another method is all primitive number wrapper classes have a method to convert to a string.

    ```java
    double d = 20.5;
    String strDouble = Double.toString(d);
    ```

* Formatting a string that is to be printed, can be done using the `format` method in the `String` class. Ex. `String.format(%.2f, 2.0029)`
* The percent (%) sign says insert the string here and format it with the instructions provided (after %)

Format specifier | Effect
-----------------|-------
%.2f | The floating point number is approximated to two decimal points
%,.2f | The floating point number is approximated to two decimal points and the numbers are separated with commas

* Syntax for formatting is `%[argument number][flags][width][.precision]type`
  * Argument number - If there are more than one arguments we can specify the argument number to pair the argument with the format specifier.
  * Flags - Special formatting options, like adding comma, indenting or putting negative numbers in parentheses.
  * Width - Defines the minimum number of characters that are to be used.
  * Precision - Number f=of decimal places. Don't forget put the dot before the number.
  * Type - This is mandatory. Always the type comes last in the format specifier. The type can be both the primitive or the wrapper class.
    * d = Decimal
    * f = Floating point
    * x = Hexadecimal
    * c = Character
* Java has a `Date` class. So when a Date object is created without any arguments, it holds the value of the current time automatically. `new Date()`
* To format a date, we can use,
  * `%tc` = The complete date and time
  * `%tr` = Just the time
  * `%tA` = Day of the week
  * `%tB` = Month
  * `%td` = Day
* For example,

```java
Date today = new Date();
String.format("%tA, %tB %td", today, today, today); //Means "Sunday, November 28"
```

* For the previous example, we've to duplicate the arguments (today, today, today). For avoiding duplication,

```java
String.format("%tA, %<tB %<td", today)
```

* The `<` is a flag in the format specifier to tell the formatter to "use the previous argument again".
* For a time stamp of 'now', we can use the Date class from `java.util.Date`. For everything else, we can use the `java.util.Calendar` class.
* But the Calendar class is an abstract one. So you cannot get an instance of the class directly. Instead use the static `getInstance()` method of the class, like, `Calendar cal = Calendar.getInstance()`.
* Since the Calendar class is an abstract one, we can't create an object of it. But we can call the static methods of on the class name.
* This static function gives back the instance of a concrete subclass of the Calendar class.
* **Working with Calendar**
  * Create a Calendar instance using `Calendar.getInstance()`
  * Assign it to a Calendar reference (`Calendar cal = Calendar.getInstance()`)
    * Fields hold state - A calendar object has many states that can be used to store the ultimate state, date and time.
    * Dates and times can be incremented - It has methods to to do operations on various fields.
    * Dates and times can be represented in milliseconds - The time can be represented in milliseconds (from Jan 1, 1970) to make precise calculations.

* Calendar methods and fields
  * Methods
    * `add(int field, int amount)` - Add or subtract the time from the given field.
    * `get(int field)` - Returns the value of the given calendar field.
    * `getInstance()` -Returns a calendar. The locale can be specified optionally.
    * `getTimeInMillis()` - Returns the calendar in milliseconds, as a long.
    * `roll(int field, boolean up)` - Adds or subtracts the field without changing the larger fields.
    * `set(int field, int value)` - Sets the given value to the field.
    * `set(year, month, day, hour, minute)` - All are ints.
    * `setTimeInMillis(long millis)` - Set time in milliseconds.
  * Fields
    * `DATE` / `DAY_OF_MONTH`
    * `HOUR` / `HOUR_OF_DAY`
    * `MINUTE`
    * `MILLISECOND`
    * `MONTH`
    * `YEAR`
    * `ZONE_OFFSET`

* Static imports
* Whenever we use static methods, variables or enums we can import them and save from typing the package name again and again. But, static imports can make the code hard to read. Ex.

```java
import static java.lang.System.out;
import static java.lang.Math.*;

out.println("Hello, World!, sqrt", sqrt(2.0));
```

* Use static imports only when we've to use those methods very often. The main problem here is the naming conflict, that can happen very often.