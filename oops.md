Src: W3school
### Class and Object in Programming

**Class**  
A class is a user-defined data type which defines its properties and its functions. It is the logical representation of the data. For example, **"Human being"** is a class. The body parts of a human being are its properties, and the actions performed by the body parts are known as functions. The class itself does not occupy any memory space until an object is instantiated. `Class have properties and function`.

**Object**  
An object is a run-time entity. It is an instance of the class. An object can represent a person, place, or any other item. It can operate on both data members (properties) and member functions (methods) of the class.
`Others person can be object like John,Ram, Kali`.

| **Aspect**               | **Description**                                                                                                      |
|--------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Class**                | Human being                                                                                                          |
| **Properties (Attributes)** | - **Height**: Represents the height of the human being (e.g., 6 feet) <br> - **Weight**: Represents the weight (e.g., 180 lbs) <br> - **Age**: Represents the age (e.g., 30 years) <br> - **Eye color**: Represents the color of eyes (e.g., brown) |
| **Functions (Methods)**   | - **Walk**: The action of walking <br> - **Talk**: The action of talking <br> - **Eat**: The action of eating <br> - **Sleep**: The action of sleeping |
| **Object**               | **John** (an individual instance of the class "Human being") <br> - Specific values for properties: <br> - **Height** = 6 feet <br> - **Weight** = 180 lbs <br> - **Age** = 30 years <br> - **Eye color** = Brown |

### Example:
```java
// Class representing a human with name and age attributes
class Human {
    // Attribute to store the name of the human
    String name;

    // Attribute to store the age of the human
    int age;

    // Method to print the details of the human (name and age)
    public void printDetails() {
        // Printing the name and age of the human
        System.out.println("Name: " + this.name + ", Age: " + this.age);
    }
}

public class OOPS {
    public static void main(String args[]) {
        // Creating a new Human object for the first person (Ram)
        // [Class Human] is the blueprint for creating objects with 'name' and 'age' attributes.
        // 'person1' is a reference variable that will hold the reference to a new Human object.
        // 'new Human()' creates a new instance (object) of the Human class, which is initialized with default values (name = null, age = 0).
        Human person1 = new Human();  // 'person1' is a reference to a new Human object

        // Assigning values to the properties of person1 (name and age)
        person1.name = "Ram";         // Assigning the name "Ram" to person1
        person1.age = 25;             // Assigning the age 25 to person1

        // Creating a new Human object for the second person (John)
        // Again, 'new Human()' creates another instance of the Human class and assigns it to the 'person2' reference.
        Human person2 = new Human();  // 'person2' is a reference to a new Human object

        // Assigning values to the properties of person2 (name and age)
        person2.name = "John";        // Assigning the name "John" to person2
        person2.age = 30;             // Assigning the age 30 to person2

        // Printing details of the first person (Ram)
        person1.printDetails();       // Calling the 'printDetails' method to print Ram's details

        // Printing details of the second person (John)
        person2.printDetails();       // Calling the 'printDetails' method to print John's details
    }
}

```
## The `this` Keyword in Object-Oriented Programming (OOP)

In Object-Oriented Programming (OOP), the `this` keyword refers to the current instance of the class, i.e., the object that the method or constructor is being called on. It has two main uses:

### 1. **Passing the Current Object as a Parameter**

You can use the `this` keyword to pass the current instance of the class as a parameter to another method or constructor.

- **`this` keyword**: Refers to the current instance of the class.
- **Passing the current object**: We pass `this` (the current `pen` object) to another method (`anotherMethod`), which accepts a `Pen` object.
- **Usage of `this`**: The `this` keyword is used here to explicitly refer to and pass the current object as a parameter to another method.

## Example Code
```java
public class Pen {
    public static void main(String[] args) {
        // Creating an instance of the Pen class (creating a Pen object)
        Pen pen = new Pen();
        
        // Calling the display method on the Pen object
        pen.display();
    }

    // Method that uses the current instance of the Pen class
    public void display() {
        // Using 'this' to refer to the current Pen object and pass it to anotherMethod
        // This demonstrates the use of the 'this' keyword to pass the current object as a parameter.
        anotherMethod(this);
    }

    // Method that accepts a Pen object as a parameter
    public void anotherMethod(Pen pen) {
        // Print out the Pen object passed to the method
        // By default, this will call the 'toString()' method of the Pen class
        System.out.println("Pen object passed: " + pen);
    }
}
```

### 2. **Referencing the Current Instance Variable**
When a class has instance variables (fields) and parameters or local variables with the same name, you can use the `this` keyword to refer specifically to the instance variables.
* `this` keyword: Refers to the current instance of the class.
* **Passing current object**: The `this` keyword is used to pass the current `Pen` object to the anotherMethod().
* **Referencing instance variables**: The `this` keyword is used to differentiate between instance variables and local variables or parameters that have the same name
## Example Code

```java
public class Pen {
    // Instance variable (field) of the class
    private String color;

    public Pen(String color) {
        // Constructor with a parameter named 'color'
        // Using 'this' to refer to the instance variable 'color'
        this.color = color; // Assigns the value of the parameter to the instance variable
    }

    public void display() {
        // Accessing the instance variable 'color'
        System.out.println("The color of the pen is: " + this.color);
    }

    public static void main(String[] args) {
        // Creating a Pen object and passing the color as an argument
        Pen pen = new Pen("Blue");
        // Calling the display method on the Pen object
        pen.display();
    }
}
```


# Constructors in Java

A **constructor** is a special method that is automatically invoked when an object is created. It is used to initialize the data members of new objects. 

- **Constructor name**: It must have the same name as the class or structure.
- **Return type**: Constructors don’t have a return type (not even `void`).
- **Invocation**: Constructors are called only once, at the time of object creation.

There are three types of constructors in Java:

## 1. Non-Parameterized Constructor

A **non-parameterized constructor** is a constructor that does not take any arguments. It is used when you want to create an object with default values. If you don't define a constructor, Java provides a default no-argument constructor.

### Example:
```java
class Student {
    String name;
    int age;

    // Non-parameterized constructor
    Student() {
        System.out.println("Constructor called");
        name = "Unknown";  // Assigning default values
        age = 0;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();  // Constructor is called here
    }
}
```

In this example, the constructor is called when Student s1 = new Student(); is executed. The constructor initializes the name and age fields to default values, and a message is printed.

2\. Parameterized Constructor
-----------------------------

A **parameterized constructor** allows you to pass values at the time of object creation. This is useful when you want to initialize an object with specific values provided by the user.

### Example:
```java
class Student {
    String name;
    int age;

    // Parameterized constructor
    Student(String name, int age) {
        this.name = name;  // 'this' is used to refer to instance variables
        this.age = age;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("John", 20);  // Constructor is called with arguments
        System.out.println("Name: " + s1.name + ", Age: " + s1.age);
    }
}
```

In this case, when `Student s1 = new Student("John", 20)`; is executed, the parameterized constructor is invoked. It sets the `name` to `"John"` and `age` to `20` for the `object s1`.

3\. Copy Constructor
--------------------

A **copy constructor** is used to create a new object by copying the values of an existing object. It is particularly useful when you need to create a new instance that is a copy of another instance. In Java, the copy constructor must be defined by the programmer since it is not provided by default (unlike in C++).

### Example:
```java
class Student {
    String name;
    int age;

    // Copy constructor
    Student(Student s2) {
        this.name = s2.name;
        this.age = s2.age;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("John", 20);  // Original object
        Student s2 = new Student(s1);  // Copy constructor called
        System.out.println("Name: " + s2.name + ", Age: " + s2.age);
    }
}
```
In this example, the copy constructor Student(Student s2) is used to create s2 as a copy of s1. The fields of s1 are copied to the new object s2.

