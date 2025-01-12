Source: Spring boot in one vide Durgesh youtube channel

**aritfactId:** is project name

**What is Spring?**
Spring is a Dependency Injection framework to make java application loosely coupled.
Loosely coupled means you can make change/modify module in application using DI.
Tight coupling means you can't change/ modify module later. 

Spring framework makes the easy development of JavaEE application.


Dependency Injection: It is design pattern by following it we can develop our application.
Once class depend on another class object. But Spring can craete another object inject object;


IOC: Inversiion of control,it will create another object and inject in another object.


UI Layer-> Business/Service Layer -> Data Access Layer -> DB

`Spring DI ->
ProductController -> ProductService- (create object in ProductService)ProductDao dao = new ProductDao()-> ProductDAO -> DB. Why this productDao object will be tight couple. 
But in Case of spring ProductDao will craete object and inject to ProductService and productService object will be inject to ProductController. This will be loosely couple`

# Architecture Layers and Modules

## UI Layer
- **Spring MVC**: Handles request mapping, view resolution, and user interface rendering.
- **Spring Security**: Optional for UI-level security, managing authentication and authorization.

## Business/Service Layer
- **Spring MVC**: Controllers that manage business logic, processing requests and returning views.
- **Business/Service Classes**: Logic for processing business tasks, typically annotated with `@Service`.
- **Spring Security**: Optional for securing business logic at the service level.
- **Transaction Management**: Manages transactions for business operations, ensuring consistency and rollback capabilities.

## Data Access Layer
- **Spring JDBC**: Simplifies JDBC operations, including exception handling and resource management.
- **Spring ORM**: Integrates with ORM frameworks like Hibernate or JPA for object-relational mapping.

## DB
- **Database**: Stores data, manages queries, and handles data persistence.


SPRING: Durgesh video : 12:34 time.

# E-commerce Application with Product Management: Dependency Injection Example

In this scenario, we are building an e-commerce application with a focus on product management. We will explore how Dependency Injection (DI) can be used to decouple the classes and improve flexibility, maintainability, and testability in the system.

## Business Problem

- **ProductService** is responsible for the business logic (e.g., adding, updating, deleting products).
- **ProductDao** handles database interactions (e.g., CRUD operations for products).

If the **ProductService** is tightly coupled to the **ProductDao**, any change to the database access logic (such as switching from SQL to NoSQL or altering data access logic) will require modifying the **ProductService** as well. This leads to a maintenance challenge as the project scales.

## Goal

The objective is to create a system where **ProductService** does not directly create the **ProductDao** object. Instead, we will use Spring’s **Dependency Injection** to inject the necessary dependencies, making the system more flexible, maintainable, and easier to test.

---

## Without Dependency Injection/ Spring (Tight Coupling)

In a tightly coupled system, objects are directly created by the class that needs them. In this case, the **ProductService** is responsible for creating the **ProductDao** object and calling its methods for database operations.

### Flow Diagram (Tight Coupling):

```plaintext
+-------------------+       +-------------------+       +-------------------+       +-----------+
| ProductController | ----> |  ProductService   | ----> |     ProductDao    | ----> | Database  |
+-------------------+       +-------------------+       +-------------------+       +-----------+
                            (Creates ProductDao instance/object at ProductService)
```
-> Creates ProductDao's instance/object at **ProductService** then it is provided to **ProductDao**.
### Steps:
1. **ProductController** calls **ProductService** to perform business operations related to products.
2. **ProductService** directly creates an instance/ object of **ProductDao** using `new ProductDao()` for database operations. The object/instance of **ProductDao** created at **ProductService** is provided to **ProductDao**. **ProductService** is tightly coupled to **ProductDao**, making it harder to test or modify **ProductDao**'s implementation. 
3. If the implementation of **ProductDao** changes (e.g., switching databases), **ProductService** needs to be updated as well.
4 **ProductDao** performs CRUD operations on the database.


-----
----


### Flow with Dependency Injection/ Spring (Loose Coupling)

With Spring's Dependency Injection, the **ProductService** does not directly create the **ProductDao** object. Instead, Spring injects the **ProductDao** into **ProductService** at runtime.

