
**Core Java Complete Guide**

# **1. Introduction to Java**

## **1.1 What is Java?**

Java is a **high-level, object-oriented, platform-independent** programming language used for developing a wide range of applications, from web apps to enterprise software. It was developed by **Sun Microsystems** (now owned by **Oracle Corporation**) and released in **1995**. Java follows the **Write Once, Run Anywhere (WORA)** principle, meaning compiled Java code can run on any platform that supports Java without recompilation.

### **Key Features of Java:**

1. **Platform Independent** – Java programs are compiled into **bytecode**, which can run on any system with a **Java Virtual Machine (JVM)**.
2. **Object-Oriented** – Java is based on **OOP principles** like **Encapsulation, Inheritance, Polymorphism, and Abstraction**.
3. **Multi-threaded** – Java supports **multithreading** to allow concurrent execution of multiple tasks.
4. **Robust & Secure** – Java has **automatic memory management (Garbage Collection)** and strict security features.
5. **Dynamic and Extensible** – Java supports dynamic linking of classes and allows usage of external libraries.

## **1.2 Java Architecture**

Java runs on the **Java Virtual Machine (JVM)**, which makes Java programs platform-independent.

### **Java Components:**

1. **JDK (Java Development Kit)** – A complete development environment that includes a compiler (`javac`), debugging tools, libraries, and the **JRE**.
2. **JRE (Java Runtime Environment)** – Provides libraries and JVM to run Java applications.
3. **JVM (Java Virtual Machine)** – Translates Java **bytecode** into **machine code** for execution.

### **Java Compilation and Execution Process:**

```plaintext
Java Source Code (.java) → Compiler (javac) → Bytecode (.class) → JVM → OS Execution
```

## **1.3 Installing Java 21**

### **Steps to Install Java 21:**
- Download from [https://jdk.java.net/21/](https://jdk.java.net/21/)
- Install and configure environment variables (`JAVA_HOME`, `PATH`)
- Verify installation using:
  ```sh
  java -version
  ```
  Expected Output:
  ```
  java version "21" 2023-09-19 LTS
  ```

# **2. Object-Oriented Programming (OOP) in Java**

## **2.1 What is OOP?**

OOP is a programming paradigm that organizes code into **objects** that interact with each other. Java follows four primary OOP principles:

1. **Encapsulation** – Hiding the internal implementation of an object and only exposing necessary details.
2. **Inheritance** – Enabling a class to inherit properties and behaviors from another class.
3. **Polymorphism** – Allowing objects to take multiple forms through method overriding and method overloading.
4. **Abstraction** – Hiding implementation details and exposing only necessary functionalities.

## **2.2 OOP Concepts in Detail**

### **Encapsulation (Data Hiding)**

Encapsulation restricts direct access to data members and allows controlled access through getter and setter methods.

```java
class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### **Inheritance (Reusability)**

Inheritance allows a child class to inherit the properties and methods of a parent class.

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

### **Polymorphism (Method Overriding & Overloading)**

Polymorphism allows methods to have multiple implementations.

#### **Method Overloading (Compile-time Polymorphism)**

```java
class MathOperations {
    int add(int a, int b) {
        return a + b;
    }
    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

#### **Method Overriding (Runtime Polymorphism)**

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}
```

### **Abstraction (Hiding Implementation Details)**

Abstraction can be achieved using **abstract classes** or **interfaces**.

#### **Abstract Class Example:**

```java
abstract class Vehicle {
    abstract void start();
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with key ignition");
    }
}
```

#### **Interface Example:**

```java
interface Animal {
    void makeSound();
}

class Cat implements Animal {
    public void makeSound() {
        System.out.println("Meow Meow");
    }
}
```
# **Java Collections Framework (JCF)**
The Java Collections Framework (JCF) is a **hierarchical architecture** for handling a group of objects efficiently. It provides several interfaces and classes to store, manipulate, and retrieve data.

## **Key Features of Collections**
- **Dynamic Storage**: Unlike arrays, collections can grow or shrink dynamically.
- **Performance Optimization**: Collections are optimized for searching, sorting, and modifying data.
- **Standardized APIs**: Unified interfaces provide easy-to-use methods across different collection types.

---

## **1. Collection Interfaces and Classes**
The Java Collections Framework has **four major interfaces**:
1. **List** (Ordered Collection, allows duplicates)
2. **Set** (Unique Elements, unordered)
3. **Queue** (FIFO ordering, used for scheduling tasks)
4. **Map** (Key-Value pairs, no duplicate keys)

---

## **2. List Interface** (Ordered Collection, Allows Duplicates)
A **List** stores ordered elements and allows duplicates. It supports **index-based access** and **insertion order is preserved**.

### **Popular Implementations of List:**
| Class        | Features |
|-------------|----------|
| **ArrayList** | Resizable array, fast random access (O(1) lookup), slow insertion/deletion |
| **LinkedList** | Doubly-linked list, fast insertion/deletion (O(1)), slower random access (O(n)) |
| **Vector** | Synchronized version of ArrayList (legacy class) |
| **Stack** | Last-In-First-Out (LIFO) stack implementation |

### **Example: ArrayList**
```java
import java.util.ArrayList;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Mango");

        System.out.println(fruits);  // Output: [Apple, Banana, Mango]
    }
}
```

---

## **3. Set Interface** (No Duplicates, Unordered)
A **Set** stores **unique elements** and does not allow duplicates.

### **Popular Implementations of Set:**
| Class        | Features |
|-------------|----------|
| **HashSet** | Unordered, based on HashMap (O(1) lookup) |
| **LinkedHashSet** | Maintains insertion order |
| **TreeSet** | Sorted set based on a Red-Black Tree (O(log n) lookup) |

### **Example: HashSet**
```java
import java.util.HashSet;
import java.util.Set;

