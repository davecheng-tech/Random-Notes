# Cleaning Up Your `main()` Method (ICS4U Project Tip)

In your ICS4U OOP Design Project, **your `main()` method shouldn't be a giant pile of spaghetti**. Think of `main()` as the "entry point" to your program — it should **coordinate**, not **micromanage**.

This note shows how to keep `main()` clean, readable, and easy to understand using a **Personal Library System** example.


## Goal: Keep `main()` Simple and Meaningful

Your `main()` method should:

- Instantiate objects (create them)
- Call meaningful methods on those objects
- Show how classes interact
- Avoid doing all the work itself!


## Example: Clean, Clear `Main.java`

Here's an example with **no user input**, just method calls to simulate a working system:

```java
public class Main {

    public static void main(String[] args) {
        Library myLibrary = new Library("My Home Library");

        Book book1 = new Book("1984", "George Orwell", "Dystopian", false);
        Book book2 = new Book("To Kill a Mockingbird", "Harper Lee", "Classic", false);
        Book book3 = new Book("The Hobbit", "J.R.R. Tolkien", "Fantasy", true);

        myLibrary.addBook(book1);
        myLibrary.addBook(book2);
        myLibrary.addBook(book3);

        myLibrary.printBookList();

        System.out.println("\nBorrowing '1984'...");
        myLibrary.borrowBook("1984");

        System.out.println("\nTrying to borrow 'The Hobbit' again...");
        myLibrary.borrowBook("The Hobbit");

        System.out.println("\nReturning '1984'...");
        myLibrary.returnBook("1984");

        System.out.println("\nFinal library state:");
        myLibrary.printBookList();
    }
}
```

## Example: Adding a Simple User Input Menu

To reach **Level 4** on the rubric, your program should involve **user interaction**. Here's a menu version using `BufferedReader`:

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {
        Library myLibrary = new Library("My Home Library");

        myLibrary.addBook(new Book("1984", "George Orwell", "Dystopian", false));
        myLibrary.addBook(new Book("To Kill a Mockingbird", "Harper Lee", "Classic", false));
        myLibrary.addBook(new Book("The Hobbit", "J.R.R. Tolkien", "Fantasy", true));

        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        String choice = "";

        while (!choice.equals("5")) {
            printMenu();
            System.out.print("Enter your choice: ");
            choice = reader.readLine();

            switch (choice) {
                case "1":
                    myLibrary.printBookList();
                    break;
                case "2":
                    System.out.print("Enter the title of the book to borrow: ");
                    String borrowTitle = reader.readLine();
                    myLibrary.borrowBook(borrowTitle);
                    break;
                case "3":
                    System.out.print("Enter the title of the book to return: ");
                    String returnTitle = reader.readLine();
                    myLibrary.returnBook(returnTitle);
                    break;
                case "4":
                    myLibrary.printAvailableBooks();
                    break;
                case "5":
                    System.out.println("Exiting library system. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }

            System.out.println(); // Blank line for spacing
        }
    }

    private static void printMenu() {
        System.out.println("=== Personal Library Menu ===");
        System.out.println("1. View all books");
        System.out.println("2. Borrow a book");
        System.out.println("3. Return a book");
        System.out.println("4. View available books");
        System.out.println("5. Exit");
    }
}
```

## Final Tips

- Your `main()` should read like a **story** — what the program does, not how every little thing is done.
- Offload logic to classes and helper methods.
- Think of `main()` as the **director**, not the actor.

Clean `main()` = Clear program design = Higher marks ✅