# Notes on practice

* ~~Unlike python, where we can use the same variable name for both the local parameter and the global (or at least with higher scope) variable, in Java we cannot use the same name for two variables.~~
* We can use same name for both instance and local variable. But to access an instance variable inside the method, use the `this.variableName` and to access the local variable, just use the `variableName`.
* To get input from console, use the `Scanner` class. Ex.

```java
Scanner scanner = new Scanner(System.in);
String myString = scanner.next();
int myInt = scanner.nextInt();
scanner.close();

System.out.println("myString is: " + myString);
System.out.println("myInt is: " + myInt);
```

* For left justifying use the (-) sign.
* To add more than one items in a ArrayList while initialising... use `Arrays.asList(1,2,3,4,5)` method.
* To create a uniqueID use UUID ---> `String uniqueID = UUID.randomUUID().toString();`