# UML Class Diagram Reference (ICS4U)

This note is a reference for understanding and creating **UML Class Diagrams** in the ICS4U Computer Science course. It summarizes essential notation and concepts, using examples explored in class.

<!-- vscode-markdown-toc -->
* [Purpose of UML Class Diagrams](#PurposeofUMLClassDiagrams)
* [Class Diagram Structure](#ClassDiagramStructure)
	* [Example](#Example)
* [Class Diagram Notation](#ClassDiagramNotation)
	* [Visibility](#Visibility)
	* [Attributes](#Attributes)
	* [Methods](#Methods)
	* [Return Type and Parameters](#ReturnTypeandParameters)
* [Relationships Between Classes](#RelationshipsBetweenClasses)
	* [HAS-A Relationship (Aggregation)](#HAS-ARelationshipAggregation)
	* [IS-A Relationship (Inheritance)](#IS-ARelationshipInheritance)
* [Static Variables and Methods](#StaticVariablesandMethods)
* [Abstract Classes and Methods](#AbstractClassesandMethods)
* [Specificity vs. Language-Neutral Implementation](#Specificityvs.Language-NeutralImplementation)
	* [Example Attribute/Method Variants](#ExampleAttributeMethodVariants)
	* [Generalized (Language-Neutral) Approach](#GeneralizedLanguage-NeutralApproach)
	* [Specific (Java-Centric) Approach](#SpecificJava-CentricApproach)
	* [So Which Should You Use?](#SoWhichShouldYouUse)
* [Using Enums in UML Class Diagrams](#UsingEnumsinUMLClassDiagrams)
	* [Declaring an Enum in UML](#DeclaringanEnuminUML)
	* [Referencing the Enum in a Class](#ReferencingtheEnuminaClass)
	* [Connecting the Enum to the Class](#ConnectingtheEnumtotheClass)
	* [In Java](#InJava)
	* [Summary](#Summary)
* [Summary of Elements to Include](#SummaryofElementstoInclude)
* [Tools for Making UML Diagrams](#ToolsforMakingUMLDiagrams)
* [Additional References](#AdditionalReferences)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

## <a name='PurposeofUMLClassDiagrams'></a>Purpose of UML Class Diagrams
UML (Unified Modeling Language) Class Diagrams are a visual way to model the structure of an object-oriented program. They show the classes, their attributes (fields), operations (methods), and the relationships between them.

<br>

## <a name='ClassDiagramStructure'></a>Class Diagram Structure
Each class is shown as a box with three sections:
1. **Class Name** (top)
2. **Attributes / Fields** (middle)
3. **Operations / Methods** (bottom)

### <a name='Example'></a>Example

![Classroom](/images/uml-01.png)

This diagram describes the `Classroom` class with the following features:

```java
public class Classroom {

    // Instance variables
    private Teacher teacher;
    private Student[] students;

    // Constructor
    public Classroom(Teacher teacher, Student[] students) {
        this.teacher = teacher;
        this.students = students;
    }

    // Methods
    public int getSize() {
        return students.length;
    }

    public double getAverage() {
        if (students.length == 0) return 0.0;

        double total = 0.0;
        for (Student s : students) {
            total += s.getGradeAvg();
        }
        return total / students.length;
    }
}
```

<br>

## <a name='ClassDiagramNotation'></a>Class Diagram Notation

### <a name='Visibility'></a>Visibility
- `+` Public
- `-` Private

### <a name='Attributes'></a>Attributes
```
- name: String
- salary: double
```

### <a name='Methods'></a>Methods
```
+ getName(): String
+ setSalary(double): void
```

### <a name='ReturnTypeandParameters'></a>Return Type and Parameters
Methods must show the return type and the data type of any parameters:
```
+ markBump(double): void
```

<br>

## <a name='RelationshipsBetweenClasses'></a>Relationships Between Classes

### <a name='HAS-ARelationshipAggregation'></a>HAS-A Relationship (Aggregation)
Represented by a **white (or empty) diamond** arrow pointing from the part to the whole:

- A `Classroom` HAS-A `Teacher`
- A `Classroom` HAS-MANY `Students`

The diagram will show multiplicity:
- `1` for one
- `1..*` for one or more
- `0..1` for optional
- `*` for many (zero or more)

### <a name='IS-ARelationshipInheritance'></a>IS-A Relationship (Inheritance)
Represented by a **white (or empty) triangle** arrow pointing from the child to the parent:
- A `Teacher` IS-A `Person`
- A `Player` IS-A `TeamMember`

![UML Class Diagram](/images/uml-02.png)

<br>

## <a name='StaticVariablesandMethods'></a>Static Variables and Methods
Use **underlining** in the diagram:
- Static variables (shared across all instances of the class)
- Static methods (can be called without an object)

In the above example, `playerCount` is a static variable, and `getPlayerCount()` is a static method.

<br>

## <a name='AbstractClassesandMethods'></a>Abstract Classes and Methods
Use **italics** in the diagram:
- Abstract classes cannot be instantiated
- Abstract methods are declared but not implemented in the base class

![UML Class Diagram](/images/uml-03.png)

Any subclass must implement the abstract method.

<br>

## <a name='Specificityvs.Language-NeutralImplementation'></a>Specificity vs. Language-Neutral Implementation

When designing UML diagrams, it's common to wonder **how specific you should be about data structures and return types**. There are two valid approaches, each with its advantages:

### <a name='ExampleAttributeMethodVariants'></a>Example Attribute/Method Variants

```plaintext
- messages: String[ ]
- messages: ArrayList<String>

+ getMessages(): String[ ]
+ getMessages(): List<String>
```

### <a name='GeneralizedLanguage-NeutralApproach'></a>Generalized (Language-Neutral) Approach

- `- messages: String[ ]`  
- `+ getMessages(): String[ ]`

This version avoids Java-specific classes like `ArrayList` or `List`. It's ideal if you're:
- Designing for a **broad audience** or multiple languages
- Just focusing on **conceptual modeling**
- Teaching the idea of an **array or collection**, without locking into Java syntax


### <a name='SpecificJava-CentricApproach'></a>Specific (Java-Centric) Approach

- `- messages: ArrayList<String>`  
- `+ getMessages(): List<String>`

This version uses **Java's collection classes** explicitly. It’s great when:
- You're implementing the diagram in Java immediately
- You want to be **clear about coding choices** and interface use
- You're reinforcing the distinction between concrete classes (`ArrayList`) and abstract interfaces (`List`)


### <a name='SoWhichShouldYouUse'></a>So Which Should You Use?

Both styles are acceptable in our class. It depends on your **intent**:
- If you’re focused on **planning or cross-language design**, go more general.
- If you're preparing to **write Java code right after**, feel free to be specific.

Just be consistent within a diagram.

<br>

## <a name='UsingEnumsinUMLClassDiagrams'></a>Using Enums in UML Class Diagrams

When designing object-oriented systems, it's common to use **enums** to represent a fixed set of values — for example, message priorities like `NORMAL`, `HIGH`, or `URGENT`. UML has a standard way to show this.

### <a name='DeclaringanEnuminUML'></a>Declaring an Enum in UML

You represent an enum using a **class-like box** with the stereotype `<<enumeration>>`. For example:

![Enum Diagram](/images/uml-04b.png)

This indicates that `Priority` is an enum with three possible values.

### <a name='ReferencingtheEnuminaClass'></a>Referencing the Enum in a Class

If you have a class like `Message` that uses this enum, you can show it as:

![Enum Diagram](/images/uml-04a.png)


This shows that the `priority` field is of type `Priority`, defined by the enum above.

### <a name='ConnectingtheEnumtotheClass'></a>Connecting the Enum to the Class

Use a **simple solid line** (association) to connect the class to the enum:

![Enum Diagram](/images/uml-04.png)

There is:
- **No diamond** (◇) — this is not aggregation.
- **No triangle** (◁) — this is not inheritance.
- Just a plain association line to indicate usage.
- Arrowhead is optional, but if used, should originate from the object to the enum.

### <a name='InJava'></a>In Java

```java
public enum Priority {
    NORMAL,
    HIGH,
    URGENT
}

public class Message {
    private Priority priority;

    public Priority getPriority() {
        return priority;
    }
}
```

### <a name='Summary'></a>Summary

| Concept        | UML Representation             |
|----------------|--------------------------------|
| Enum           | `<<enumeration>>` stereotype   |
| Enum values    | Listed in enum block           |
| Attribute type | `priority: Priority`           |
| Relationship   | Solid line (association)       |

Use this approach in your designs when modeling any fixed-value types using enums.

<br>

## <a name='SummaryofElementstoInclude'></a>Summary of Elements to Include
| Feature                        | Notation / Indicator                    |
|-------------------------------|-----------------------------------------|
| Public / Private              | `+` / `-`                               |
| Attribute (Field)             | `name: Type`                            |
| Method                        | `methodName(params): ReturnType`        |
| Static                        | <ins>Underlined</ins>                   |
| Abstract                      | *Italicized*                            |
| Aggregation (HAS-A)          | ◇ Diamond Arrow - from part to whole, w/ diamond on the whole side |
| Inheritance (IS-A)           | ▷ Triangle Arrow (unfilled) - from child to parent |
| Multiplicity (Cardinality)   | `1`, `0..1`, `1..*`, `*`                 |

<br>

## <a name='ToolsforMakingUMLDiagrams'></a>Tools for Making UML Diagrams
We recommend using the website [**draw.io** / diagrams.net](https://draw.io) (also available on the Chrome Web Store) to build your own UML class diagrams.

<br>

## <a name='AdditionalReferences'></a>Additional References

While we will use this document as the official UML style guide for ICS4U, you can read more at this [Visual Paradigm UML Class Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/). 