Key Points:
-----------

*   **Non-Parameterized Constructor**: A constructor with no parameters, used to initialize an object with default values.
    
*   **Parameterized Constructor**: A constructor with parameters, used to initialize an object with specific values passed during object creation.
    
*   **Copy Constructor**: A constructor used to copy the state of one object into another.
    

Default Constructor (Implicit)
------------------------------

If you don't provide any constructors in a class, Java will implicitly provide a **default no-argument constructor**. However, if you provide any constructor (either parameterized or non-parameterized), the default constructor will **not** be automatically created unless explicitly defined.

### Example:
```java
class Student {
    String name;
    int age;
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();  // Default constructor provided by Java
        System.out.println("Name: " + s1.name + ", Age: " + s1.age);  // null, 0 (default values)
    }
}
```

In this case, the default constructor is provided by Java, initializing `name` to `null` and `age` to `0` as default values.


# Keyword Access Modifiers and Their Behavior in Java

| **Keyword**        | **Meaning**                                                                 | **What Happens If Omitted**                                                                 | **In Case of extends or implements**                                                                                           |
|--------------------|-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| **public**         | Makes a class, method, or field accessible from any other class.            | If omitted, defaults to **package-private** (only accessible within the same package).      | When extending or implementing, **public** methods in a superclass or interface can be overridden. A **public** method in a subclass is also accessible outside the package. |
| **private**        | Makes a field or method accessible only within the same class.               | If omitted, defaults to **package-private** (only accessible within the same package).      | Cannot be overridden or accessed in subclasses or implementing classes. Methods and fields remain **private** to the class.   |
| **protected**      | Makes a field or method accessible within the same package and by subclasses (even in different packages). | If omitted, defaults to **package-private** (accessible only within the same package).      | In a subclass, **protected** methods/fields can be accessed and overridden, even if the subclass is in a different package.   |
| **static**         | Means the method/field belongs to the class itself, not to any specific instance. | If omitted, the method/field becomes instance-based (must be called on an instance).       | **Static** methods/fields from a superclass can be accessed without creating an instance, but they cannot be overridden in subclasses. |
| **void**           | Indicates the method does not return a value.                               | If omitted, you must specify a return type, and the method must return a value of that type. | When overriding a method from a superclass, the return type must be compatible (or the same) as the original method. If **void** is omitted, you must provide a return type in both the superclass and subclass. |

1\. **Using `public` and `private` in inheritance:**
```java
class Superclass {
    public void publicMethod() {
        System.out.println("Public Method");
    }
    
    private void privateMethod() {
        System.out.println("Private Method");
    }
}

class Subclass extends Superclass {
    @Override
    public void publicMethod() {
        System.out.println("Overridden Public Method");
    }

    // The following would cause an error because `privateMethod` is private in the superclass
    // @Override
    // private void privateMethod() {
    //     System.out.println("Overridden Private Method");
    // }
}
```
* `publicMethod()` can be overridden in the subclass and is accessible outside of the package.
* `privateMethod()` cannot be overridden or accessed in the subclass because it's `private` to the superclass.

2\. **`Static` Method in Inheritance:**
```java
class Superclass {
    static void staticMethod() {
        System.out.println("Static Method in Superclass");
    }
}

class Subclass extends Superclass {
    // staticMethod() cannot be overridden, but can be accessed like this:
    // Superclass.staticMethod();
}
```
* **Static methods** in the superclass are inherited but **cannot be overridden**. They can be accessed directly from the class (e.g., **Superclass.staticMethod()**).

3\. **Using `protected` and `public` with extends/implements:**
```java
interface MyInterface {
    void interfaceMethod();
}

class Superclass {
    protected void protectedMethod() {
        System.out.println("Protected Method");
    }
}

class Subclass extends Superclass implements MyInterface {
    @Override
    public void interfaceMethod() {
        System.out.println("Implemented Method from Interface");
    }

    @Override
    protected void protectedMethod() {
        System.out.println("Overridden Protected Method");
    }
}
```
* `protectedMethod()` can be overridden in the subclass and is accessible to subclasses (even in different packages).
* `interfaceMethod()` from the interface is public by default and must be implemented as public in the subclass.

### Summary:

* **Inheritance** (`extends`): A subclass can access and override `public` and `protected` members of the superclass but cannot access `private` members.
* **Implementation** (`implements`): Methods from an interface must be implemented with `public` visibility. The subclass or implementing class must provide a compatible return type and can override methods from the superclass or interface.

# Polymorphism in Object-Oriented Programming (OOP)

Polymorphism is the ability to present the same interface for differing underlying forms (data types). With polymorphism, each of these classes will have different underlying data. Precisely, **Poly** means 'many' and **morphism** means 'forms'. 

Polymorphism allows a method or an object to take on many forms, which enables more flexible and reusable code.

## Types of Polymorphism
`Polymorphism` is the ability to present the same interface for differing underlying forms (data types). With `polymorphism`, each of these classes will have different underlying data. 

* **Poly** means `‘many’` and
* **morphism** means `‘forms’`. 

There are two main types of polymorphism in OOP:
1. **Compile-Time Polymorphism (Static Polymorphism)**
2. **Runtime Polymorphism (Dynamic Polymorphism)**

Let's understand them in detail:

---

## 1. Compile-Time Polymorphism (Static Polymorphism)

**Compile-time polymorphism** is resolved at the time of compilation. This means the method to be invoked is determined during the compile phase, and no decision is made at runtime. **Method Overloading** is a common example of compile-time polymorphism.

### Method Overloading:

Method overloading occurs when a class has multiple methods with the **same name** but **different parameter lists**. Overloading can be based on:
- **Number of parameters** passed to the method.
- **Type of parameters** passed to the method.

The Java compiler determines which version of the overloaded method to call based on the method signature during compilation.

### Example:

```java
class Student {
    String name;
    int age;
    
    // Overloaded method with a single String parameter
    public void displayInfo(String name) {
        System.out.println("Name: " + name);
    }

    // Overloaded method with a single int parameter
    public void displayInfo(int age) {
        System.out.println("Age: " + age);
    }

    // Overloaded method with both String and int parameters
    public void displayInfo(String name, int age) {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student student = new Student();
        student.displayInfo("Alice");        // Calls displayInfo(String name)
        student.displayInfo(25);             // Calls displayInfo(int age)
        student.displayInfo("Alice", 25);    // Calls displayInfo(String name, int age)
    }
}
```
In the above example, the method `displayInfo` is overloaded in the `Student` class, and the compiler decides which version to call based on the arguments passed.

# 2. Runtime Polymorphism (Dynamic Polymorphism)

Runtime polymorphism, also called dynamic polymorphism, is resolved at runtime. This type of polymorphism occurs when a subclass overrides a method defined in the parent class. The specific method to call is determined at runtime based on the object type, not the reference type.

In Java, method overriding is the way to achieve runtime polymorphism. The method signature in the child class matches the method in the parent class, but the method's implementation in the child class may differ.

### Method Overriding

Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its superclass. Even though both the parent and child class have the same method signature, the method that gets called depends on the actual object at runtime.

### Example:

```java
class Shape {
    // Parent class method
    public void area() {
        System.out.println("Displays Area of Shape");
    }
}

class Triangle extends Shape {
    // Method overriding in subclass
    public void area(int h, int b) {
        System.out.println("Area of Triangle: " + (0.5 * b * h));
    }
}

class Circle extends Shape {
    // Method overriding in subclass
    public void area(int r) {
        System.out.println("Area of Circle: " + (3.14 * r * r));
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape1 = new Triangle();
        shape1.area(); // Runtime polymorphism: Calls overridden method in Triangle
        
        Shape shape2 = new Circle();
        shape2.area(); // Runtime polymorphism: Calls overridden method in Circle
    }
}
```
In the above example:
- `Shape` is the parent class with a method `area()`.
- `Triangle` and `Circle` are subclasses that override the `area()` method, but each class has its own implementation.
- Even though `shape1` and `shape2` are references of type `Shape`, they hold objects of type `Triangle` and `Circle` respectively. 
- Therefore, the method call `shape1.area()` and `shape2.area()` will invoke the overridden methods in `Triangle` and `Circle` at runtime.

---

### Key Differences Between Compile-Time and Runtime Polymorphism

| Aspect                | Compile-Time Polymorphism   | Runtime Polymorphism        |
|-----------------------|-----------------------------|-----------------------------|
| **Resolution Time**    | Resolved at compile time    | Resolved at runtime         |
| **Method Overloading** | Yes                         | No                          |
| **Method Overriding**  | No                          | Yes                         |
| **Binding**            | Early binding (static binding) | Late binding (dynamic binding) |
| **Example**            | Method Overloading          | Method Overriding           |
| **Flexibility**        | Less flexible (fixed method resolution) | More flexible (decided at runtime) |

### **Java: Encapsulation**

**Definition:**
Encapsulation is the process of wrapping data (attributes) and methods (functions) that operate on the data into a single unit called a **class**. It ensures that the data is accessed and modified only through specific methods (getters and setters), rather than directly. This is a core principle of **Object-Oriented Programming (OOP)**, which promotes **data hiding** and **modular design**.

---

### **Key Concepts:**

1. **Data Hiding**:  
   Encapsulation allows for **data hiding**, which means the internal state of an object is not accessible directly from outside the class. Instead, the data can only be accessed or modified through defined methods, enhancing security and reducing the risk of unintended changes.

2. **Private Members**:  
   In Java, the attributes (fields) of a class are usually declared as **private**, making them inaccessible from outside the class. This protects the integrity of the data by preventing unauthorized modifications.

3. **Getter and Setter Methods**:  
   To access or modify private attributes, **getter** and **setter** methods are used. The getter method allows you to retrieve the value of an attribute, while the setter method allows you to modify its value.

4. **Access Control Modifiers**:  
   - **private**: Restricts access to the members of the class within the same class.
   - **public**: Allows access to the members from outside the class.
   - **protected**: Allows access within the same package and subclasses.
   - **default** (no modifier): Restricts access within the same package.

---

### **Example of Encapsulation in Java:**
file: Person.java
```java
public class Person {
    // Private attributes
    private String name;
    private int age;

    // Getter method for 'name'
    public String getName() {
        return name;
    }

    // Setter method for 'name'
    public void setName(String name) {
        this.name = name;
    }

    // Getter method for 'age'
    public int getAge() {
        return age;
    }

    // Setter method for 'age'
    public void setAge(int age) {
        if(age > 0) {  // Adding a check to ensure valid data
            this.age = age;
        } else {
            System.out.println("Age must be positive.");
        }
    }
}
```
file: Main.java
```java
public class Main {
    public static void main(String[] args) {
        Person person = new Person();
        
        // Using setter methods to set data
        person.setName("Alice");
        person.setAge(30);
        
        // Using getter methods to retrieve data
        System.out.println("Name: " + person.getName()); // Name: Alice
        System.out.println("Age: " + person.getAge()); // Age: 30
        
        // Attempting to set invalid data
        person.setAge(-5);  // This will not change the age due to validation
    }
}

```
# Benefits of Encapsulation

### 1. Data Protection
By restricting direct access to data, encapsulation ensures that the object's state cannot be altered in an unpredictable or harmful way.

### 2. Maintainability
Changes in the internal implementation of the class (e.g., how the data is stored) can be made without affecting other parts of the code that use the class, as long as the public interface (getters and setters) remains unchanged.

### 3. Flexibility and Control
You can control the values of the attributes by adding validation or processing logic in the setter methods, ensuring that only valid data is assigned.

### 4. Improved Security
Sensitive information (e.g., passwords) can be hidden and accessed in a controlled manner, improving security.

### 5. Code Readability and Reusability
Encapsulation promotes the use of clean, reusable code with well-defined interfaces for interacting with data.

**Real-world Example**:
`Bank Account:`
In a banking application, you would encapsulate the account balance by making it a private variable. You could then provide getter and setter methods to allow controlled access to the balance, for example, ensuring that withdrawals cannot exceed the available balance.

# Java Abstraction

**Abstraction** is the concept of hiding the complex implementation details and showing only the essential features of an object. It helps simplify real-world problems by focusing on the relevant details and ignoring unnecessary information.

### Key Points:
- **Modeling Real-World Problems**: Abstraction allows us to create an **abstract model** of a real-life problem, capturing only the important details.
- **Reducing Complexity**: By **showing only essential parts** and hiding irrelevant details, it reduces complexity.
- **Standard Solution**: It provides a **generalized solution** for problems with similar properties.
  
### **Definition**:
Abstraction is achieved by defining the **properties** of a problem, and the **data** and **operations** that affect the model. It simplifies the solutions to complex real-world issues by focusing on the essential aspects and ignoring irrelevant ones.

---

### Data Binding:
**Data Binding** is a process of linking the application's **UI (User Interface)** with the **business logic**. Any changes made in the business logic will automatically reflect in the UI, ensuring synchronization between them.

---

### Ways to Achieve Abstraction in Java:
1. **Abstract Class**
2. **Interface (Pure Abstraction)**

---

### 1. **Abstract Class**

An **abstract class** is a class that cannot be instantiated on its own and may contain both **abstract** (unimplemented) methods and **concrete** (implemented) methods. It serves as a **blueprint** for other classes.

#### **Features of an Abstract Class**:
- **Declared using the `abstract` keyword**.
- Can contain both **abstract** and **non-abstract (concrete)** methods.
- **Cannot be instantiated** directly.
- Can have **constructors**, **static methods**, and **final methods**.
- Can have **final methods**, which **cannot be overridden** in subclasses.

#### **Example of an Abstract Class**:

```java
abstract class Animal {
   // Abstract method (no implementation)
   abstract void walk();

   // Non-abstract method (with implementation)
   void breathe() {
       System.out.println("This animal breathes air");
   }

   // Constructor
   Animal() {
       System.out.println("You are about to create an Animal.");
   }
}

class Horse extends Animal {
   Horse() {
       System.out.println("Wow, you have created a Horse!");
   }

   // Implementing the abstract method
   void walk() {
       System.out.println("Horse walks on 4 legs");
   }
}

class Chicken extends Animal {
   Chicken() {
       System.out.println("Wow, you have created a Chicken!");
   }

   // Implementing the abstract method
   void walk() {
       System.out.println("Chicken walks on 2 legs");
   }
}

public class OOPS {
   public static void main(String args[]) {
      Horse horse = new Horse(); // Creating an object of Horse
      horse.walk();  // Calls the walk method of Horse
      horse.breathe();  // Calls the breathe method of Animal
   }
}
```
**Output:**
```
You are about to create an Animal.
Wow, you have created a Horse!
Horse walks on 4 legs
This animal breathes air
```

# 2. Interfaces (Pure Abstraction)

An interface represents pure abstraction. It contains only method declarations without any implementation. A class that implements an interface must provide the implementation for all the methods defined in the interface.

## Features of Interfaces:
- All fields are `public`, `static`, and `final` by default.
- All methods are `public` and `abstract` by default.
- A class that implements an interface must implement all the methods declared in the interface.
- Supports multiple inheritance, allowing a class to implement more than one interface.