```
+-------------------+       +-------------------+       +-------------------+       +-----------+
| ProductController | ----> |  ProductService   | <---- |     ProductDao    |       | Database  |
+-------------------+       +-------------------+       +-------------------+       +-----------+
                            (Injected by Spring)
                                    ^
                                    |
                        +-------------------------------+
                        | Spring Dependency Injection   |
                        | of ProductDao instance/object | 
                        +-------------------------------+
```
-> The **productDao** instance is created in **ProductDao** and it is provided/ injected to **ProductService**, and **ProductService** is object is injected to **ProductController**.
### Steps:
1. **ProductController** calls **ProductService** to perform business operations related to products. 
2. **ProductService** declares a dependency on **ProductDao** using the `@Autowired` annotation or through constructor injection:

   ```java
   @Autowired
   private ProductDao dao;
   ```
3. **ProductService** does not create the **ProductDao** object. Instead, Spring injects the required **ProductDao** instance at runtime.
4. Spring’s Dependency Injection mechanism automatically injects an instance of **ProductDao** into **ProductService**. Spring manages the creation of all objects and handles their dependencies through DI.
5. **ProductService** interacts with **ProductDao** without having to create it.
6. This decouples the classes, meaning that changes to **ProductDao** (e.g., switching from SQL to NoSQL) do not require changes in **ProductService**.
7. **ProductDao** performs CRUD operations on the database.

| Feature              | Tight Coupling (Without Spring)                        | Loose Coupling (With Spring)                      |
|----------------------|--------------------------------------------------------|---------------------------------------------------|
| Object Creation      | Directly created in the service (e.g., new ProductDao()) | Created and injected by Spring (via Dependency Injection) |
| Flexibility          | Low flexibility, as changes in ProductDao require changes in ProductService | High flexibility, can swap ProductDao implementations without changing ProductService |
| Testability          | Difficult to mock ProductDao in tests                  | Easy to mock ProductDao in tests due to Spring's DI |
| Dependency Management | Hardcoded, needs manual updates in the code            | Handled by Spring container, automatic and configurable |


**Dependency Injection (DI):**

Dependency Injection is a design pattern where objects are provided with their dependencies (e.g., other objects or services) rather than creating them internally. In the Spring framework, DI is used to inject dependencies into a class, such as injecting `ProductDao` into `ProductService`. This decouples the classes and improves testability, as dependencies can be easily swapped and mocked in unit tests. DI can be achieved via constructor injection, setter injection, or field injection (as seen with the `@Autowired` annotation in the example). 


**Inversion of Control (IoC):**

Inversion of Control is a design principle where the control of object creation and the flow of execution is handed over to a container or framework, rather than being controlled by the application itself. In the context of Dependency Injection (DI), IoC refers to the way that a framework (like Spring) manages the dependencies between classes. `The application no longer needs to manually create and manage objects, but instead, the framework takes care of the object creation and the injection of dependencies at runtime.` 

**Key Concept: Using Metadata to Automatically Inject Dependencies:**

Spring uses **metadata** (annotations, XML configurations, or Java Config classes) to determine what dependencies to inject and where. This means that Spring’s **Inversion of Control (IoC) container** reads metadata to understand which services or objects (like `ProductDao`, `ProductService`, `ProductController`) need to be injected into other components.

This dynamic configuration process allows Spring to automatically manage object creation and dependency injection at runtime, without any manual intervention in the code.

**Tight Coupling:**

Tight coupling refers to a situation in which one class (e.g., `ProductService`) directly depends on another class (e.g., `ProductDao`) by creating and managing its instance. In this case, the dependent class (e.g., `ProductService`) has a hard dependency on the implementation details of the other class (e.g., it uses `new ProductDao()` to instantiate `ProductDao`). This leads to low flexibility and maintainability, because any change in the dependent class (e.g., changing the database or the implementation of `ProductDao`) would require changes in `ProductService` as well.

**Loose Coupling:**

Loose coupling refers to a design in which classes are less dependent on each other, meaning that changes to one class (e.g., `ProductDao`) do not necessarily require changes to the dependent class (e.g., `ProductService`). In the example with Spring, `ProductService` does not directly create the `ProductDao` object. Instead, `ProductDao` is injected by the framework (Spring), and `ProductService` interacts with it without needing to know the details of its creation. This allows for greater flexibility, as different implementations of `ProductDao` can be swapped in without impacting the rest of the system.



