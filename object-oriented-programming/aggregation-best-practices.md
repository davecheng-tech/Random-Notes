# OOP Best Practices: Code Review Notes

As we wrap up these aggregation and encapsulation assignments, here are some key best practices observed in top student submissions. These guidelines will help you write cleaner, more professional, and more reusable code.

## 1. Use of `enum` for Categorical Data

Instead of using Strings for values like type or rarity (e.g., "Fire", "Common"), define them as enums. This provides:

- Compile-time validation (no typos)
- A fixed set of allowed values
- Better readability and type safety

Example:

```java
public enum Type {
    FIRE, WATER, GRASS, ELECTRIC, ...
}
```

Use enums for both `Type` and `Rarity` in your card class for consistency.

## 2. Return Objects, Don’t Just Print

Design your methods to return objects like `Card` or `List<Card>` instead of printing directly inside the method. This approach:

- Makes your code reusable and easier to test
- Separates logic from presentation

Instead of this:

```java
public void showHighestHpCard() {
    // prints to console
}
```

Do this:

```java
public Card getCardWithHighestHp() {
    // returns a Card object
}
```

You can then decide where and how to display that result (e.g., in `Main.java`).

## 3. Clear and Conventional Method Naming

Choose method names that clearly describe their purpose and follow common Java conventions.

Recommended naming patterns:
- `getCardsByType()` instead of `findAllTypes()`
- `getCardWithHighestHp()` instead of `findHighestHP()`
- `getAllCards()` instead of `getCollection()` (which can be unclear)

Naming matters—make your method names tell the truth about what they return.

## 4. Protect Your Data (Optional Advanced Tip)

Avoid returning direct references to internal lists unless you really mean to allow modification.

Instead of this:

```java
public List<Card> getAllCards() {
    return cards;
}
```

Use defensive copying:

```java
public List<Card> getAllCards() {
    return new ArrayList<>(cards);
}
```

This keeps the internal state of your object safe from accidental changes.

---

Practicing these habits will help you as you work on larger, more complex Java projects. They’re also great habits to carry into Grade 12 Computer Science or post-secondary programming work.