## Example of an Interface:

```java
interface Animal {
   // Abstract method (no implementation)
   void walk();
}

class Horse implements Animal {
   // Implementing the abstract method
   public void walk() {
       System.out.println("Horse walks on 4 legs");
   }
}

class Chicken implements Animal {
   // Implementing the abstract method
   public void walk() {
       System.out.println("Chicken walks on 2 legs");
   }
}

public class OOPS {
   public static void main(String args[]) {
      Horse horse = new Horse(); // Creating an object of Horse
      horse.walk();  // Calls the walk method of Horse
   }
}
```
`Output:`
```
Horse walks on 4 legs
```

# Differences Between Abstract Class and Interface

| Feature                | Abstract Class                              | Interface                                    |
|------------------------|---------------------------------------------|----------------------------------------------|
| **Abstract Methods**    | Can have both abstract and concrete methods | All methods are abstract by default          |
| **Instance Creation**   | Cannot instantiate directly                 | Cannot instantiate directly                  |
| **Multiple Inheritance**| Not supported                               | Supports multiple inheritance                |
| **Fields**              | Can have instance variables                 | All fields are public, static, and final by default |
| **Method Implementation**| Can have both abstract and concrete methods | All methods are abstract by default          |
| **Constructors**        | Can have constructors                       | Cannot have constructors                     |
| **Access Modifiers**    | Can have different access modifiers         | All methods are public by default            |

**Fields** refer to the variables or data members that are declared within a class or interface.

**Interface Fields**: All fields are **implicitly public**, **static**, and **final** by default.

**Abstract Class Fields:**
- Fields can be instance variables or static variables.
- Fields can have different access modifiers: private, protected, or public.

# Static Members in Java

### Static Variables
- Shared among all instances of the class.
- They are initialized only once when the class is loaded into memory.

### Static Methods
- Can be called without creating an object of the class.
- Can only access other static members of the class.

### Static Block
- Used for initializing static variables or performing one-time setup when the class is loaded.

### Static Nested Class
- Can be instantiated without an outer class object.
- Can access static members of the outer class.
```java
// Static Variables
static <data_type> <variable_name>;
static int count;  // Example: static variable of type int

// Static Methods
static <return_type> <method_name>(<parameters>);
static void display() {  // Example: static method with void return type
    System.out.println("Hello, World!");
}

// Static Block
static {
    count = 10;  // Example: Static block to initialize static variables
    System.out.println("Static block executed.");
}

// Static Nested Class
static class <NestedClassName> {
    // Nested class content
}
static class InnerClass {  // Example: static nested class
    void printMessage() {
        System.out.println("This is a static nested class.");
    }
}

```

# Understanding `implements` in Java

In Java, the `implements` keyword is used to indicate that a class is **implementing an interface**. An interface in Java is a reference type, similar to a class, but it has specific characteristics and rules.

### Key Points about `implements` and Interfaces:

## 1. Interface in Java

- An **interface** is a **reference type** in Java, similar to a class, but with specific differences:
  - It cannot have **instance fields** (i.e., it cannot hold data specific to an object instance).
  - It can only declare **method signatures** (method names and parameters, but without implementations).
  - It can define **constants** (public static final variables).
  - It can have **default methods** (methods with a body, introduced in Java 8).
  - It can have **static methods**.
  - It can also include **nested types** (like nested interfaces or enums).

An interface provides a **contract**, defining **what methods a class should implement** without dictating **how the methods should be implemented**.

```java
interface Animal {
    void eat();  // Method signature, no body
    void sleep(); // Method signature, no body
}
```
# Using the `implements` Keyword in Java

## 2. When a Class Uses the `implements` Keyword
When a class uses the `implements` keyword, it means that the class is agreeing to implement all the methods declared in the interface. The class must provide method implementations for every abstract method in the interface, unless the class is abstract.

```java
class Dog implements Animal {
    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }

    @Override
    public void sleep() {
        System.out.println("Dog is sleeping");
    }
}
```

**Method Signatures:**
An interface can only define abstract methods (methods without a body) or default methods (methods with a body).
```java
interface Animal {
    void eat();  // Abstract method (no body)
}
```
Or with a default method:
```java
interface Animal {
    default void breathe() {
        System.out.println("Breathing...");
    }
}
```
**Constants**:
An interface can contain constants (variables that are implicitly `public static final`).
```java
interface Animal {
    int MAX_AGE = 100;  // constant (implicitly public static final)
}
```
# Why Use `implements` in Java?

The keyword `implements` is used in Java when a class wants to adopt the behavior defined by an interface. The use of `implements` enables a class to follow a behavior contract specified by the interface. Here are key reasons for using `implements` in Java:

## 1. Behavior Contract

- **Interface as a Contract**: An interface in Java defines a contract or a blueprint for classes. It specifies a set of methods that a class must implement.
- **Ensures Consistency**: Any class that implements the interface is required to provide its own implementation for all the methods declared in the interface, ensuring consistency and predictable behavior.

## 2. Decoupling Code

- **Separation of Concerns**: Using interfaces helps separate the definition of behavior from the implementation. This allows you to change the implementation without affecting the code that uses the interface, promoting flexibility and maintainability.
- **Code Reusability**: Since multiple classes can implement the same interface, code that uses the interface can work with any class that implements it, providing reusability and scalability.

## 3. Polymorphism

- **Dynamic Behavior**: Polymorphism allows objects of different classes to be treated as instances of the same interface type. This means you can write code that operates on interface types, enabling it to work with any class that implements the interface.
- **Flexible Code Design**: Using interfaces with `implements` allows the creation of flexible and extendable code that can work with different types of objects without knowing their specific class types.

## Define Behavior Contracts

A **Behavior Contract** is a concept where an interface defines a set of methods (or actions) that must be implemented by any class that claims to follow the contract.

### What it Implies:
- The class promises to provide specific implementations for the methods declared in the interface.
- It guarantees that any object of the class will have the defined behavior, ensuring that certain operations can be performed in a predictable way.

### Purpose:
- **Standardization**: Interfaces provide a standardized way to define behavior across different classes.
- **Abstraction**: They allow the definition of behavior without needing to specify how it’s carried out (the implementation). The implementation is left to the classes that implement the interface.
- **Loose Coupling**: Code that uses the interface does not need to be concerned with the specific details of the class. It can rely on the methods defined in the interface to function, making the code loosely coupled and easier to maintain.

## Example of Interface as a Behavior Contract

```java
interface Animal {
    void eat();
    void sleep();
}

class Dog implements Animal {
    public void eat() {
        System.out.println("Dog is eating.");
    }

    public void sleep() {
        System.out.println("Dog is sleeping.");
    }
}

class Cat implements Animal {
    public void eat() {
        System.out.println("Cat is eating.");
    }

    public void sleep() {
        System.out.println("Cat is sleeping.");
    }
}
```
# Interface and Class Example

In this example:

- The `Animal` interface defines a behavior contract with the methods `eat()` and `sleep()`.
- The `Dog` and `Cat` classes implement the `Animal` interface, ensuring they provide their own implementations for the methods specified in the contract.



## W3SCHOOL

### 1. **Class:** 
A Class is like an object constructor, or a `"blueprint"` for creating objects.
For example: in real life, a car is an **object**. The car has **attributes**, such as weight and color, and methods, such as drive and brake.

* To create a class, use the keyword **class**:

### 2. **Using Multiple Classes:** 
You can also create an `object` of a `class` and access it in another `class`.