# Spring Modules:
# Definitions and Descriptions
IMPORTANT:


---

### **Spring Framework**
- **What it is**: The Spring Framework is a comprehensive framework for enterprise Java development, providing infrastructure support for developing Java applications.
- **What it does**: It offers a wide range of functionality, including dependency injection, aspect-oriented programming (AOP), transaction management, and web development.
- **Linked with**: Dependency Injection (DI), AOP, Spring Boot, Spring MVC.
---

### **Spring Core** (core- bean- context)
- **What it is**: The core module of the Spring Framework that includes the fundamental concepts such as dependency injection, the IoC container, and other essential infrastructure components.
- **What it does**: It provides the base infrastructure for the Spring framework, handling bean creation, management, and dependency injection.
- **Linked with**: IoC (Inversion of Control), Dependency Injection, Spring Beans.
---

### **Core**
- **What it is**: Core typically refers to the fundamental building blocks of a framework or library. In Spring, it refers to the essential components for dependency injection, configuration, and application context.
- **What it does**: Provides the foundation for Spring applications, including the IoC container, DI (Dependency Injection), and basic utilities.
- **Linked with**: Spring Core, Spring IoC Container.
---
### **Beans**
- **What it is**: In the context of the Spring Framework, a "bean" is an object that is managed by the Spring IoC (Inversion of Control) container.
- **What it does**: It defines the components of your application, and Spring manages their lifecycle and dependencies.
- **Linked with**: Spring IoC, Dependency Injection (DI).
---

