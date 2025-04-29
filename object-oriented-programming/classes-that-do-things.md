# OOP Design: Classes That "Do Things"

In Object-Oriented Programming (OOP), a good class is not just a container for data — it **knows things about itself** and **can make decisions or perform actions**.

Bad OOP design ("dumb data classes") just stores information and forces the rest of your program to figure everything out.  

Good OOP design builds **smart objects** that manage their own logic.

## DON'T: Dumb Data Class

Here’s an example of a weak Shoe class for a clothing inventory system:

```java
public class Shoe {
    private String material;
    private String season;

    public String getMaterial() { return material; }
    public String getSeason() { return season; }
}
```

Main program:

```java
if (shoe.getSeason().equals("Winter")) {
    // Winter shoe
}
if (shoe.getMaterial().equals("Leather") || shoe.getMaterial().equals("Rubber")) {
    // Good for wet weather
}
```

The main program is doing all the thinking. The `Shoe` object is just a bag of facts.

## DO: Behavioral Class

Better version — the Shoe knows about itself:

```java
public class Shoe {
    private String material;
    private String season;

    public boolean isWinterShoe() {
        return season.equalsIgnoreCase("Winter");
    }

    public boolean isGoodForRain() {
        return material.equalsIgnoreCase("Leather") || material.equalsIgnoreCase("Rubber");
    }
}
```

Main program:

```java
if (shoe.isWinterShoe()) {
    System.out.println("This shoe is good for winter.");
}

if (shoe.isGoodForRain()) {
    System.out.println("Wear this shoe on rainy days.");
}
```

The logic is **inside the object** — cleaner, safer, and easier to maintain.

<br>

## Example: Inventory Item Price Calculation

### DON'T: Dumb Data Class

```java
public class InventoryItem {
    private String name;
    private double price;

    public String getName() { return name; }
    public double getPrice() { return price; }
}
```

Main program:

```java
double priceWithTax = item.getPrice() * 1.13;
System.out.println("Price with tax: $" + priceWithTax);
```

The main program is doing the calculation — the item doesn't know its own final price.

### DO: Behavioral Class

```java
public class InventoryItem {
    private String name;
    private double price;

    public double getPriceWithTax() {
        return price * 1.13;
    }
}
```

Main program:

```java
System.out.println("Price with tax: $" + item.getPriceWithTax());
```

Now, the **InventoryItem** knows how to calculate its taxed price.

<br>

## Example: Student and Passing Grade

### DON'T: Dumb Data Class

```java
public class Student {
    private double average;

    public double getAverage() { return average; }
}
```

Main program:

```java
if (student.getAverage() >= 50) {
    System.out.println("Student passed.");
}
```

The main method is deciding what "passing" means.

### DO: Behavioral Class

```java
public class Student {
    private double average;

    public boolean hasPassed() {
        return average >= 50;
    }
}
```

Main program:

```java
if (student.hasPassed()) {
    System.out.println("Student passed.");
}
```

**The Student object knows if it passed or failed.**

<br>

## Example: Car Maintenance Check

### DON'T: Dumb Data Class

```java
public class Car {
    private int mileage;

    public int getMileage() { return mileage; }
}
```

Main program:

```java
if (car.getMileage() > 10000) {
    System.out.println("Time for an oil change.");
}
```

Again, the main method does the thinking.

### DO: Behavioral Class

```java
public class Car {
    private int mileage;

    public boolean needsOilChange() {
        return mileage > 10000;
    }
}
```

Main program:

```java
if (car.needsOilChange()) {
    System.out.println("Time for an oil change.");
}
```

The **Car** takes responsibility for knowing when it needs maintenance.

<br>

# Summary

### Good Classes:
- Own their calculations and decision-making
- Hide their raw data as much as possible
- Make code easier to read, use, and maintain

### Bad Classes:
- Just expose data through getters
- Push responsibility onto other parts of the program

Always ask yourself:

> Can I move this decision or action into the object itself?

That's what great object-oriented programming looks like. Try applying these choices to your object-oriented design project.