1. **Main.java**
The `Main` class has an integer field `x`, which is initialized with the value `5`.
```java
public class Main {
  int x = 5;  // Field x is initialized to 5
}
```
2. **Second.java**
The `Second` class contains the `main` method, which is the entry point for running the Java program
```java
class Second {
  public static void main(String[] args) {
    Main myObj = new Main();  // Creates a new object of type Main
    System.out.println(myObj.x);  // Accesses the field x of myObj and prints it
  }
}
```
3. **Object Creation:**
The line `Main myObj = new Main();` creates a new object of the Main class. <span style="color:orange;">The field `x` of this object is automatically set to 5, as specified in the class definition.</span>
Thus, `myObj.x` refers to the value of `x` within the `myObj` object, which is `5`.

### 3. Accessing Attributes
You can access attributes by creating an `object` of the class, and by using the dot syntax (.). Like above access value of x (attribute) by `System.out.println(myObj.x)`.

**Modify Attributes**:
* Can modify attributes value.
* Can also override attribute values.
* Can't override existing values, if the attribute as  <span style="color:orange;">final.</span>. If try to overide it will generate an error: cannot assign to a final value.

Note:



* <span style="color:orange;">The final keyword is useful when you want a variable to always store the same value, like PI (3.14159...).</span>

* <span style="color:orange;"> The final keyword is called a "modifier". You will learn more about these in the Java Modifiers Chapter. </span>


### 4. Java Class Methods
* To call a method, write the method's name followed by two parentheses () and a semicolon; Call method inside main method `public static void main(String[] args) {..}`.

### Static vs Public Methods:

1. **Static Method**: A `static` method belongs to the class, so it can be called without creating an object of the class. Static method called from the same class only. For example, a `static` method can be accessed using `ClassName.methodName()` or `methodName()`.

2. **Public**: A `public` method can be accessed from anywhere, but requires an object to be called unless it is static. For example, a `public` method can be accessed after creating an object to call the public method.
` MyClass obj = new MyClass(); obj.publicMethod();`

### 5. Java Constructors
* A `constructor` in Java is a special method that is used to `initialize objects`.
* The `constructor` is called when an `object` of a class is created. 
* It can be used to set initial values for object attributes.


<span style="color:orange;"> **Remember that:** </span>

1. **Constructor Name**: The constructor name must exactly match the class name.
2. **No Return Type**: A constructor does not have a return type, not even `void`.
3. **Constructor Invocation**: The constructor is called automatically when an object of the class is created.
4. **Default Constructor**: If you don’t provide a constructor, Java provides a default constructor. Java provides a `no-argument constructor` that initializes the object with default values. A `no-argument constructor` is a constructor that takes no parameters and assigns default values to the object's attributes.

5. **Initial Values**: Without a custom constructor, you cannot set initial values for the object's attributes.
6. **Constructor Parameters**: Constructors can also take parameters, which are used to initialize object attributes with specific values.
7. **No Default Parameters for Constructors**:  
   Constructors cannot have default parameters like in some other programming languages. Each parameter must be explicitly passed when calling the constructor.
8. **Constructor Overloading**:  
   You can create multiple constructors with different parameters (constructor overloading) to allow initializing the object in different ways.

### 6. Modifiers (Access Modifiers and Non-Access Modifiers)

| **Feature**            | **Access Modifiers**                                                                                   | **Non-Access Modifiers**                                                                                       |
|------------------------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| **Definition**          | **Keywords** that control **visibility/access** to **classes, methods, and variables**.                             | **Keywords** that modify the **behavior, properties, or characteristics** of **classes, methods, and variables**.          |
| **Purpose**             | Control **access or visibility** of **members** (variables, methods, etc.).                                      | Modify the **behavior, attributes, or characteristics** of **methods and variables**.                                  |
| **Examples**            | **public, private, protected, default (package-private)**                                                   | **static, final, abstract, synchronized, volatile, transient, native**                                           |
| **Usage**               | To restrict or allow **access** between **classes, methods, or packages**.                                       | To define **properties** like **immutability (final)**, **behavior** like **thread synchronization (synchronized)**, and more. |
| **Scope of Effect**     | Affects **visibility and access control**, i.e., determining **who can access what**.                           | Affects the **behavior** of the **class or method**, such as **thread safety**, **inheritance constraints**, or **method implementation**. |
| **Inheritance Impact**  | Controls **access** in inheritance, allowing or restricting the subclass's ability to **access or override members**. | Influences whether a **method** can be **overridden** (e.g., **final**), whether a **class** can be **inherited** (e.g., **final**), or how methods behave (e.g., **abstract**). |


#### 6.1. Access Modifiers (Controls Access Level)

1. **public:** The class or member is accessible by any other class.  
   In Java, the `public` modifier allows access to the class or member from any other class, regardless of the package.  

2. **default:** The class or member is only accessible by classes in the same package (used when no modifier is specified).  
   The `default` access modifier is applied when no access modifier is explicitly mentioned. It means the class or member is visible only within classes in the same package. For example, `Scanner scanner = new Scanner(System.in)` is accessible if in the same package.

For **attributes, methods, and constructors**:
1. **public:** The code is accessible for all classes.  
   This allows the attribute, method, or constructor to be accessed from any class, including those from different packages.

2. **private:** The code is only accessible within the declared class.  
   The `private` modifier restricts access, allowing only the class in which the code is defined to access the attribute, method, or constructor.

3. **default:** The code is only accessible in the same package (used when no modifier is specified).  
   When no access modifier is provided, this is the default level of access, meaning the member is accessible within the same package. For example, classes in the `java.util` package can access each other if they have default access.

4. **protected:** The code is accessible in the same package and subclasses.  
   `protected` allows access within the same package, as well as to subclasses (even if they are in different packages).

---

#### 6.2. Non-Access Modifiers (Does Not Control Access Level, Provides Other Functionality)

**Note:** Non-access modifiers apply to classes, attributes, and methods, but not constructors. Access modifiers are used for constructors as well.

For **classes**:
1. **final:** The class cannot be inherited by other classes.  
   A `final` class cannot be extended by other classes, meaning no subclass can be created.

2. **abstract:** The class cannot be used to create objects. It must be inherited from another class to be used.  
   An `abstract` class cannot be instantiated. It must be subclassed, and the subclass provides concrete implementations.

For **attributes and methods**:
1. **final:** Attributes and methods cannot be overridden/modified.  
   A `final` attribute or method cannot be changed once it has been assigned or defined. It prevents overriding or modifying.

2. **static:** Attributes and methods belong to the class, rather than to instances (objects).  
   A `static` attribute or method is shared among all instances of the class. It belongs to the class itself rather than an individual object.

3. **abstract:** Can only be used in an abstract class and can only be used on methods. The method does not have a body; for example `abstract void run()`;. the body is provided by a subclass(inherited from).  
   An `abstract` method is declared without an implementation. The subclass that inherits the class must provide the method body.

#### In table:
### Access Modifiers (Controls Access Level)

| **Access Modifier** | **Description**                                                                                           | **Applicable To**                                 |
|---------------------|-----------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| **public**          | The class or member is accessible by any other class, regardless of the package.                         | Classes, attributes, methods, constructors        |
| **default**         | The class or member is only accessible by classes in the same package (when no modifier is specified).    | Classes, attributes, methods, constructors        |
| **private**         | The class, attribute, method, or constructor is only accessible within the declared/ same class.               | Attributes, methods, constructors                 |
| **protected**       | The class, attribute, method, or constructor is accessible within the same package and subclasses.        | Attributes, methods, constructors                 |

---

### Non-Access Modifiers (Does Not Control Access Level, Provides Other Functionality)

