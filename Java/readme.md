# Java language learning.
## Tutorials
### [Tutorials Point](https://www.tutorialspoint.com/java/index.htm)
### [javaTpoint](https://www.javatpoint.com/java-tutorial)
### [javatutorialhq](http://javatutorialhq.com/java/)
- core concept
- Java API
### [java2novice](https://www.java2novice.com/)
### [beginner's book](https://beginnersbook.com/java-tutorial-for-beginners-with-examples/)

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
  
- [Java: How to split a String into an ArrayList](http://programming.guide/java/split-string-into-arraylist.html)  
  ```
	String s = "lorem,ipsum,dolor,sit,amet";
	List<String> myList = new ArrayList<String>(Arrays.asList(s.split(",")));
	
	List<String> strings = Arrays.asList(new String[]{"one", "two", "three"});      // immutable
	List<String> strings = 
     new ArrayList<String>(Arrays.asList(new String[]{"one", "two", "three"}));   // mutable
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

### [Character Class](https://docs.oracle.com/javase/7/docs/api/java/lang/Character.html)
The [java.lang.Character class](https://www.tutorialspoint.com/java/lang/java_lang_character.htm) wraps a value of the primitive type char in an object. An object of type Character contains a single field whose type is char.
- mainly used methods

  Method | Description
  ------ | --------------------
  isLetter() | Determines whether the specified char value is a letter.
  isDigit() | Determines whether the specified char value is a digit.
  isWhitespace() | Determines whether the specified char value is white space.
  isUpperCase() | Determines whether the specified char value is uppercase.
  isLowerCase() | Determines whether the specified char value is lowercase.
  toUpperCase() | Returns the uppercase form of the specified char value.
  toLowerCase() | Returns the lowercase form of the specified char value.
  toString() | Returns a String object representing the specified character value that is, a one-character string.
  getNumericValue() | returns the _int_ value that the specified Unicode character represents.

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
  - [Deep Understanding of Arrays.sort()](https://www.programcreek.com/2013/11/arrays-sort-comparator/)
  - [Java Comparator Example](https://examples.javacodegeeks.com/core-java/util/comparator/java-comparator-example/)
- java.util.ArrayList

# 2. Java Collections Framework
- [tutorial](http://beginnersbook.com/java-collections-tutorials/)

![Java collections](JAVA-collections.jpg)

![Java collections 2](Java_collections.JPG)

## [Queue](https://beginnersbook.com/2017/08/queue-interface-in-java-collections/)
### basic operations

 Operation | Throws exception | Returns special value
 --------- | ---------------- | -----------------------
 inserts the element e to the tail of the queue. | add(E e): If there is no space available because of capacity restrictions, IllegalStateException is thrown. | offer(E e): If the insertion is successful the method returns true, otherwise it returns false. Generally, if there are capacity bounds, it is preferred to use add method instead.
 removes and returns the head (the first element) of the queue. | remove(): throw NoSuchElementException if the queue is empty. | poll(): returns null when the queue is empty.
 returns the head of the queue, without removing it. | element(): throw NoSuchElementException if the queue is empty. | peek(): return null is the queue is empty.

## [LinkedList](https://beginnersbook.com/2013/12/linkedlist-in-java-with-example/)
`LinkedList<T> llist  = new LinkedList<T>();`

- Methods of LinkedList:
	- **boolean add(Object element)** : It appends the element to the end of the list.
	- **void add(int index, Object element)**: It inserts the element at the position ‘index’ in the list.
	- **void addFirst(Object element)** : It inserts the element at the beginning of the list.
	- **void addLast(Object element)** : It appends the element at the end of the list.
	- **boolean contains(Object element)** : It returns true if the element is present in the list.
	- **Object get(int index)** : It returns the element at the position ‘index’ in the list. It throws ‘IndexOutOfBoundsException’ if the index is out of range of the list.
	- **int indexOf(Object element)** : If element is found, it returns the index of the first occurrence of the element. Else, it returns -1.
	- **Object remove(int index)** : It removes the element at the position ‘index’ in this list. It throws ‘NoSuchElementException’ if the list is empty.
	- **int size()** : It returns the number of elements in this list.
	- **void clear()** : It removes all of the elements from the list.

- [LinkedList to array](https://beginnersbook.com/2014/07/how-to-convert-linkedlist-to-array-using-toarray-in-java/)
```
  //Creating and populating LinkedList
  LinkedList<String> linkedlist = new LinkedList<String>();
  linkedlist.add("Harry");
  linkedlist.add("Maddy");
  linkedlist.add("Chetan");
  linkedlist.add("Chauhan");
  linkedlist.add("Singh");

  //Converting LinkedList to Array
  String[] array = linkedlist.toArray(new String[linkedlist.size()]);
```

## [ArrayList](https://beginnersbook.com/2013/12/java-arraylist/)
`ArrayList<T> obj = new ArrayList<T>();`
- [ArrayList to Array](http://www.geeksforgeeks.org/arraylist-array-conversion-java-toarray-methods/)
```
  List<Integer> al = new ArrayList<Integer>();
  al.add(10);
  al.add(20);
  al.add(30);
  al.add(40);

  Integer[] arr = al.toArray(new Integer[al.size()]);
```

## [ArrayList VS. LinkedList](https://beginnersbook.com/2013/12/difference-between-arraylist-and-linkedlist-in-java/)

Operation | performance    ArrayList  :   LinkedList
--------- | -------------------------------------------
Search : get(int index) |  O(1)  :  O(n)
Deletion : remove(int index) | O(n)/O(1)  :  O(1)
Inserts : add(int index) |  O(n)/O(1)  :  O(1)

## [HashMap](http://javatutorialhq.com/java/util/hashmap-class/)
- iterate hashmap
```
Map<String, Integer> items = new HashMap<>();
items.put("A", 10);
items.put("B", 20);
items.put("C", 30);
items.put("D", 40);
items.put("E", 50);
items.put("F", 60);

for (Map.Entry<String, Integer> entry : items.entrySet()) {
	System.out.println("Item : " + entry.getKey() + " Count : " + entry.getValue());
}
```

In Java 8, you can loop a Map with forEach + lambda expression.
```
Map<String, Integer> items = new HashMap<>();
items.put("A", 10);
items.put("B", 20);
items.put("C", 30);
items.put("D", 40);
items.put("E", 50);
items.put("F", 60);

items.forEach((k,v)->System.out.println("Item : " + k + " Count : " + v));

items.forEach((k,v)->{
	System.out.println("Item : " + k + " Count : " + v);
	if("E".equals(k)){
		System.out.println("Hello E");
	}
});
```

## [Dequeue](http://www.geeksforgeeks.org/deque-interface-java-example/)
Methods of deque:

- add(element): Adds an element to the tail.
- addFirst(element): Adds an element to the head.
- addLast(element): Adds an element to the tail.
- offer(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
- offerFirst(element): Adds an element to the head and returns a boolean to explain if the insertion was successful.
- offerLast(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
- iterator(): Returna an iterator for this deque.
- descendingIterator(): Returns an iterator that has the reverse order for this deque.
- push(element): Adds an element to the head.
- pop(element): Removes an element from the head and returns it.
- removeFirst(): Removes the element at the head.
- removeLast(): Removes the element at the tail.