public class SetExample {
    public static void main(String[] args) {
        Set<String> names = new HashSet<>();
        names.add("Alice");
        names.add("Bob");
        names.add("Alice");  // Duplicate, will be ignored

        System.out.println(names);  // Output: [Alice, Bob] (order may vary)
    }
}
```

---

## **4. Queue Interface** (FIFO Structure)
A **Queue** follows the **First-In-First-Out (FIFO)** principle.

### **Popular Implementations of Queue:**
| Class        | Features |
|-------------|----------|
| **LinkedList** | Implements Queue and Deque, supports FIFO/LIFO |
| **PriorityQueue** | Maintains elements based on priority |

### **Example: PriorityQueue**
```java
import java.util.PriorityQueue;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<Integer> pq = new PriorityQueue<>();
        pq.add(30);
        pq.add(10);
        pq.add(20);

        while (!pq.isEmpty()) {
            System.out.println(pq.poll());  // Output: 10, 20, 30 (sorted order)
        }
    }
}
```

---

## **5. Map Interface** (Key-Value Pair Collection)
A **Map** stores data in **key-value pairs**, where keys are unique.

### **Popular Implementations of Map:**
| Class        | Features |
|-------------|----------|
| **HashMap** | Fast access (O(1)), unordered, allows one null key |
| **LinkedHashMap** | Maintains insertion order |
| **TreeMap** | Sorted keys based on Red-Black Tree (O(log n) lookup) |

### **Example: HashMap**
```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        Map<Integer, String> students = new HashMap<>();
        students.put(101, "Alice");
        students.put(102, "Bob");

        System.out.println(students.get(101));  // Output: Alice
    }
}
```

---

## **6. Stack (LIFO Data Structure)**
A **Stack** follows the **Last-In-First-Out (LIFO)** principle.

### **Example: Stack**
```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println(stack.pop());  // Output: 30 (Last element removed first)
    }
}
```

---

## **7. Comparison of Collections**
| Collection Type | Ordering | Allows Duplicates | Performance |
|----------------|----------|-------------------|-------------|
| **ArrayList** | Maintains insertion order | ✅ | Fast random access, slow insert/delete |
| **LinkedList** | Maintains insertion order | ✅ | Fast insert/delete, slow random access |
| **HashSet** | Unordered | ❌ | Fast operations (O(1)) |
| **TreeSet** | Sorted | ❌ | O(log n) operations |
| **HashMap** | No order | ✅ (values) / ❌ (keys) | Fast access (O(1)) |

---

## **Conclusion**
- **Use `ArrayList`** when you need fast random access.
- **Use `LinkedList`** when frequent insertions/deletions are needed.
- **Use `HashSet`** when you need unique elements and don't care about order.
- **Use `TreeSet`** when you need sorted unique elements.
- **Use `HashMap`** when storing key-value pairs without ordering constraints.

---
### **8. Streams & Functional Programming**
- Introduced in **Java 8**, Streams allow processing data declaratively using functional programming.
- Supports operations like **map, filter, reduce**.

**Example:**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
System.out.println(squares); // Output: [1, 4, 9, 16, 25]
```

---

### **9. Java 21: Sequenced Collections**
- Java 21 introduces `SequencedCollection`, `SequencedSet`, and `SequencedMap`.
- These unify **List**, **Set**, and **Map** under a common interface.
- Supports **first()**, **last()**, **reversed()** methods.

**Example:**
```java
SequencedCollection<String> seqList = new ArrayList<>();
seqList.add("A");
seqList.add("B");
System.out.println(seqList.first());  // Output: A
System.out.println(seqList.last());   // Output: B
```

This enhancement improves **code clarity** and **reduces redundant logic** across different collection types.

---
### **Exception Handling in Java**