| **Non-Access Modifier** | **Description**                                                                                              | **Applicable To**                                 |
|-------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| **final**               | For classes: The class cannot be inherited. For attributes and methods: Cannot be modified or overridden.     | Classes, attributes, methods                      |
| **abstract**            | For classes: The class cannot be instantiated, must be subclassed. For methods: Declared without implementation, implemented by subclass. | Classes (abstract class), methods                 |
| **static**              | The attribute or method belongs to the class, not to instances.                                              | Attributes, methods                               |

### 7. Java Packages
A package is a namespace used to organize classes and interfaces in a logical manner. 
- Packages group related classes, like folders in a file directory.
- They help avoid name conflicts, organizing code and improve code maintainability.

#### 7.1 Types of Packages

- **Built-in Packages**: Prewritten classes provided by the Java API.
  - Examples:
    - `java.util` (e.g., `Scanner`, `List`)
    - `java.io` (e.g., `File`, `BufferedReader`)
  
- **User-defined Packages**: Custom packages created by the user.

#### 7.2 Importing Classes/Packages

- **Single Class Import**: Import a specific class from a package.
  - Syntax: `import package.name.Class;`
  - Example: `import java.util.Scanner;`
  
- **Whole Package Import**: Import all classes from a package.
  - Syntax: `import package.name.*;`
  - Example: `import java.util.*;`

#### 7.3 Creating User-defined Packages

- Use the `package` keyword to define a custom package.
- Save Java files in an appropriate directory structure that reflects the package name.
- Example: for this folder structure: `/com/example/employeeCrud/MyClass.java` package name: `package com.example.employeeCrud;`



## OOPS

### 7. Encapsulation:
Encapsulation is the concept of hiding sensitive data within a class and providing controlled access to it.

**Private Class Variables:** Class variables/attributes should be declared as private to restrict direct access from outside the class.

**Public Getter and Setter Methods** To access or update private variables, public getter and setter methods are provided.
- **Getter method** returns the value of the private variable.
- **Setter method** assigns/ set a new value to the private variable.

**Naming Convention for Getters and Setters:**
- The getter and setter methods start with `get` and `set`, followed by the variable name with the first letter capitalized.

#### 7.1. Example of Encapsulation:
`Person.java`
```java
public class Person {
    private String name; // private = restricted access

    // Getter method
    public String getName() {
        return name;
    }

    // Setter method
    public void setName(String newName) {
        this.name = newName;
    }
}
```
#### 7.2. Accessing Private Variables:
Private variables cannot be accessed directly from outside the class. So, we have to create access it from setter or getter method.

`Main.java`
- Cannot access directly
```java
public class Main {
    public static void main(String[] args) {
        Person myObj = new Person();
        myObj.name = "John";  // error: name is private
        System.out.println(myObj.name); // error: name is private
    }
}
```
`Main.java`
- Can access using setter and getter method.
```java
public class Main {
    public static void main(String[] args) {
        Person myObj = new Person();
        myObj.setName("John"); // Set the value of the name variable
        System.out.println(myObj.getName()); // Outputs: "John"
    }
}
```

#### 7.3. Why Use Encapsulation?

- **Better Control**: Control how class attributes are accessed or modified.
- **Read-only or Write-only**: Make class attributes read-only (using only the getter) or write-only (using only the setter).
- **Flexibility**: The implementation can be modified without affecting other parts of the code.
- **Increased Security**: Sensitive data can be kept secure by restricting access to it directly.

### 8. Java Inheritance

Java `Inheritance` allows a class (subclass or child class) to inherit properties and behaviors (attributes and methods) from another class (superclass or parent class). This is one of the core features of Object-Oriented Programming (OOP) that supports code reusability and logical organization of code.

## Key Concepts

### Subclass (Child Class/ Car)
- A subclass inherits attributes and methods from a superclass.
- It can add its own properties and methods, or `override` the inherited methods.

### Superclass (Parent Class/ Vehicle)
- A superclass is the class from which other classes `inherit`.
- It contains shared `attributes` and `methods` that subclasses can use.

### The `extends` Keyword
- The `extends` keyword is used to create an `inheritance relationship` between a subclass and a superclass.
- Example: `class Car extends Vehicle` means the `Car` class inherits from the `Vehicle` class.

### 8.1. Access via Inheritance

- **Private members** of the superclass are **not accessible** in the subclass.
- **Protected members** are **accessible** within the subclass, even if it's in a different package.
- **Public members** are **accessible** both within and outside the subclass, regardless of the package.

### 8.2. Example of Inheritance
```java
class Vehicle {
  protected String brand = "Ford";  // Vehicle attribute
  public void honk() {             // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}
// class <Child class> extends <Parent>
class Car extends Vehicle {
  private String modelName = "Mustang"; // Car attribute
  public static void main(String[] args) {
    // Create a Car object
    Car myCar = new Car();

    // Call the honk() method from Vehicle class
    myCar.honk();

    // Display brand from Vehicle class and modelName from Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}
```

### 8.3. The `final` Keyword
In Java, the `final` keyword can be used to prevent inheritance.

- **Final Class**: If a class is marked as `final`, it cannot be subclassed.
- **Final Method**: A method declared as `final` cannot be overridden by subclasses.
```java
final class Vehicle {
  ...
}

class Car extends Vehicle {  // This will result in a compile-time error, error: cannot inherit from final Vehicle

  ...
}
```
## 9. Polymorphism Explained

**Polymorphism** comes from two Greek words: *poly* (meaning many) and *morph* (meaning form or shape). So, polymorphism literally means `"many forms."`

In Java and other object-oriented programming languages, `polymorphism` means that different classes (which are related through `inheritance`) can `implement` or `override` **methods** in different ways, even though they share the same method name.

### 9.1. How It Works

#### Inheritance:
- You have a **parent class** (also called a superclass) that provides common behavior (methods).
- **Child classes** (subclasses) inherit those methods/behaviour but can provide their own versions (overriding methods) to perform specific tasks differently.
- **Polymorphism** lets a method behave differently based on the `actual object type`, not the `reference type`.

### 9.3. Example: Animal Sound

You have a **parent class** called `Animal` with a method `animalSound()`.  
You then create subclasses such as `Pig`, `Dog`, `Cat`, etc. Each subclass overrides the `animalSound()` method to make its own unique sound.

```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}
```
Now, using polymorphism, you can treat all of them as `Animal` objects, even though each subclass has a different implementation of `animalSound()`:
```java
Animal myAnimal = new Animal();  // Animal object
Animal myPig = new Pig();        // Pig object
Animal myDog = new Dog();        // Dog object

myAnimal.animalSound();  // Calls the Animal version of animalSound
myPig.animalSound();     // Calls the Pig version of animalSound
myDog.animalSound();     // Calls the Dog version of animalSound
```
### 9.4. What Does This Mean?

The same method name (`animalSound()`) behaves differently depending on the object (`myAnimal`, `myPig`, `myDog`).

Even though all these objects are treated as **Animal** types, **polymorphism** allows the method to perform different tasks based on the specific class that calls it.

### 9.5. Why is Polymorphism is Useful?

**Code Reusability:**
You don't have to write separate code for each class to call the method; **polymorphism** allows you to reuse the same code and have it behave differently based on the object type.

**Flexibility:**
You can add more subclasses (like **Cat**, **Bird**, etc.) later without changing the existing code. The new subclasses can simply override the method in their own way, maintaining the flexibility of the program.

```java
class Cat extends Animal {
  public void animalSound() {
    System.out.println("The cat says: meow");
  }
}
```
### Why And When To Use "Inheritance" and "Polymorphism"?

- **Code Reusability**: Inheritance allows you to reuse `attributes` and `methods` of an existing class when creating a new class.

