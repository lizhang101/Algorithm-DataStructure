Java language learning.
### tutorials point [Java Tutorial](https://www.tutorialspoint.com/java/index.htm)
### javatpoint [Java Tutorial](https://www.javatpoint.com/java-tutorial)

# QA
- [Difference between add() and offer() methods of Queue interface](https://stackoverflow.com/questions/20526910/difference-between-add-and-offer-methods-of-queue-interface)
  ```
  Queue.add - throws an exception if the operation fails,
  Queue.offer - returns a special value (either null or false, depending on the operation).
  ```
- [Queue remove vs poll](https://stackoverflow.com/questions/2193450/why-java-provides-two-methods-to-remove-element-from-queue)
  ```
  The remove() and poll() methods differ only in their behavior when the queue is empty:
  the remove() method throws an exception, 
  while the poll() method returns null
  ```

# 1. Basics 
### local variable VS. instance variable
- local variable: variable declared inside method;
- instance variable: variable decalred inside class but outside method.
### primitive VS. reference types
- Primitive types
  - boolean, byte, char, short, int, long, float, double
  - Variable holds one value of given type
  - boolean instance variables, initialized to _**false**_
  - Other primitive instance variables initialized to _**0**_
  - Do NOT have methods
  - promotion rules
    - argument promotion
      - converting an argument's value, if possible, to the type that the method expects to receive in its corresponding parameter
      - only promote from lower to higher type, eg. short -> int. NOT long -> short. Allowed promotions:
        - double -> None
        - float -> double
        - long -> float or double
        - int -> long, float or double
        - char -> int, long, float or double
        - short -> int, long, float or double
        - byte -> short, int, long, float or double
        - boolean -> None. _**boolean values are not considered to be numbers in Java.**_
      - may lead to compilation errors if Java's promotion rules are not satisfied
  
- Reference types
  - Any non-primitive type is a reference type
  - Variable refer to objects that may contain many instance variables
  - Default instance variable value is _**null**_ - reference to nothing
  - Reference required to call an object's methods

### Methods : in-depth
- **static** methods and variables
  - static methods perform tasks that do not require an object of the class
  - static method call : `ClassName.methodName(args)`
  - Docs show which class members are static. Example: Math class.
  - Modifiers : public, final, static
    - public : allows you to use these fields in your own classes
    - final : the value is constant and cannot be changed after initialization
    - static : access via the class name and a dot(.) separator
  - All objects of a class share one copy of the class's static fields
  - Fields of a class - class variables and instance variables
  
- why **main** is static

- some common Java packages
  - [Java SE8 packages documentation](http://docs.oracle.com/javase/8/docs/api/index.html)
  
- secure random number generation
  - `import java.security.SecureRandom`
  
- named constants with **enum** types

- scope of identifiers
  - Parameter declaration: body of the method in which the declaration appears
  - Local-variable declaration: from the declaration to the end of that block
  - Local-variable declaration that appears in the initialization section of a _for_ statement's header: entire for statement
  - Method or field's scope:
    - entire body of the class
    - instance methods can use all class members
    
- method overloading

### Array and ArrayList
- declare an array w/o initialization
  ```
  int[] arr0 = new int[10];
  int[] arr1 = {1,2,3,4,5,6,7};
  ```

- Enhanced _**for**_ loop
  ```
  int[] arr = {3,1,5,8,2,9,7,6,4};
  int total = 0;
  for (int num : arr) {
    total += num;
  }
  System.out.printf("Total of array elements : %d%n", total);
  ```
  
- java.util.Arrays
- java.util.ArrayList

# 2. Java Collections Framework
- [tutorial](http://beginnersbook.com/java-collections-tutorials/)

![Java collections](JAVA-collections.jpg)

![Java collections 2](Java_collections.JPG)

## Queue
### basic operations

 Operation | Throws exception | Returns special value
 --------- | ---------------- | -----------------------
 inserts the element e to the tail of the queue. | add(E e): If there is no space available because of capacity restrictions, IllegalStateException is thrown. | offer(E e): If the insertion is successful the method returns true, otherwise it returns false. Generally, if there are capacity bounds, it is preferred to use add method instead.
 removes and returns the head (the first element) of the queue. | remove(): throw NoSuchElementException if the queue is empty. | poll(): returns null when the queue is empty.
 returns the head of the queue, without removing it. | element(): throw NoSuchElementException if the queue is empty. | peek(): return null is the queue is empty.

## [LinkedList](https://beginnersbook.com/2013/12/linkedlist-in-java-with-example/)


