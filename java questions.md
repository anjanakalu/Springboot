# Dependency Injection Example in Java

### Question:

**Q1:**

In the given scenario, you need to design two classes, `Student` and `Address`. The `Student` class should have fields for `id`, `name`, and an `Address` object, which represents the address of the student. The `Address` class should have fields for `street`, `city`, `state`, and `country`.

- **Dependency Injection**: The `Student` class should not directly create an `Address` object. Instead, the `Address` should be passed into the `Student` class via constructor injection.
- Implement both classes with proper constructors, getter and setter methods, and a `toString()` method to display the student and address information in a readable format.

On this  code:
- `**Student Class**: The Address object is injected into the Student class via the constructor, following constructor-based dependency injection.`

- `**Main Class:** In the main method, we first create an Address object, then pass it into a new Student object during construction.`

**Write the complete code to implement the above functionality.**

---

### Answer:

```java
// Address class definition
class Address {
    String street;
    String city;
    String state;
    String country;

    // Constructor for Address class to initialize the fields
    public Address(String street, String city, String state, String country) {
        this.street = street;
        this.city = city;
        this.state = state;
        this.country = country;
    }

    // toString method to display Address information in a readable format
    @Override
    public String toString() {
        return street + ", " + city + ", " + state + ", " + country;
    }

    // Getter and Setter methods for Address fields
    public String getStreet() {
        return street;
    }

    public void setStreet(String street) {
        this.street = street;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    public String getState() {
        return state;
    }

    public void setState(String state) {
        this.state = state;
    }

    public String getCountry() {
        return country;
    }

    public void setCountry(String country) {
        this.country = country;
    }
}

// Student class definition
class Student {
    int id;
    String name;
    Address address;

    // Constructor for Student class to initialize the fields
    public Student(int id, String name, Address address) {
        this.id = id;
        this.name = name;
        this.address = address; // Injecting Address dependency via constructor
    }

    // toString method to display Student information in a readable format
    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Address: " + address;
    }

    // Getter and Setter methods for Student fields
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Address getAddress() {
        return address;
    }

    public void setAddress(Address address) {
        this.address = address;
    }
}

// Main class to demonstrate the usage of Student and Address classes
public class Main {
    public static void main(String[] args) {
        // Creating an Address object
        Address address = new Address("1234 Elm St", "Springfield", "IL", "USA");

        // Creating a Student object and injecting the Address dependency
        Student student = new Student(1, "John Doe", address);

        // Printing the Student object which will automatically call the toString method
        System.out.println(student);
    }
}