## 10. Abstraction in Java ( Using Abstract Class)
Use the `implements` keyword to associate a class with an interface.
<span style="color:orange;">Use the `extend` keyword to associate a subclass with an abstract class.</span>
**Abstraction** is a core concept in Object-Oriented Programming (OOP) that refers to hiding the implementation details and exposing only the essential features of an object. 

- The primary goal is to reduce complexity by focusing on high-level mechanisms while hiding the implementation details that are not necessary for the user.

- <span style="color:orange;">In Java, abstraction can be achieved using two way **abstract classes** and **interfaces**(pure interface).</span>

### 11.1. Abstract Class

- An **abstract class** is a class that cannot be instantiated directly. It is used to define common `properties` and `methods` that must be shared by its `subclasses`. 
- You <span style="color:orange;">cannot create an object of an abstract class</span>. 
- Instead, it must be inherited by another class that provides concrete implementations of the abstract methods.

An abstract class can have both: **Abstract methods** (methods without a body) and **Concrete methods** (methods with an implementation).

- **Abstract methods** in an abstract class must be implemented by its subclasses. This ensures that all subclasses provide their own specific implementations of these methods.
  
- **Concrete methods** can be inherited directly by subclasses, or they can be overridden if the subclass needs to customize or extend the behavior defined in the superclass.

**Syntax:**
```java
abstract class ClassName {
    // Abstract method (no body)
    public abstract void methodName();

    // Regular method (with body)
    public void regularMethod() {
        // Method body
    }
}
```
In object-oriented programming, an **abstract method** and a **concrete method** serve different purposes. In this example:

- **`methodName()`** is an **abstract method**. It does not have a body and must be implemented by a subclass. It serves as a blueprint for subclasses to follow.
  
- **`regularMethod()`** is a **concrete method**. It provides an actual implementation that can be inherited as-is by subclasses, or overridden if the subclass needs to modify or extend its behavior.

### 11.2. Abstract Method in Java 

An **abstract method** is a method declared in an `abstract class` that does not have an implementation (i.e., it has no method body). The actual implementation is provided by `subclasses` that `inherit` the `abstract class`. 

An `abstract method` forces `subclasses` to provide their own specific implementation.

**Syntax:**

```java
public abstract void methodName();
```
**Example:** Using Abstract Classes and Methods
Here’s an example of how to use an abstract class and abstract methods in Java:

```java

// Abstract class
abstract class Animal {
    // Abstract method (does not have a body)
    public abstract void animalSound();

    // Regular method (with body)
    public void sleep() {
        System.out.println("Zzz");
    }
}

// Subclass (inherits from Animal)
class Pig extends Animal {
    // Providing concrete implementation for the abstract method
    public void animalSound() {
        System.out.println("The pig says: wee wee");
    }
}

public class Main {
    public static void main(String[] args) {
        // Animal myObj = new Animal(); // will generate an error, because object cannot created with abstract class

        // Create an object of Pig (subclass)
        Pig myPig = new Pig();
        // Call the overridden method in Pig
        myPig.animalSound();  // Calls the method defined in Pig
        // Call the inherited method from Animal
        myPig.sleep();        // Calls the regular method from Animal
    }
}
```

Output:
```
The pig says: wee wee
```
On above we cannot create an object of the Animal class:
```
Animal myObj = new Animal(); // will generate an error
```
### 11.3. Flow of Abstraction:
```
+--------------------+       +--------------------+       +--------------------+
| Abstract Class     |       | Subclass           |       | Main Class         |
| (Animal)           |  ---->| (Pig)              |  ---->| (Main)             |
+--------------------+       +--------------------+       +--------------------+
| - abstract method  |       | - Implement method  |       | - Create object    |
|   animalSound()    |<------|   animalSound()     |<------|   Pig myPig = new  |
| - regular method   |       |                    |       |   Pig();           |
|   sleep()          |       +--------------------+       | - Call methods     |
+--------------------+                                     |   myPig.animalSound();|
                                                            |   myPig.sleep();     |
                                                            +--------------------+
```

### 11.3.1 Explained Flow details:

#### `Abstract Class (Animal)`/ Abstract Class Creation

An abstract class is created with:

- **Abstract Method:** `animalSound()` - This method lacks a body and must be overridden by subclasses.
- **Regular Method:** `sleep()` - This method has a full implementation, so subclasses inherit it directly.

**Key Points:**
- The abstract method does not have a body and must be implemented by any concrete subclass.
- The regular method is inherited as is by subclasses.

#### `Subclass (Pig)`/ Subclass Implementation

The subclass `Pig` extends the abstract class `Animal`.

- The subclass **must** provide a concrete implementation of the abstract method `animalSound()`, as it is abstract in the parent class.
- The regular method `sleep()` is inherited directly from the `Animal` class.

**Key Points:**
- Subclass `Pig` overrides the `animalSound()` method.
- Subclass inherits the `sleep()` method from the `Animal` class.

#### `Main Class (Main)`/ Object Creation in Main Class

In the main method:

- You **cannot** instantiate an object of the `Animal` class since it is abstract.
- Instead, an object of the concrete subclass `Pig` is created.

#### Method Calls:
- `myPig.animalSound()` - Calls the overridden method in `Pig`.
- `myPig.sleep()` - Calls the inherited method from `Animal`.

**Summary of the Flow**

1. **Abstract Class:** Defines abstract method(s) and regular methods.
2. **Subclass:** Provides concrete implementation of abstract method(s) and inherits regular methods.
3. **Main Class:** Creates an object of the subclass and calls both abstract and regular methods on it.

### 10.4. Summary of Benefits of Abstract Methods

- **Enforce Consistency**:  
  All subclasses must implement the abstract method, ensuring a consistent interface.

- **Design Clarity**:  
  Abstract methods provide a clear blueprint for how subclasses should behave, improving code organization and structure.

- **Polymorphism**:  
  Abstract methods allow polymorphic behavior, enabling objects of different subclasses to be treated uniformly.

- **Decoupling**:  
  By separating the interface from the implementation, abstract methods make code more flexible and easier to maintain.

- **Encourage Overriding**:  
  Abstract methods promote method overriding, allowing subclasses to define their specific behaviors.

- **Ease of Extension**:  
  New subclasses can be added without modifying existing code, promoting a more flexible, extensible system.

- **Testability**:  
  Abstract methods facilitate testing by allowing mock implementations of abstract classes.


## 10. Abstraction in Java ( Using interface)
An **interface** in Java is a powerful tool for achieving abstraction. It defines a contract that classes can implement, but it cannot be instantiated itself. Here are the important concepts related to interfaces:

<span style="color:orange;">Use the `implements` keyword to associate a subclass with an interface.</span>

### 11.1. **What is an Interface?**
   - An **interface** is a collection of method signatures with no implementation. 
   - Interfaces allow you to define methods that a class must implement, but they do not provide the implementation of those methods.
   - They are considered a "completely abstract class" and are used for grouping related methods.

### 11.2. **Creating an Interface**
   - You declare an interface using the `interface` keyword.
   - `Methods` inside an `interface` do not have a body (implementation).
   - Example:
     ```java
     interface Animal {
         void animalSound(); // Method signature, no body
         void sleep();       // Method signature, no body
     }
     ```

### 11.2.1. **Implementing an Interface**
   - A class that `implements` an interface must provide the implementation (body) for all methods declared in the interface.
   - Use the `implements` keyword to associate a class with an interface.
   - Example:
     ```java
     class Pig implements Animal {
         public void animalSound() {
             System.out.println("The pig says: wee wee");
         }
         public void sleep() {
             System.out.println("Zzz");
         }
     }
     ```

