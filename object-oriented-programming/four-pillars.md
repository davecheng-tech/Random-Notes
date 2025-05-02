# Understanding the Four Pillars of OOP: A Guide to Object-Oriented Programming

This article explores the four pillars of OOP - **Encapsulation, Abstraction, Inheritance and Polymorphism** - and how these fundamental concepts shape modern software design. Whether you are starting with OOP or seeking a better understanding, this guide will give you practical examples and clear insights to apply these principles effectively in your development projects. Learn how every pillar contributes to create organized, flexible, and easy-to-maintain systems.

## Introduction

Object-Oriented Programming (OOP) is a widely adopted paradigm in modern software development, providing a structured and modular approach to building complex systems. Unlike procedural programming, which focuses on functions and logic, OOP revolves around the creation of objects: **self-contained units that combine both data and behavior**. This method not only mirrors real-world entities but also enhances the scalability, maintainability, and reusability of code.

At the core of OOP are four essential pillars: **Encapsulation, Abstraction, Inheritance, and Polymorphism**. These principles serve as the foundation for writing clean, organized, and flexible code that can evolve with changing requirements.

Let’s start by exploring how these pillars contribute to better design practices and why they are key to successful object-oriented programming.

## 1. Encapsulation

### Definition

Encapsulation is one of the fundamental principles of OOP. It teaches us to hide the internal details of an object and expose only what is necessary through public interfaces. This means that an object's private attributes and methods remain protected, and their access is controlled by public methods like getters and setters. In this way, the internal state stays safe from unwanted changes, maintaining the integrity of the data.

### Example

```java
public class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public void deposit(double value) {
        balance += value;
    }

    public boolean withdraw(double value) {
        if (value <= balance) {
            balance -= value;
            return true;
        } else {
            return false;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

In this example, the account balance is protected (made `private`), and only can be modified through the controlled methods. This guarantees that the balance changes are made in a safe and correct manner.

### Benefits

- **Data security:** prevents sensitive information from being accessed or modified directly.
- **Easy maintenance:** changes to internal details do not affect the external code that interacts with the object.
- **Modularity:** each object becomes an independent unit, improving the organization of the system.

## 2. Abstraction

### Definition

Abstraction is the process of **hiding complexity** and **exposing only the essential details** of an object. Instead of revealing all the internal implementation, only relevant operations are made available externally. This helps developers focus on the primary functionalities of a class or object, without worrying about the internal implementation details.

### Practical Example

Consider a payment system with different payment methods like credit card, PayPal, and bank transfer. We can use an interface or an abstract class called `Payment`, where the specific details of each payment method are hidden. The idea is to provide a common way to process payments:

```java
public abstract class Payment {
    public abstract void processPayment(double amount);
}

public class CreditCard extends Payment {
    @Override
    public void processPayment(double amount) {
        // Fancy logic to process a credit card payment goes here
        System.out.println("Processing credit card payment of: " + amount);
    }
}

public class PayPal extends Payment {
    @Override
    public void processPayment(double amount) {
        // Fancy logic to process a PayPal payment goes here
        System.out.println("Processing PayPal payment of: " + amount);
    }
}
```

Here, abstraction allows each payment method to have its own implementation, but all of them follow a common structure defined by the abstract class `Payment`.

### Practical Example

Consider this interface and usage of a `Printer` class:

#### `Printer` Class
```java
public class Printer {
    public void printDocument(String content) {
        loadPaper();
        startInk();
        System.out.println("Printing: " + content);
        finish();
    }

    private void loadPaper() {
        System.out.println("Loading paper...");
    }

    private void startInk() {
        System.out.println("Starting ink system...");
    }

    private void finish() {
        System.out.println("Finished printing.");
    }
}
```

#### `Printer` Usage
```java
public class Main {
    public static void main(String[] args) {
        Printer myPrinter = new Printer();
        myPrinter.printDocument("Hello, world!");
    }
}
```

From the outside, you only need to call `printDocument()`. You don’t need to worry about loading paper or starting ink — those details are hidden inside the class. The complexity is abstracted away.

### Benefits of Abstraction

- **Simplification:** focus on the essential aspects, making objects easier to use and understand.
- **Flexibility:** different implementations can be created without changing the external interface.
- **Easier maintenance:** changes to the implementation do not affect the code that uses the abstraction.

## 3. Inheritance

### Definition

Inheritance is the mechanism by which one class **inherits the characteristics (attributes and methods)** of another class. The class that inherits is called a **subclass** or **derived class**, while the class that is inherited from is called the **superclass** or **parent class**.

### Practical Example

```java
public class Vehicle {
    protected String brand;

    public void start() {
        System.out.println("Vehicle started.");
    }
}

public class Car extends Vehicle {
    public void openDoor() {
        System.out.println("Car door opened.");
    }
}

public class Motorcycle extends Vehicle {
    public void raiseKickstand() {
        System.out.println("Kickstand raised.");
    }
}
```

In this example, both `Car` and `Motorcycle` inherit the `start()` method from the `Vehicle` class. The subclasses can also have their own specific behaviors, such as `openDoor()` for Car and `raiseKickstand()` for `Motorcycle`.

### Benefits of Inheritance

- **Code reuse:** prevents duplication by allowing subclasses to reuse methods and attributes from the superclass.
- **Easier extension:** common behaviors can be centralized in the superclass, while subclasses add specific functionality.
- **Hierarchical organization:** reflects real-world relationships, making the code structure more logical.

## 4. Polymorphism

### Definition

Polymorphism allows a single interface or method to have **multiple forms** of implementation or execution. In practice, this means that different objects can respond to the same message or method call in different ways, making the code more flexible and extensible.

- **Method overloading:** same method with different signatures (compile-time).
- **Method overriding:** same method name, different implementation in subclass (runtime).

Going back to the payment example, we can see polymorphism in action when using the same `processPayment()` method call, but with different behaviors depending on the payment method:

### Practical Example

```java
public class Main {
    public static void main(String[] args) {
        Payment creditCardPayment = new CreditCard();
        Payment paypalPayment = new PayPal();

        creditCardPayment.processPayment(100.0);
        paypalPayment.processPayment(200.0);
    }
}
```

Here, `processPayment()` has different implementations in `CreditCard` and `PayPal`, but the method is called polymorphically through the `Payment` superclass reference.

### Benefits of Polymorphism

- **Flexibility:** allows a method to have different behaviors depending on the object that implements it.
- **Extensibility:** makes it easier to add new functionality without modifying existing code.
- **Code reuse:** enables general methods to operate on different types of objects, making the system more modular.

## Reference

- [Java Polymorphism](https://www.w3schools.com/java/java_polymorphism.asp)
- [Java Abstraction](https://www.w3schools.com/java/java_abstract.asp)
- [Java Inheritance](https://www.w3schools.com/java/java_inheritance.asp)
- [Java Encapsulation](https://www.w3schools.com/java/java_encapsulation.asp)