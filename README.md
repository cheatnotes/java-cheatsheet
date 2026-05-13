# Java Programming Comprehensive Cheatsheet

> **Comprehensive Java programming cheatsheet with 14 topics: basic syntax, data types, operators, control flow, arrays, strings, OOP, exceptions, collections, I/O, multithreading, lambda/streams, utilities & best practices. Quick reference for beginners to advanced developers. Includes code examples, version highlights, and practical tips.**

## Table of Contents

1. [Basic Syntax](#1-basic-syntax)
2. [Data Types & Variables](#2-data-types--variables)
3. [Operators](#3-operators)
4. [Control Flow](#4-control-flow)
5. [Arrays](#5-arrays)
6. [Strings](#6-strings)
7. [Object-Oriented Programming (OOP)](#7-object-oriented-programming-oop)
8. [Exception Handling](#8-exception-handling)
9. [Collections Framework](#9-collections-framework)
10. [Input & Output (I/O)](#10-input--output-io)
11. [Multithreading](#11-multithreading)
12. [Lambda & Streams (Java 8+)](#12-lambda--streams-java-8)
13. [Common Utilities](#13-common-utilities)
14. [Best Practices & Tips](#14-best-practices--tips)

---

## 1. Basic Syntax

```java
// Single-line comment

/* 
   Multi-line comment 
*/

// Main method (entry point)
public static void main(String[] args) {
    System.out.println("Hello, World!");
}

// Naming conventions
// Classes: PascalCase (MyClass)
// Methods/variables: camelCase (myMethod)
// Constants: UPPER_SNAKE_CASE (MAX_SIZE)
// Packages: lowercase (com.example.myapp)
```

---

## 2. Data Types & Variables

### Primitive Types

| Type | Size | Range/Example |
|------|------|---------------|
| `byte` | 1 byte | -128 to 127 |
| `short`| 2 bytes | -32,768 to 32,767 |
| `int` | 4 bytes | -2³¹ to 2³¹-1 |
| `long` | 8 bytes | -2⁶³ to 2⁶³-1 (suffix `L`) |
| `float` | 4 bytes | ~±3.4e38 (suffix `f`) |
| `double`| 8 bytes | ~±1.8e308 |
| `char` | 2 bytes | Unicode (0-65,535) |
| `boolean`| 1 bit | `true` / `false` |

### Reference Types

```java
// Strings, arrays, classes, interfaces, enums
String name = "Java";
int[] numbers = {1, 2, 3};
```

### Variable Declaration

```java
int x = 10;
double pi = 3.14;
boolean isReady = true;
char grade = 'A';
long bigNum = 100000L;
float precise = 5.75f;

// Type inference (Java 10+)
var message = "Inferred type";  // String
var count = 42;                  // int
```

---

## 3. Operators

### Arithmetic
```java
+   -   *   /   %   ++   --
```

### Relational
```java
==   !=   >   <   >=   <=
```

### Logical
```java
&&   ||   !   &   |   ^   (short-circuit: &&, ||)
```

### Bitwise
```java
&   |   ^   ~   <<   >>   >>>
```

### Assignment
```java
=   +=   -=   *=   /=   %=   &=   |=   ^=   <<=   >>=
```

### Ternary
```java
condition ? exprIfTrue : exprIfFalse
int max = (a > b) ? a : b;
```

### instanceof
```java
if (obj instanceof String) { ... }
// Pattern matching (Java 16+)
if (obj instanceof String s) { System.out.println(s.length()); }
```

---

## 4. Control Flow

### If-Else
```java
if (condition) {
    // code
} else if (otherCondition) {
    // code
} else {
    // code
}
```

### Switch (traditional & enhanced)
```java
// Traditional
switch (value) {
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // code
}

// Enhanced (Java 14+)
switch (day) {
    case MONDAY, FRIDAY -> System.out.println("Work");
    case SATURDAY, SUNDAY -> System.out.println("Weekend");
    default -> System.out.println("Midweek");
}

// Switch as expression
int numLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> 6;
    case TUESDAY -> 7;
    default -> 8;
};
```

### Loops
```java
// for loop
for (int i = 0; i < 10; i++) { }

// enhanced for (for-each)
for (String item : collection) { }

// while
while (condition) { }

// do-while
do { } while (condition);

// break, continue
break;      // exit loop
continue;   // skip to next iteration
```

---

## 5. Arrays

### Declaration & Initialization
```java
// Declaration
int[] arr;
int arr[];   // valid but not preferred

// Initialization
arr = new int[5];
int[] arr2 = {1, 2, 3, 4, 5};
int[] arr3 = new int[]{10, 20, 30};

// Multi-dimensional
int[][] matrix = new int[3][4];
int[][] matrix2 = {{1,2}, {3,4}};
```

### Common Operations
```java
int[] nums = {5, 2, 8, 1};
int length = nums.length;          // 4
Arrays.sort(nums);                  // [1,2,5,8]
Arrays.fill(nums, 0);               // fill with zeros
Arrays.toString(nums);              // "[1, 2, 5, 8]"
Arrays.equals(arr1, arr2);          // compare
int[] copy = Arrays.copyOf(nums, nums.length);
int index = Arrays.binarySearch(nums, 5);  // requires sorted
```

---

## 6. Strings

### Creation & Methods
```java
String s1 = "Hello";
String s2 = new String("World");

// Common methods
s1.length();                // 5
s1.charAt(1);               // 'e'
s1.substring(1, 4);         // "ell"
s1.indexOf('l');            // 2
s1.lastIndexOf('l');        // 3
s1.equals("Hello");         // true
s1.equalsIgnoreCase("hello"); // true
s1.compareTo("Hi");         // negative
s1.contains("ell");         // true
s1.replace('l', 'p');       // "Heppo"
s1.toUpperCase();           // "HELLO"
s1.toLowerCase();           // "hello"
s1.trim();                  // remove whitespace
"a,b,c".split(",");         // ["a","b","c"]
String.join("-", "a","b");  // "a-b"
```

### StringBuilder (mutable)
```java
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(" ");
sb.append("World");
sb.insert(5, ",");          // "Hello, World"
sb.reverse();               // "dlroW ,olleH"
sb.toString();              // convert to String
```

---

## 7. Object-Oriented Programming (OOP)

### Class Definition
```java
public class Person {
    // Fields (instance variables)
    private String name;
    private int age;
    
    // Static (class) variable
    public static int population = 0;
    
    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
        population++;
    }
    
    // Methods
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    
    // Static method
    public static int getPopulation() { return population; }
    
    // Override toString
    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}
```

### Inheritance
```java
public class Student extends Person {
    private String studentId;
    
    public Student(String name, int age, String studentId) {
        super(name, age);   // call parent constructor
        this.studentId = studentId;
    }
    
    @Override
    public String toString() {
        return super.toString() + " - " + studentId;
    }
}
```

### Abstract Classes & Interfaces
```java
// Abstract class
abstract class Animal {
    abstract void makeSound();   // no body
    void breathe() { System.out.println("Breathing"); }
}

// Interface (Java 8+)
interface Flyable {
    void fly();
    
    // Default method
    default void land() {
        System.out.println("Landing...");
    }
    
    // Static method
    static void glide() {
        System.out.println("Gliding");
    }
}

// Multiple inheritance with interfaces
class Bird extends Animal implements Flyable {
    @Override
    void makeSound() { System.out.println("Chirp"); }
    
    @Override
    public void fly() { System.out.println("Flying"); }
}
```

### Enums
```java
enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}

// Enum with fields and methods
enum Status {
    SUCCESS(200), ERROR(500);
    
    private final int code;
    Status(int code) { this.code = code; }
    public int getCode() { return code; }
}
```

### Access Modifiers

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| default | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

### Key Keywords
```java
this        // reference to current object
super       // reference to parent
final       // constant, prevent overriding/inheritance
static      // belongs to class, not instance
abstract    // must be implemented
synchronized // thread-safe
volatile    // variable stored in main memory
transient   // skip during serialization
```

---

## 8. Exception Handling

### Hierarchy
```
Throwable
├── Error (unrecoverable, don't catch)
└── Exception
    ├── RuntimeException (unchecked)
    └── Checked Exception (must handle)
```

### Try-Catch-Finally
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero: " + e.getMessage());
} catch (Exception e) {
    e.printStackTrace();
} finally {
    System.out.println("Always executes");
}
```

### Try-with-Resources (Java 7+)
```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line = br.readLine();
} catch (IOException e) {
    e.printStackTrace();
} // br automatically closed
```

### Custom Exception
```java
class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}

// Throwing
throw new MyException("Something went wrong");
```

---

## 9. Collections Framework

### Main Interfaces

| Interface | Implementation | Order | Sorted | Duplicates | Null |
|-----------|---------------|-------|--------|------------|------|
| `List` | `ArrayList`, `LinkedList` | ✅ | ❌ | ✅ | ✅ |
| `Set` | `HashSet`, `LinkedHashSet` | ❌/✅ | ❌ | ❌ | ✅(1) |
| `Set` | `TreeSet` | ✅ | ✅ | ❌ | ❌ |
| `Queue` | `PriorityQueue`, `ArrayDeque` | ✅ | ❌ | ✅ | ❌ |
| `Map` | `HashMap`, `LinkedHashMap` | ❌/✅ | ❌ | keys ❌ | ✅(1) |
| `Map` | `TreeMap` | ✅ | ✅ | keys ❌ | ❌ |

### ArrayList Example
```java
import java.util.*;

List<String> list = new ArrayList<>();
list.add("Apple");
list.add(1, "Banana");
list.get(0);
list.set(1, "Orange");
list.remove(0);
list.size();
list.contains("Apple");
list.isEmpty();
Collections.sort(list);

// Iteration
for (String item : list) { }
list.forEach(item -> System.out.println(item));
```

### HashMap Example
```java
Map<String, Integer> map = new HashMap<>();
map.put("Alice", 25);
map.put("Bob", 30);
int age = map.get("Alice");
map.getOrDefault("Charlie", 0);
map.containsKey("Bob");
map.remove("Alice");

for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

### Useful Collections Methods
```java
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
Collections.max(collection);
Collections.min(collection);
Collections.binarySearch(list, key);  // sorted list required
```

---

## 10. Input & Output (I/O)

### Console Input
```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
String text = sc.nextLine();    // read entire line
int num = sc.nextInt();          // read int
double d = sc.nextDouble();
boolean b = sc.nextBoolean();
sc.close();

// Console (for passwords)
Console console = System.console();
char[] password = console.readPassword("Enter password: ");
```

### File Reading
```java
// Using Files (Java 7+)
List<String> lines = Files.readAllLines(Paths.get("file.txt"));
String content = Files.readString(Paths.get("file.txt"));

// BufferedReader
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
}
```

### File Writing
```java
// Using Files
Files.writeString(Paths.get("output.txt"), "Hello World");
Files.write(Paths.get("output.txt"), lines);  // List<String>

// BufferedWriter
try (BufferedWriter bw = new BufferedWriter(new FileWriter("file.txt"))) {
    bw.write("Hello");
    bw.newLine();
    bw.write("World");
}
```

---

## 11. Multithreading

### Creating Threads
```java
// Extend Thread
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}
MyThread t1 = new MyThread();
t1.start();

// Implement Runnable
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable running");
    }
}
Thread t2 = new Thread(new MyRunnable());
t2.start();

// Lambda
Thread t3 = new Thread(() -> System.out.println("Lambda thread"));
t3.start();
```

### Thread Methods
```java
Thread.sleep(1000);          // milliseconds
thread.join();                // wait for thread to finish
thread.interrupt();           // interrupt thread
Thread.currentThread();       // get current thread
```

### Synchronization
```java
// Synchronized method
public synchronized void increment() {
    count++;
}

// Synchronized block
synchronized(this) {
    count++;
}

// Locks (more flexible)
Lock lock = new ReentrantLock();
lock.lock();
try {
    // critical section
} finally {
    lock.unlock();
}
```

### Executor Framework
```java
ExecutorService executor = Executors.newFixedThreadPool(10);
executor.submit(() -> System.out.println("Task"));
Future<String> future = executor.submit(() -> "Result");
String result = future.get();   // blocks
executor.shutdown();
```

---

## 12. Lambda & Streams (Java 8+)

### Lambda Expressions
```java
// Syntax: (parameters) -> expression or { statements }

// Functional interfaces
Runnable r = () -> System.out.println("Hello");
Comparator<String> comp = (a, b) -> a.length() - b.length();
Predicate<Integer> isEven = n -> n % 2 == 0;
Function<String, Integer> length = s -> s.length();
Consumer<String> printer = s -> System.out.println(s);
Supplier<Double> random = () -> Math.random();
```

### Stream API
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Intermediate ops: filter, map, sorted, distinct, limit, skip
// Terminal ops: forEach, collect, reduce, count, anyMatch, findFirst

// Chaining
names.stream()
    .filter(name -> name.length() > 3)
    .map(String::toUpperCase)
    .sorted()
    .forEach(System.out::println);

// Collect to list
List<String> longNames = names.stream()
    .filter(n -> n.length() > 3)
    .collect(Collectors.toList());

// Primitive streams
IntStream.range(1, 10).sum();           // 45
IntStream.rangeClosed(1, 10).average();

// Reduce
int sum = numbers.stream().reduce(0, Integer::sum);
Optional<String> reduced = strings.stream().reduce((a,b) -> a + "," + b);
```

### Method References
```java
// Types: static, instance, constructor
Math::max                // static method
String::length           // instance method of arbitrary object
System.out::println      // instance method of specific object
ArrayList::new           // constructor
```

---

## 13. Common Utilities

### Date & Time (Java 8+)
```java
import java.time.*;

LocalDate date = LocalDate.now();
LocalTime time = LocalTime.now();
LocalDateTime dt = LocalDateTime.now();

// Specific values
LocalDate.of(2024, Month.JANUARY, 1);
LocalTime.of(14, 30);

// Formatting
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");
String formatted = dt.format(formatter);

// Parsing
LocalDate parsed = LocalDate.parse("2024-01-01");

// Calculations
LocalDate tomorrow = date.plusDays(1);
LocalDate lastMonth = date.minusMonths(1);
Period period = date.until(LocalDate.of(2024, 12, 31));
```

### Math
```java
Math.PI, Math.E
Math.abs(-5);           // 5
Math.max(3, 7);         // 7
Math.min(3, 7);         // 3
Math.pow(2, 3);         // 8.0
Math.sqrt(16);          // 4.0
Math.random();          // 0.0 to 1.0
Math.round(3.6);        // 4
Math.ceil(3.1);         // 4.0
Math.floor(3.9);        // 3.0
```

### Random Numbers
```java
Random rand = new Random();
rand.nextInt(100);       // 0-99
rand.nextDouble();       // 0.0-1.0
rand.nextBoolean();

// Secure random
SecureRandom secure = new SecureRandom();
```

---

## 14. Best Practices & Tips

### Naming & Structure
- **Packages**: `com.company.project.module`
- **Classes**: PascalCase, nouns (`Customer`, `OrderService`)
- **Methods**: camelCase, verbs (`calculateTotal`, `getName`)
- **Constants**: UPPER_SNAKE_CASE (`MAX_RETRY_COUNT`)

### Coding Conventions
```java
// Braces: K&R style (opening brace same line)
if (condition) {
    // code
}

// Indentation: 4 spaces
// One statement per line
// No magic numbers: use constants
private static final int MAX_USERS = 100;
```

### Performance Tips
- Use `StringBuilder` for repeated concatenation
- Prefer `ArrayList` over `LinkedList` for random access
- Use primitive streams (`IntStream`) for better performance
- Initialize collections with capacity when known
- Use `try-with-resources` for auto-closing

### Common Pitfalls
```java
// Equality: use equals() for objects, == for primitives
String s1 = new String("Hi");
String s2 = new String("Hi");
s1 == s2;          // false (different objects)
s1.equals(s2);     // true

// Null checks
if (obj != null && obj.method()) { }  // order matters

// Integer caching (-128 to 127)
Integer a = 127, b = 127;
a == b;    // true (cached)
Integer c = 128, d = 128;
c == d;    // false
```

### Java Versions Quick Reference

| Version | Key Features |
|---------|--------------|
| Java 8 | Lambdas, Streams, Optional, Date/Time API |
| Java 9 | Modules, private interface methods |
| Java 10 | `var` (local variable type inference) |
| Java 11 | HTTP Client, local-variable syntax for lambdas |
| Java 14 | Records, pattern matching for `instanceof` |
| Java 16 | `record` classes |
| Java 17 | Sealed classes, pattern matching switch (preview) |
| Java 21 | Virtual threads, sequenced collections |

---

*This cheatsheet covers the most essential Java concepts. For detailed documentation, visit [docs.oracle.com](https://docs.oracle.com/en/java/).*