### 11.3. **Important Notes on Interfaces**
   - **Cannot Instantiate**: You cannot create an instance of an interface directly.
     ```java
     // This is not allowed
     Animal myAnimal = new Animal(); // Error!
     ```
   - **Interface Methods**: By default, methods in an interface are `public` and `abstract` (i.e., no implementation). They must be implemented in the class that implements the interface.
   - **Interface Fields**: All fields in an interface are implicitly `public`, `static`, and `final` (constants).
   - **No Constructors**: Interfaces cannot have constructors since they cannot be instantiated.
   - **Must Implement All Methods**: When a class implements an interface, it must provide a body for all the methods declared in that interface, unless the class is abstract.

### 11.4. **Why and When to Use Interfaces**
   - **Abstraction**: Interfaces allow you to hide the details of implementation and expose only essential methods.
   - **Multiple Inheritance**: Java does not support multiple inheritance of classes, but a class can implement multiple interfaces. This is useful when a class needs to exhibit behaviors defined in multiple interfaces.
   - **Flexibility**: Interfaces can be used to achieve a higher degree of flexibility and modularity in your programs.

### 11.5. **Example of Multiple Interfaces**
   - A class can implement multiple interfaces by separating them with commas.
   - Example:
```java
   interface FirstInterface {  // Define FirstInterface
    void myMethod();  // Declare method to be implemented by any class
}

interface SecondInterface {  // Define  SecondInterface
    void myOtherMethod();  // Declare method to be implemented by any class
}

class DemoClass implements FirstInterface, SecondInterface {  // DemoClass implements both interfaces
    // Implementing myMethod from FirstInterface
    public void myMethod() {  
        System.out.println("Some text.."); 
    }
    
    // Implementing myOtherMethod from SecondInterface
    public void myOtherMethod() {  
        System.out.println("Some other text...");  
    }
}

public class Main {
    public static void main(String[] args) {
        DemoClass obj = new DemoClass();  // Create an instance of DemoClass
        obj.myMethod();  // Call myMethod on obj
        obj.myOtherMethod();  // Call myOtherMethod on obj
    }
}

class Pig implements Animal {  // Pig class implements the Animal interface
    // Implementing animalSound from Animal interface
    public void animalSound() {  
        System.out.println("The pig says: wee wee");  
    }

    // Implementing sleep from Animal interface
    public void sleep() {  
        System.out.println("Zzz");  
    }
}
  
```
In this example, `DemoClass` implements both `FirstInterface` and `SecondInterface`, providing the implementation for all the methods from both interfaces.

### 11.6. Summary of Key Features of Interfaces:
- Cannot be instantiated.
- Methods must be implemented by the class using `implements`.
- Methods are by default `public` and `abstract`.
- Fields are by default `public`, `static`, and `final`.
- Can be used to achieve multiple inheritance by implementing multiple interfaces.
- Interface methods do not have a body - the body is provided by the "implement" class.
-  Interfaces is used to achieve *security* - hide certain details and only show the important details of an object (interface).

Interfaces in Java provide a flexible way to define common behaviors and enable multiple inheritance, which makes them a powerful abstraction tool.

## Java InnerClass (w3school)
1. Inner Class (Non-static Inner Class)
2. Private Inner Class
3. Static Inner Class
4. Access Outer Class from Inner Class

Example:
```java
class OuterClass {
  int x = 10;
  class InnerClass {
    int y = 5;
  }
}
// To access the inner class, create an object of the outer class, and then create an object of the inner class
```
**Notes:** Note: just like static attributes and methods, a static inner class does not have access to members of the outer class.

## 12. Enums in Java
An `enum` is a special class used to define a group of constants (unchangeable variables). Enums are typically used when you need to represent a fixed set of related constants.

### 12.1. Creating an Enum
* Use the `enum` keyword to define an enum, instead of `class` or `interface`.
* Constants in an enum are usually written in uppercase letters, separated by commas.
Example:
```java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
```
### 12.2. Accessing Enum Constants:
```
Level myVar = Level.MEDIUM;
```
### 12.3. Enum Inside a Class:
```
public class Main {
  enum Level {
    LOW,
    MEDIUM,
    HIGH
  }

  public static void main(String[] args) {
    Level myVar = Level.MEDIUM;
    System.out.println(myVar);
  }
}
// Output: MEDIUM
```
### 12.4. Looping Through Enum Constants
- Enums provide a `values()` method that returns an array of all enum constants, which can be useful for iterating through the constants in a loop.
```
for (Level myVar : Level.values()) {
  System.out.println(myVar);
}

// Output:
LOW
MEDIUM
HIGH
```

## 13. ArrayList:
- The `ArrayList` class is part of the `java.util` package.
- It is a resizable array that allows dynamic modification of the size (i.e., elements can be added or removed).

### 13.1. Comparison with Built-in Arrays:
- **Array:**
  - Fixed size.
  - To add or remove elements, you need to create a new array.
  
- **ArrayList:**
  - Resizable; elements can be added or removed dynamically.
  - Provides built-in methods for easier management of data.

### 13.2. Syntax for Creating an ArrayList:
Create an `ArrayList` object called `cars` that will store `strings`:
- **Declaration and Instantiation:**
```java
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object
```
### 13.3. Adding Items to an ArrayList
- Using `add()` Method: Adds an item at the end of the list.
```java
cars.add("Volvo");
cars.add("BMW");
cars.add("Ford");
cars.add("Mazda");
```
- Adding an Item at a `Specific Position`:

You can specify the index where you want to add an element.
```java
cars.add(0, "Mazda");  // Insert "Mazda" at the beginning (index 0)
```
### 13.3. Access Items in an ArrayList
Using `get()` Method: Access elements by specifying the index.
```java
String car = cars.get(0);  // Access the first element (index 0)
```

### 13.4. Comparison of **Array** and **ArrayList** in Java

| **Feature**            | **Array**                                  | **ArrayList**                           |
|------------------------|--------------------------------------------|-----------------------------------------|
| **Syntax**             | `dataType[] arrayName = new dataType[size];` | `ArrayList<dataType> listName = new ArrayList<>();` |
| **Type**               | Can store both primitive types (e.g., `int`, `char`) and reference types. | Can only store reference types (e.g., `Integer`, `String`). |
| **Accessing Elements** | `arrayName[index]`                        | `listName.get(index)`                   |
| **Methods**            | Limited methods (e.g., `length`)            | Rich set of methods: <br> `add()`, `remove()`, `get()`, `set()`, `size()`, `clear()` |
| **Size**               | Fixed size, defined at the time of creation. | Dynamic size, can grow or shrink with `size()` method. |


# Comparison of **List** and **ArrayList** in Java

# Comparison of **List** and **ArrayList** in Java

| **Feature**            | **List**                                    | **ArrayList**                           |
|------------------------|---------------------------------------------|-----------------------------------------|
| **Definition**         | `List` is an interface in Java, part of the `java.util` package. It defines a contract for implementing classes like `ArrayList`, `LinkedList`, etc. | `ArrayList` is a class that implements the `List` interface. It is backed by a dynamic array and provides the ability to grow as needed. |
| **Type**               | Can be implemented by various classes like `ArrayList`, `LinkedList`, `Vector`, etc. | A specific implementation of the `List` interface using a resizable array. |
| **Methods**            | Inherits methods from the `List` interface, including `add()`, `remove()`, `get()`, `set()`, `size()`, and more. | Inherits methods from `List` interface and provides specific implementations (e.g., resizing array when needed). |
| **Syntax**             | `List<dataType> listName = new LinkedList<>();` | `ArrayList<dataType> listName = new ArrayList<>();` |


