Java language learning.
### [Java Tutorial](https://www.tutorialspoint.com/java/index.htm)


# 1. Basic data types
## 1.1 Primitive Data Types

  type | definition | min value | max value | default value | main usage
  ---- | ---------- | --------- | --------- | ------------- | ------------------
  byte | 8-bit signed two's complement integer | -128 (-2^7) | 127 (inclusive)(2^7 -1) | 0 |  is used to save space in large arrays, mainly in place of integers
  short | 16-bit signed two's complement integer | -32,768 (-2^15) | 32,767 (inclusive) (2^15 -1) | 0 | can also be used to save memory as byte data type
  int | 32-bit signed two's complement integer | -2^31 | (2^31 -1)(inclusive) | 0 | is generally used as the default data type for integral values unless there is a concern about memory
  long | 64-bit signed two's complement integer | -2^63 | (2^63 -1)(inclusive) | 0L | is used when a wider range than int is needed. e.g.: long a = 100000L
  float | 32-bit IEEE 754 floating point |  |  | 0.0f | mainly used to save memory in large arrays of floating point numbers, is never used for precise values such as currency. e.g.: float f1 = 234.5f
  double | double-precision 64-bit IEEE 754 floating point |  |  | 0.0d | generally used as the default data type for decimal values, should never be used for precise values such as currency. e.g.: double d1 = 123.4
  boolean | represents one bit of information, true / false |  |  | false | used for simple flags that track true/false conditions
  char | single 16-bit Unicode character | '\u0000' (or 0) | '\uffff' (or 65,535 inclusive) |  | used to store any character
  
## 1.2 Reference/Object Data Types
- Class objects and various type of array variables come under reference datatype.
- Default value of any reference variable is null.
- Reference variables are created using defined constructors of the classes. They are used to access objects. These variables are declared to be of a specific type that cannot be changed. For example, Employee, Puppy, etc.
- A reference variable can be used to refer any object of the declared type or any compatible type.


# 2. Variable types
- [details](https://www.tutorialspoint.com/java/java_variable_types.htm)

  type | definition | memory locatoin
  ---- | ---------- | -------------------
  Local variables | Variables defined inside methods, constructors or blocks. The variable will be declared and initialized within the method and the variable will be destroyed when the method has completed. | stack
  Instance variables | Variables within a class but outside any method. These variables are initialized when the class is instantiated. Instance variables can be accessed from inside any method, constructor or blocks of that particular class. | heap
  Class/Static variables | Variables declared within a class, outside any method, with the **static** keyword. | static memory

# 3. Modifier Types
- Modifiers are keywords that you add to those definitions to change their meanings.
- To use a modifier, you include its keyword in the definition of a class, method, or variable. The modifier precedes the rest of the statement.
- Java language has a wide variety of modifiers, including
  - [Access Modifiers](https://www.tutorialspoint.com/java/java_access_modifiers.htm)
    
    Java provides a number of access modifiers to set access levels for classes, variables, methods and constructors.
    - Visible to the package, the default. No modifiers are needed.
    - Visible to the class only (private).
    - Visible to the world (public).
    - Visible to the package and all subclasses (protected).
    
  - [Non Access Modifiers](https://www.tutorialspoint.com/java/java_nonaccess_modifiers.htm)
  
    Java provides a number of non-access modifiers to achieve many other functionality.

    - The _**static**_ modifier for creating class methods and variables.
    - The _**final**_ modifier for finalizing the implementations of classes, methods, and variables.
    - The _**abstract**_ modifier for creating abstract classes and methods.
    - The _**synchronized**_ and _**volatile**_ modifiers, which are used for threads.

# Basic concepts
## Classes : A class is a template/blueprint for object.
## Objects : An object is an instance of a class.
## Instance
## Method
## Message Parsing

## Polymorphism
## Inheritance
## Encapsulation
## Abstraction


### Variable types in class


  
### Constructor

- Every class has a constructor. If we do not explicitly write a constructor for a class, the Java compiler builds a default constructor for that class.
- A class can have more than one constructor. Each time a new object is created, at least one constructor will be invoked.
- The main rule of constructors is that they should have the same name as the class.
  
  


