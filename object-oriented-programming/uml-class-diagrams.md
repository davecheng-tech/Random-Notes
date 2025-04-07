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
* [Tools for Making UML Diagrams](#ToolsforMakingUMLDiagrams)
* [Summary of Elements to Include](#SummaryofElementstoInclude)
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
Represented by a **diamond** arrow:
- A `Classroom` HAS-A `Teacher`
- A `Classroom` HAS-MANY `Students`

The diagram will show multiplicity:
- `1` for one
- `1..*` for one or more
- `0..1` for optional
- `*` for many (zero or more)

### <a name='IS-ARelationshipInheritance'></a>IS-A Relationship (Inheritance)
Represented by a **solid** arrow with an empty triangle.
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

## <a name='ToolsforMakingUMLDiagrams'></a>Tools for Making UML Diagrams
We recommend using the website [**draw.io** / diagrams.net](https://draw.io) (also available on the Chrome Web Store) to build your own UML class diagrams.

<br>

## <a name='SummaryofElementstoInclude'></a>Summary of Elements to Include
| Feature                        | Notation / Indicator                    |
|-------------------------------|-----------------------------------------|
| Public / Private              | `+` / `-`                               |
| Attribute (Field)             | `name: Type`                            |
| Method                        | `methodName(params): ReturnType`       |
| Static                        | <ins>Underlined</ins>                              |
| Abstract                      | *Italicized*                              |
| Aggregation (HAS-A)          | ◇ Diamond Arrow                           |
| Inheritance (IS-A)           | ◁ Triangle Arrow                          |
| Multiplicity (Cardinality)   | `1`, `0..1`, `1..*`, `*`                |

<br>

## <a name='AdditionalReferences'></a>Additional References

While we will use this document as the official UML style guide for ICS4U, you can read more at this [Visual Paradigm UML Class Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/). 