Exception handling in Java is a mechanism to **handle runtime errors** in a controlled manner to prevent abnormal termination of the program.

---

## **1. What is an Exception?**
An **exception** is an event that disrupts the normal flow of execution. It occurs during runtime due to **logical errors**, **invalid inputs**, or **hardware failures**.

### **Types of Exceptions:**
1. **Checked Exceptions** – Known at compile-time (e.g., `IOException`, `SQLException`).
2. **Unchecked Exceptions** – Occur at runtime (e.g., `NullPointerException`, `ArrayIndexOutOfBoundsException`).
3. **Errors** – Severe problems (e.g., `OutOfMemoryError`, `StackOverflowError`).

---

## **2. Try-Catch-Finally: Handling Exceptions**
The `try-catch-finally` block helps handle exceptions and maintain program execution.

```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // This causes ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero: " + e.getMessage());
        } finally {
            System.out.println("This will always execute.");
        }
    }
}
```

✔ **`try`**: Code that may throw an exception.  
✔ **`catch`**: Handles the exception.  
✔ **`finally`**: Code that always runs (e.g., closing resources).

---

## **3. Custom Exceptions**
You can define your own exceptions by extending the `Exception` class.

```java
class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}

public class CustomExceptionDemo {
    public static void main(String[] args) {
        try {
            throw new CustomException("Custom Exception Occurred");
        } catch (CustomException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

✔ Used for **business logic errors** or **custom validation rules**.

---

## **4. Java 21: Scoped Values (Alternative to Thread-Local Variables)**
Java 21 introduces **Scoped Values**, a safer alternative to `ThreadLocal`, optimizing memory usage in concurrent applications.

```java
import java.lang.ScopedValue;

public class ScopedValueExample {
    static final ScopedValue<String> USER = ScopedValue.newInstance();

    public static void main(String[] args) {
        ScopedValue.where(USER, "Admin").run(() -> {
            System.out.println("Current User: " + USER.get());
        });
    }
}
```

✔ **Thread-safe alternative** to `ThreadLocal`.  
✔ **Avoids memory leaks** and **reduces contention in multithreading**.

---
### **Explanation of Java 21+ Features**

Java 21 introduces several **enhancements and new features** that improve code readability, maintainability, and performance. Below is a detailed breakdown of the mentioned features:

---

### **1. Pattern Matching (Switch & Records)**
Pattern matching simplifies type checking and casting, making code more concise and readable.

#### **Pattern Matching in Switch**
Before Java 21, we had to use explicit type casting when using `instanceof`. With pattern matching, Java automatically casts the variable.

**Example (Before Java 21 - Without Pattern Matching):**
```java
void process(Object obj) {
    if (obj instanceof String) {
        String str = (String) obj;  // Explicit casting required
        System.out.println(str.toUpperCase());
    }
}
```

**Example (Java 21 - With Pattern Matching):**
```java
void process(Object obj) {
    if (obj instanceof String str) {  // No explicit casting needed
        System.out.println(str.toUpperCase());
    }
}
```
✔ **Reduces boilerplate code**  
✔ **Increases readability**

#### **Pattern Matching in Switch Statements**
The `switch` statement now supports **type-safe** pattern matching.

**Example:**
```java
static String process(Object obj) {
    return switch (obj) {
        case String s -> "String: " + s.toUpperCase();
        case Integer i -> "Integer: " + (i * 2);
        case null -> "Null Value";
        default -> "Unknown Type";
    };
}
```
✔ **More concise and readable switch cases**  
✔ **Automatic type inference**

---

### **2. String Templates (Interpolated Strings)**
Before Java 21, string concatenation was done using **+ operator** or **String.format()**. Java 21 introduces **String Templates**, making string manipulation easier.

**Example (Before Java 21 - Using `+` or `String.format`)**
```java
String name = "John";
int age = 30;
System.out.println("Hello, my name is " + name + " and I am " + age + " years old.");
```

**Example (Java 21 - Using String Templates)**
```java
String name = "John";
int age = 30;
String message = STR."Hello, my name is \{name} and I am \{age} years old.";
System.out.println(message);
```
✔ **Easier string formatting**  
✔ **Less error-prone syntax**

---

### **3. Unnamed Classes & Instance Main Methods**
Java 21 introduces **unnamed classes** and **simplified main methods** for small programs.

#### **Unnamed Classes**
Unnamed classes allow us to write **single-use classes** without defining a full-fledged class.

**Example (Before Java 21)**
```java
class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, Java 21!");
    }
}
```

**Example (Java 21 - Unnamed Class)**
```java
void main() {
    System.out.println("Hello, Java 21!");
}
```
✔ **Reduces boilerplate code for simple scripts**  
✔ **Ideal for testing and educational purposes**

---
**Happy Learning!**