### **Context**
- **What it is**: In Spring, a context is an interface that provides the configuration of beans and manages their lifecycle within the application.
- **What it does**: It acts as a container for beans, managing their creation, dependencies, and lifecycle.
- **Linked with**: ApplicationContext (Spring's main container), Spring BeanFactory.
---
### **Data Access/Integration** (JDBC- ORM)
- **What it is**: Data access/integration refers to the technologies and techniques used to connect to databases or external systems and manage data interactions.
- **What it does**: It provides mechanisms for working with data, such as JDBC, ORM (Object-Relational Mapping), and integration tools (like Spring Integration).
- **Linked with**: JDBC, Spring Data, Spring ORM, Spring Batch, Spring Integration.

---

### **ORM (Object-Relational Mapping)**
- **What it is**: ORM is a technique for converting data between incompatible type systems, primarily mapping Java objects to database tables.
- **What it does**: It abstracts away the low-level SQL queries, allowing developers to interact with databases through Java objects.
- **Linked with**: Hibernate, JPA (Java Persistence API), Spring ORM.

---
### **JDBC (Java Database Connectivity)**
- **What it is**: JDBC is an API (Application Programming Interface) in Java that allows Java applications to interact with relational databases.
- **What it does**: It provides methods for querying, updating, and managing databases, allowing Java programs to execute SQL queries, updates, and retrieve results.
- **Linked with**: Relational databases (e.g., MySQL, PostgreSQL, Oracle), SQL.

---

### **Web**
- **What it is**: In the context of Java or Spring, "Web" typically refers to technologies and frameworks that handle HTTP requests and responses, including web servers and application frameworks.
- **What it does**: Manages HTTP communication between client and server, enabling the creation of web applications, handling requests, responses, sessions, and cookies.
- **Linked with**: HTTP, REST, Spring Web, Servlets.

---

### **Servlet**
- **What it is**: A servlet is a Java class that handles HTTP requests and responses in a web application.
- **What it does**: It processes incoming client requests, generates a response (usually HTML), and sends it back to the client.
- **Linked with**: Java EE (Enterprise Edition), Apache Tomcat, Spring MVC.

---

### **Test**
- **What it is**: Test in the Spring context typically refers to the Spring Testing Framework, which supports unit testing and integration testing for Spring applications.
- **What it does**: It provides utilities and annotations to facilitate testing of Spring beans, contexts, and components.
- **Linked with**: JUnit, Spring Test, Mockito, TestContext Framework.

---
# Spring IoC Container

### 1. **Definition**  
The Spring IoC (Inversion of Control) Container is a core part of the Spring Framework. It is responsible for managing the lifecycle of beans (objects) and their dependencies.

### 2. **Responsibilities**  
- **Object Creation**: It creates objects (beans) as defined in the configuration.
- **Object Management**: It holds the beans in memory, ensuring that they are available as needed.
- **Dependency Injection**: It injects one object into another when required (Dependency Injection).
- **Lifecycle Management**: It manages the complete lifecycle of beans, from creation to destruction.

### 3. **Configuration Required**  
- **Beans Configuration**: You need to define all the beans (objects) in the Spring configuration file (XML or Java-based configuration).
- **Dependency Information**: Specify which beans depend on which other beans, so the container can properly wire them together.

### 4. **Usage in Application**  
The main application code will interact with the Spring IoC container to retrieve the beans, and Spring will handle the injection and lifecycle management.

By using the Spring IoC container, you can decouple object creation and management from your application code, allowing for more flexible and modular code.

---
## Application Context in Spring

### Definition
- The **ApplicationContext** in Spring is a central interface to the Spring IoC (Inversion of Control) container. It extends **BeanFactory** and provides more advanced features for managing beans and their lifecycle.

#### Role
- Represents the **IoC container** (Inversion of Control container), where beans are managed and configured.
- Provides access to the beans, allowing you to retrieve or interact with objects that have been configured in the Spring container.

#### How It Works
- The **ApplicationContext** provides methods to get beans by name or type.
- It initializes the beans during startup, manages their lifecycle, and ensures dependency injection is applied correctly.

---

## Different Types of ApplicationContext Implementations

1. **ClassPathXmlApplicationContext**
   - **Purpose**: Loads the Spring configuration from an XML file located on the classpath.
   - **Use Case**: This is used when your Spring beans are defined in an XML file and the application is loaded from the classpath.
   - **Example**:
     ```java
     ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
     ```

2. **AnnotationConfigApplicationContext**
   - **Purpose**: Used to load the Spring configuration from **Java-based configuration** (annotated classes).
   - **Use Case**: This is used when you define your beans using **Java annotations** like `@Configuration`, `@Bean`, etc.
   - **Example**:
     ```java
     ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
     ```

3. **FileSystemXmlApplicationContext**
   - **Purpose**: Loads the Spring configuration from an XML file located in the filesystem (not necessarily on the classpath).
   - **Use Case**: This is used when your Spring beans are defined in an XML file, and the file is outside the classpath (e.g., in the file system).
   - **Example**:
     ```java
     ApplicationContext context = new FileSystemXmlApplicationContext("file:/path/to/beans.xml");
     ```

### Why Use ApplicationContext? DI: 37:11 DURGESH 

- **Centralized Management**: It acts as the central point for accessing all the beans in the application.
- **Advanced Features**: Compared to **BeanFactory**, **ApplicationContext** provides additional features such as event propagation, declarative mechanisms, and support for internationalization.
- **Dependency Injection**: It manages bean creation and dependency injection, making your application loosely coupled and easier to manage.
- **Contextual Information**: It provides access to the environment and other contextual data such as message resources and application events.

## IOC Container and Configuration in Spring Framework

### IOC Container dependency injection can be done in two ways:
- using setter injection (property injection)
- using constructor injection
## Dependency Injection Methods

| **Aspect**                          | **Setter Injection**                                         | **Constructor Injection**                                       |
|-------------------------------------|--------------------------------------------------------------|------------------------------------------------------------------|
| **Dependency Injection Type**       | Dependency is injected through setter methods after object creation. | Dependency is injected at the time of object creation via constructor. |
| **How Dependencies are Set**        | Calls **setter methods** to set the value of dependencies/ object properties.      | Calls the **constructor** to set the value of dependencies/ object's properties.         |
| **Bean Configuration**              | Dependencies can be defined in the bean’s setter methods.   | Dependencies are defined in the constructor parameters.         |
| **Main Use in Spring Framework**    | Useful when dependencies are optional or can be changed post object creation. | Preferred for mandatory dependencies, ensuring all required values are provided on instantiation. |

---

### IOC Container Configuration

| **Point**                                    | **Description**                                                                                                                                                 |
|---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Configuration Files**                      | IOC configuration can be defined in XML or annotation-based configuration. These files specify which injection method to use and how dependencies are provided. |
| **Beans and IOC Container**                  | The classes that are managed by the IOC container are called **beans**. They represent objects with dependencies that need to be injected.                         |
| **XML Configuration and Tags**               | In XML-based configuration, tags like `<bean>` are used to define beans and specify dependencies. Tags indicate which class is dependent and its injected dependencies. |
| **Where Beans and Dependencies are Declared**| Beans and their dependencies are declared in the configuration files (XML, JavaConfig). Dependencies are specified through constructor or setter methods.         |
| **`<bean>` Tag**                             | The `<bean>` tag in XML defines a bean and can specify properties, constructor arguments, and other configuration details for the bean.                          |

# **Inversion of Control (IoC) in Java: (with Setter Injection)**

### **Definition:**
In Java, IoC is a design pattern where an external container (e.g., Spring) manages object creation and dependency injection, instead of the developer doing it manually.

## **Example with Setter Injection:**

### 1. **Student Class (with Setter Injection)**  
The `Student` class has properties like `id`, `name`, and `address`. IoC uses setter methods to inject these dependencies.

```java
class Student {
    private int id;        // id of the student
    private String name;   // name of the student
    private Address address; // Address object injected by IoC container

// Setter method to set student ID (IoC container will call this to inject the id)
    public void setId(int id) { this.id = id; }
// Setter method to set student Name (IoC container will call this to inject the name)
    public void setName(String name) { this.name = name; }
// Setter method to set student Address (IoC container will inject an Address object here)
    public void setAddress(Address address) { this.address = address; }
}
```
**Explanation:**
- The Student class has setters for its properties.
- The IoC container will call these setters to inject values.

### 2. **Address Class (with Setter Injection)**
The Address class has properties like `street`, `city`, etc., with setters to inject these values.

```java
// Address Class with Setter Injection
class Address {
    private String street;
    private String city;
    private String state;
    private String country;

   // Setter method to set street name
    public void setStreet(String street) { this.street = street; }
   // Setter method to set city name
    public void setCity(String city) { this.city = city; }
   // Setter method to set state name
    public void setState(String state) { this.state = state; }
   // Setter method to set country name
    public void setCountry(String country) { this.country = country; }
}
```
**Explanation:**
The `Address` class has setters for its properties.
The IoC container will create and populate an `Address` object.

### 3. **IoC Container Role:**
The IoC container manages the creation of objects and dependency injection.
For example, it will create a `Student` and an `Address` object, then use **setter** methods to inject dependencies.

```java
public class Main {
    public static void main(String[] args) {
       // Example of IoC Container managing the Student and Address objects
        Student student = new Student();

        // IoC container will call these methods to inject values
        student.setId(1);      // Inject ID
        student.setName("John");  // Inject Name

        // Create and inject Address object (IoC container does this automatically)
        Address address = new Address();
        address.setStreet("123 Main St.");
        address.setCity("New York");
        address.setState("NY");
        address.setCountry("USA");

        student.setAddress(address);  // Inject Address (IoC container will do this automatically)

        // Now student object is fully populated with ID, Name, and Address
        System.out.println("Student ID: " + student.id);
        System.out.println("Student Name: " + student.name);
        System.out.println("Student Address: " + student.address);
    }
}
```
#### How the IoC Container Works (with Setter Injection):
- The IoC container will create an instance of `Student`.
- For `Student`, it will inject the `id`, `name`, and `Address` using the setter methods (`setId`, `setName`, and `setAddress`).
- The IoC container will also create an `Address` object and inject values for `street`, `city`, `state`, and `country` using the corresponding setter methods in the `Address` class.

#### Key Points:
- **IoC Container's Role**: It creates objects and injects dependencies.The dependency in this case is the `Address` object that is injected into the `Student` object.  
- The IoC container creates the `Address` object and injects it into the `Student` object using the setter method `setAddress()`.
- **Setter Injection**: Uses setter methods to inject values.
- **Decoupling**: The `Student` class doesn't create or manage its `Address` object; the IoC container does it, making the code easier to maintain.


## Inversion of Control (IoC)  (with Constructor Injection)
It will call constructor to set value of properties/ dependencies in Constructor injection but call setter method in case of setter injection to set value of object's properties.


### 1. **Student Class (with Constructor Injection)**
In this example, the `Student` class requires dependencies such as `id`, `name`, and `address`. These dependencies are injected through the constructor when the `Student` object is created.

```java
class Student {
    private String id;        // id of the student
    private String name;      // name of the student
    private Address address;  // Address object injected via constructor

    // Constructor to inject dependencies
    public Student(String id, String name, Address address) {
        this.id = id;
        this.name = name;
        this.address = address;
    }

    // Getter methods to access the properties
    public String getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public Address getAddress() {
        return address;
    }
}
```
**Explanation**
- The `Student` class does not use setter methods. Instead, dependencies such as `id`, `name`, and `address` are passed to the constructor.
- The `Address` object is injected through the constructor when the `Student` object is instantiated.
- This ensures that the `Student` object is fully initialized with all its required dependencies.

### 2. **Address Class (with Constructor Injection)**
Similarly, the `Address` class also uses constructor injection for its dependencies, including `street`, `city`, `state`, and `country`.

```java
class Address {
    private String street;
    private String city;
    private String state;
    private String country;

    // Constructor to inject dependencies, to set value it will call constructor
    public Address(String street, String city, String state, String country) {
        this.street = street;
        this.city = city;
        this.state = state;
        this.country = country;
    }

    // Getter methods to access the properties
    public String getStreet() {
        return street;
    }

    public String getCity() {
        return city;
    }

    public String getState() {
        return state;
    }

    public String getCountry() {
        return country;
    }
}
```
**Explanation**:

- The `Address` class uses constructor injection for all its dependencies (`street`, `city`, `state`, `country`). 
- By passing these dependencies to the constructor, it ensures that an `Address` object cannot be created without the necessary data.

- The absence of setter methods ensures **immutability** and **consistency**.

### 3. IoC Container Role

In a real-world application, such as when using a framework like Spring, the **IoC Container** is responsible for managing the creation and injection of dependencies.

- The **IoC Container** creates instances of `Student` and `Address` with the required dependencies.
- The container takes care of instantiating the objects and injecting their dependencies via the constructors, reducing the need for manual object creation in the business logic.

Here's how the IoC container might manage the objects:
```java
public class Main {
    public static void main(String[] args) {
        // Example of IoC Container managing the creation and dependency injection
        
        // IoC container will create an Address object with the required parameters
        Address address = new Address("123 Main St.", "New York", "NY", "USA");

        // IoC container will create a Student object and inject dependencies through the constructor
        Student student = new Student("S001", "John", address);

        // Now, the Student object is fully populated with ID, Name, and Address
        System.out.println("Student ID: " + student.getId());
        System.out.println("Student Name: " + student.getName());
        System.out.println("Student Address: " + student.getAddress().getStreet() + ", " + student.getAddress().getCity() + ", " + student.getAddress().getState() + ", " + student.getAddress().getCountry());
    }
}
```
#### Explanation of IoC in the Example:
- The IoC container (in this case, it's the manual instantiation of objects) is responsible for creating the `Address` and `Student` objects.
- Instead of the `Student` class managing its own dependencies, the IoC container supplies the `Address` object to the `Student` constructor.
- This is the essence of **Inversion of Control**: the responsibility for object creation and dependency management lies with the container, not with the class itself.

#### How IoC Works in This Example?

In this example, **Inversion of Control (IoC)** is demonstrated through **Constructor Injection**, where dependencies are provided externally rather than internally within the classes themselves.

- The IoC container manages object creation. When we create a `Student` object, the IoC container automatically provides the necessary dependencies, such as `Address`, by passing them through the constructor.
- This decouples object creation and dependency management from the business logic, making the code more flexible, testable, and maintainable

What types of data types can be handled by IOC container, or it can inject?
- primitive data type: byte, short, char, int, float, double, long, boolean
- collection type: list, set, map and properites
ioc container can inject all of them mentioned  data type inisde another  another object. 

inject : it can inject list inside another object in runtime. 
ioc container will give ready to use object. 


### What types of data types can be handled by IOC container, or it can inject?
The IoC container can handle and inject the following data types:

- **Primitive Data Types:**
 `byte`,
 `short`,
 `char`,
 `int`,
 `float`,
 `double`,
 `long`,
 `boolean`,
- **Collection Types:**
 `List`,
 `Set`,
 `Map`,
 `Properties`,
 - **User defined data Types:Reference Type**: **Example:** We inject Address object into Student Class/ Student Object. Address in object created by us, This Address object is injected in different class/ Student Object.

## Injection/ What is inject means?
The IoC container can inject these data types, including collections, into other objects(set value of object's properites, that will comes from another object) at runtime. It manages dependencies and ensures that the required objects are available when needed. For example, it can inject a `List` or other collection types into another object to provide ready-to-use dependencies.
**Example:** We inject Address object into Student Class/ Student Object. Address in object created by us, This Address object is injected in different class/ Student Object.

Step1: Create class, then set object's properites. 
spring core and spring context dependency are required:

## Lifecycle Methods of Spring:

Spring provides two important lifecycle methods for beans, used for initialization and destruction. These methods can be customized but must follow certain rules.

### 1. **Initialization Method (`init`)**:
- **Signature:** `public void init()`
- **Customization:** You can name the method anything, but the signature (method name and return type) must remain the same. For example, you can name the method `initMethod()` instead of `init()`, but it should still be a `void` method with no parameters.
- **Purpose:** 
   - Used for **initialization** tasks such as loading configuration files, connecting to databases, or initializing web services.
   - This method is invoked after the Spring container has set all bean properties (through dependency injection).

### 2. **Destruction Method (`destroy`)**:
- **Signature:** `public void destroy()`
- **Customization:** Similar to the initialization method, you can name this method anything you want, but it must have the signature `public void destroy()`.
- **Purpose:**
   - Used for **cleanup** tasks like closing database connections, stopping services, or releasing resources.
   - This method is invoked when the Spring container is destroyed (typically when the application shuts down or the container is closed).

---

### Spring Bean Lifecycle Flow (Steps):

1. **Spring Bean Creation**:
   - Spring creates a new bean (i.e., a Java object) using the default constructor.
   
2. **Setting Properties (Dependency Injection)**:
   - The Spring container injects any necessary properties into the bean, such as data sources, values, or other beans.

3. **Calling the `init()` Method**:
   - Once all properties are set, Spring calls the `init()` method (if defined).
   - You can use this method to perform any additional initialization logic such as database connections, file loading, etc.

4. **Bean Ready for Use**:
   - After initialization, the bean is ready for use. The application can interact with it, and Spring will provide the bean as requested by other parts of the application.

5. **Destruction (`destroy()`)**:
   - When the Spring container is shut down, or the bean is no longer needed, Spring calls the `destroy()` method to perform any cleanup (e.g., closing resources or connections).

---

### Spring Bean Lifecycle Flow Diagram
```
+----------------------------+     +-------------------------------+     +-------------------------------+     +-------------------------------+     +-------------------------------+
|      Bean Creation          | --> |     Property Injection        | --> |        init() Method           | --> |      Bean Ready for Use       | --> |        destroy() Method       |
|  (Default Constructor)      |     | (DI - Spring injects values)  |     |   (Perform initialization tasks)|     | (Application uses the bean)   |     |     (Cleanup resources)      |
+----------------------------+     +-------------------------------+     +-------------------------------+     +-------------------------------+     +-------------------------------+

```

---
### Summary of Key Points:
- **`init()`** is called for **initialization** tasks after Spring injects properties into the bean.
- **`destroy()`** is called for **cleanup** tasks when the bean is no longer in use or when the container is destroyed. Cleanup db connection, stop services. 
- You can change the method names for both `init()` and `destroy()`, but their signatures should remain `public void init()` and `public void destroy()`.
- The lifecycle ensures that beans are properly initialized and cleaned up, supporting efficient resource management in Spring-based applications.

# Spring Lifecycle Configuration Techniques

## 1. XML Configuration
- The Spring lifecycle can be configured through the `applicationContext.xml` file.
- Beans can have lifecycle-related methods configured via `<bean>` tags, such as:
  - `init-method`: Specifies the initialization method.
  - `destroy-method`: Specifies the destruction method.
  
### Example:
```xml
<bean id="beanName" class="com.example.BeanClass" init-method="initMethod" destroy-method="destroyMethod"/>
```
### 2. Spring Interface (InitializingBean and DisposableBean)

Spring provides two interfaces to hook into the lifecycle of beans:

## InitializingBean

- **afterPropertiesSet()**: This method is invoked after all the bean properties are set. It is used for initialization logic.

## DisposableBean

- **destroy()**: This method is invoked when the bean is destroyed. It is used for cleanup.

## Example:

```java
import org.springframework.beans.factory.InitializingBean;
import org.springframework.beans.factory.DisposableBean;

public class MyBean implements InitializingBean, DisposableBean {

    private String name;

    // Setter for name property
    public void setName(String name) {
        this.name = name;
    }

    @Override
    public void afterPropertiesSet() throws Exception {
        // Initialization logic after properties are set
        System.out.println("Initialization logic: " + name);
    }

    @Override
    public void destroy() throws Exception {
        // Cleanup logic before bean is destroyed
        System.out.println("Cleanup logic for: " + name);
    }
}
```
### 3. Annotation-based Configuration (@PostConstruct and @PreDestroy)

Annotations provide a more declarative and convenient approach for lifecycle management.

- **@PostConstruct**: Marks a method to be called after the bean has been initialized.
- **@PreDestroy**: Marks a method to be called before the bean is destroyed.

These annotations are part of the `javax.annotation` package (or `jakarta.annotation` in newer versions).
**Example**
```java
import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;

@Component
public class MyBean {

    @PostConstruct
    public void init() {
        // Initialization logic
    }

    @PreDestroy
    public void cleanup() {
        // Cleanup logic
    }
}
```
### Summary of Lifecycle Configuration Techniques
1. `XML Configuration`: Use `init-method` and `destroy-method` in the `<bean>` tag.
2. `Spring Interface`: Implement `InitializingBean` and `DisposableBean` for lifecycle methods.
3. `Annotation-based Configuration`: Use `@PostConstruct` for initialization and `@PreDestroy` for cleanup.



# Autowiring in Spring

Autowiring is a feature of the Spring Framework that allows automatic injection of dependencies into Spring beans. Instead of manually configuring bean dependencies, Spring uses autowiring to match beans based on specified criteria and inject them as required.

## Key Characteristics:
- **Autowiring works with object references**: Dependencies are injected as beans (objects) and not as primitive types or string values.
- **Dependency Injection (DI)**: If `Object A` depends on `Object B`, autowiring helps Spring automatically inject `Object B` into `Object A`.

## Types of Autowiring in Spring

Autowiring in Spring can be configured in two primary ways:
1. **XML Configuration**
2. **Annotation-based Configuration**

### 1. XML Configuration (Autowiring Modes)
In the XML configuration, Spring provides different **autowiring modes** to automatically inject dependencies into beans. The modes are:

- **byName**: The Spring container injects a dependency by matching the bean name. If a bean with a matching name exists, it is injected.
- **byType**: The Spring container injects a dependency by matching the type of the bean. If a matching bean type is found, it will be injected.
- **constructor**: The dependency is injected through the constructor of the bean.

#### Example XML Configuration for Autowiring:
```xml
<bean id="beanA" class="com.example.BeanA" autowire="byName"/>
<bean id="beanB" class="com.example.BeanB"/>
// beanA will automatically receive a reference to beanB if a property or field of beanA matches beanB by name.
```
## 2. Annotation-based Configuration (Using `@Autowired`)

In the annotation-based configuration, autowiring is handled using the `@Autowired` annotation. It allows Spring to automatically inject the dependency either by field, constructor, or setter method based on the type of the bean.

### Autowiring with `@Autowired`:

- **Field-based Autowiring**: You place the `@Autowired` annotation directly on a field, and Spring injects the dependency automatically.

- **Constructor-based Autowiring**: You place the `@Autowired` annotation on the constructor, and Spring injects the dependencies through the constructor.

- **Setter-based Autowiring**: You place the `@Autowired` annotation on the setter method, and Spring injects the dependencies when the setter is called.

### Example Annotation-based Configuration:

#### 1 Field-based Autowiring:
```java
@Autowired
private BeanB beanB;
```
In this example:
`beanB` will be automatically injected into the field of the class where the `@Autowired` annotation is placed.

#### 2 Constructor-based Autowiring:
```java
@Autowired
public BeanA(BeanB beanB) {
    this.beanB = beanB;
}
```





















