Java language learning.
### tutorials point [Java Tutorial](https://www.tutorialspoint.com/java/index.htm)
### javatpoint [Java Tutorial](https://www.javatpoint.com/java-tutorial)


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

# 2. Java Collections Framework
- [tutorial](http://beginnersbook.com/java-collections-tutorials/)

![Java collections](JAVA-collections.jpg)

![Java collections 2](Java_collections.JPG)
