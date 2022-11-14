# 2. Data Types

## Variables and Data Types in Java

In this lesson, you have found out that:

-   A variable is a named program object storing a value of the declared type that can change this value as the program is executed.
-   In Java, data can be stored in the stack or heap.
-   Primitive data types are small, with a predefined size, used mostly to work with numbers.
-   Reference data types – for such variables the stack only stores the address of the memory cell in the heap where the object related to this variable is stored.

## Primitives

In this lesson, you have studied primitive data types. You found out that:

-   Integer literals include **byte**, **short**, **int**, and **long**. They are used to represent integer values.
-   Floating-point literals describe real values and by default have the type **double**. They can also have the type **float**.
-   The boolean (logical) literals include **true** and **false**. They are used to program various alternative actions.
-   **Char** is a character literal. Its description must be enclosed in single quotes. A character literal has two forms: the first in the form of a graphic image of the character in single quotation marks, and the second one in the form of '\ucode' according to which two bytes are allocated for each character.
-   String literals are used to write text consisting of several characters in the program's source code. These are objects of the class **String**.
-   You can define a variable using the keyword **var**. To do this, you must initialize the variable when declaring it.

## Operators

In this lesson, you found out that:

-   Arithmetic operators are used in math expressions in the same way as they are used in algebra.
-   Bitwise operators execute operations bit by bit. In Java they are used only for integer types.
-   The result of comparison and logical operations will always be "true" or "false".
-   The goal of the ternary operator is to make a decision about which value should be returned in the result of its execution.

Moreover, you studied the order of priority of operators in Java, as well as explored the methods of the class **Math**.

## Typecasting

In this lesson, you have explored the rules that determine the type of the resulting expression_._ You have found out that:

-   Widening typecasting can be performed implicitly. This type allows not to lose information about the value of a numeric expression. Java performs this typecasting automatically.
-   Narrowing typecasting is done explicitly. At that, the information about the value of the numeric expression, as well as precision and range, may be lost. This operation is performed by the developer.

You have studied the peculiarities of performing these forms of typecasting and found out how compilation optimization is done in Java.

## Reference Types

In this lesson, you found out that:

-   In Java, objects are placed and stored in the heap. The Java runtime system allocates memory to store an object when you request it using the operator **new**.
-   A string literal is a set of characters placed inside double quotation marks. The compiler wraps all string literals in an object of the class **String** with the value of this literal. The type **String** is a reference data type; therefore, string values are stored in the heap.

## Naming Convention in Java

In this lesson, you found out that:

-   The names of local variables, class fields, method parameters, and method names (should contain verbs) use **CamelCase**.
-   The names of classes, interfaces, annotations, and lists use **TitleCase** The names of classes and lists should be nouns, and the names of interfaces, as a rule, are adjectives.
-   The names of variables with invariable values are specified in uppercase, and the words are separated with the underscore symbol.
-   The names of packages have a prefix that is always specified in lowercase and represents the domain name of the higher level: com, edu, gov, mil, net, org, or a two-letter country code.
-   The names of parameters of the generic types should be a single capital letter.

# 3. Conditions and Loops 

## Concept of the Code Block

In this lesson, you found out that:

-   A variable is a named memory cell storing data.
-   A code block means a part of the program placed in braces.
-   You cannot declare two or more variables with the same name in the same code block.
-   Code blocks can be nested one within the other.

## Conditional Statement

In this lesson, you have explored:

    The syntax of the short and long form of the if statement
    The syntax for a chain of statements
    An example of the construction if-then-else-if

## Selection Statement

In this lesson, you found out that:

-   The statement switch is similar to the branching statement if-then-else. It also allows you to organize branching of the program execution process.
-   The statement switch may be applied only to a known number of possible situations.
-   When the statement switch is used, then in two different branches the keys cannot have the same value.

## Loops

In this lesson, you found out that:

-   Using the statements **while** and **do-while** is useful when it is necessary to repeat certain actions and the number of repetitions is unknown and depends on a certain condition.
-   Branching statements (**break, continue**) are statements that make it possible to go from the point where the statement is used to a different part of the program.
-   It is convenient to use the **for** loop when the number of iterations is known.

# 4. Arrays

This lesson introduced you to the concept of an array. You found out:

-   An array is a set of homogeneous data under a common name in Java in the form of a container object.
-   The data in an array is called elements, each of which has its own index and position.
-   To create an array, you should declare it, allocate memory for it, and initialize it.
-   If the array is small and the initial values of the array elements are known, it may be initialized during declaration.
-   You can create an anonymous array, i.e., an array whose name and length are not specified.

In this lesson, you:

-   Found out that information about the amount of elements an array has is stored in the array's length property
-   Copied part of one array into another array using the _System.arraycopy()_ method
-   Changed the length of an array by reinitializing the reference to it

In this lesson, you have explored the loop statements **for** and **for-each**, and found out that:

-   The **for** loop is convenient when the number of iterations is known.
-   The **for-each** loop is designed for strict sequential execution of loop statements for all elements of a dataset.

# 5. Classes

## Keyword this

To sum up, in this lesson you discovered that:

-   The keyword **this** is a reference to the current object inside a class, that is, the object for which a method or constructor is being executed.
-   There are special methods for accessing closed class fields: A **getter** is a method used to receive the value of a field, while a **setter** is a method used to set the value of a field.
-   Static methods are distinguished by their special behavior, status, tools, and terms of use.
- 
## Creating Objects

In this lesson, you have seen that:

-   Objects in Java are stored in a memory area called a "heap", which you cannot manage by yourself.
-   Creating an object involves three steps: declaring, allocating memory, and initializing.
-   If a reference variable is not linked to an object, it has a null value defined by the literal statement **null**.

In addition, you explored the actions that can be performed with the literal expression **null**.

## Constructors

In this lesson, you have seen that:

-   Constructors are special methods defined in a class that initialize and return objects of the class where they are defined.
-   All classes have constructors.
-   There are two types of constructors: without parameters (default constructors) and with parameters (user-defined constructors).

## Initializers

In this lesson, you have found out that:

-   Initializers are special class structures used to initialize class fields (static) and instance fields.
-   A **final** instance field must be initialized, but only in one place: where it is declared, in a dynamic initializer, or in a constructor.
-   Unused objects are destroyed by a special JVM component called a garbage collector.

## Packages

In this lesson, you have found out that:

-   In Java, **packages** are used to prevent conflicts with names; control access; make searching easier; and find and use classes, interfaces, lists, and annotations.
-   The keyword **import** is used to get access to classes and interfaces from other packages and avoid long names when creating class objects.
-   Static constants and static methods of a class can be used without specifying the class. This helps avoid code complexity and promotes quick comprehension.

# 6. OOP

## Encapsulation

In this lesson, you have seen that:

-   Encapsulation prohibits direct access to the fields of a given class instance from other classes.
-   In Java, access modifiers are responsible for implementing the principle of encapsulation. These are keywords that regulate access to data and code.

You also reviewed several examples that demonstrate how to use the access modifiers public, private, protected, and package-private and reviewed some recommendations for using encapsulation.

## Modifiers static and final

In this lesson, you have seen that:

-   The modifier **static** is used to create methods and variables belonging to a class, not an object.
-   The modifier **final** is used to define a final implementation of classes and methods, as well as invariability of variables and fields.

You also studied the specifics of using these modifiers—including their limitations—with the help of a few examples.

## Inheritance

In this lesson, you have seen that:

-   Inheritance allows you to create a new class (subclass) based on an existing class (superclass) with a complete or partial import of its characteristics. The main benefit of inheritance is reuse.
-   In Java, classes can have one and only one direct superclass (single inheritance).
-   A subclass inherits **public** and **protected** elements from its superclass. **Package-private** elements of a superclass are inherited only if they are defined in the same package. A subclass does not inherit **private** elements from a superclass.
-   Subclasses have various use cases for the elements they inherit—fields and methods.
-   The keyword **super** may be used in subclass constructors to explicitly access superclass constructors and initialize private fields in the superclass.


In this lesson, you have seen that:

-   When creating a subclass object, the constructors of all its superclasses are invoked. This is called constructor chaining. You also studied the rules for invoking superclasses as well as some examples of how to do this.
-   Methods are inherited to implement differences in the behavior of a superclass and a subclass.
-   It is not recommended to use field hiding since this makes code difficult to read.
-   To disable a chain of inheritance, the keyword **final** is used.

## Polymorphism

In this lesson, you have found out that:

-   Polymorphism involves providing a single interface to entities of different types or using a single symbol to represent multiple different types.
-   The most widely used polymorphism in OOP is the use of a reference to a superclass when manipulating a subclass object.
-   Static binding is performed during compilation, and dynamic binding is used during program execution. Static polymorphism is executed faster since there are no dynamic overheads, but additional support from the compiler is required. Dynamic polymorphism is more flexible but is performed slower since a dynamically bound library can work with objects without knowing their complete type.
-   Object typecasting involves receiving access to all methods of a successor class instance when operating it through a reference to the parent class. You can check the correctness of this casting using the operator **instanceof**.

## Method Overloading

In this lesson, you have seen that:

    If one class has two methods with the same name, their parameter lists should be different. These methods are overloaded.
    When calling, the appropriate method is called so the overloading is resolved. This is performed during compilation. The compiler selects the execution method based on the method's signature and the type of arguments passed. This process includes three steps.

## The Class Object

In this lesson, you have seen that:

-   Every class has the class Object as its superclass, and the class Object includes certain methods.
-   The method _toString()_ returns a string representation of an object.
-   The method _equals()_ checks whether two objects are equivalent.
-   The method _hashCode()_ returns the value of the object's hash code.

#  7. Abstract Classes and Interfaces 

## Abstract Classes

In this lesson, you have seen that:

-   Abstraction is a general concept that can be observed in the real world and in OOP languages.
-   Any objects in the real world or classes that conceal internal details help to provide abstraction.
-   Abstractions significantly simplify the processing of program code, reducing complexity and breaking code into smaller parts.

## Interfaces

In this lesson, you have seen that in Java, interfaces are references that can contain:

-   Only immutable fields
-   Declarations of methods (abstract methods) and nested types
-   Methods with static and default implementations (beginning with Java 8)

If a class approves the implementation of an interface, all the methods defined by this interface must appear in the class code for it to be compiled successfully.

You also studied the specifics of using interfaces with the help of various examples and discovered how interfaces are different from abstract classes.

## Interfaces in Java 8

In this lesson, you have seen that:

-   Default methods are marked with the keyword **default** and should have a body. A class is not required to override the body of such a method. In the case of a diamond problem, to avoid a compilation error, the class should provide a common implementation of default methods.
-   Static methods are marked with the keyword **static** and should have an implementation. These methods belong to the interface; they cannot be overridden in the class implementing the interface.
-   In Java, functional interfaces are interfaces with only one abstract method. With this method, the interface can have any number of default and static methods.

## Cloning Objects

In this lesson, you have seen that:

-   Cloning is used when it is necessary to give wider access to an object but at the same time important to leave the initial object unchanged.
-   The **Cloneable** interface marks a class as available for cloning. Without this interface, an attempt to clone a class will throw an exception.
-   Shallow cloning is implemented by Java itself, whereas deep cloning must be implemented by the developer.

## Design Recommendations

-   Decomposition refers to defining physical and logical entities, including the principles of their interaction, based on a domain analysis of the system being created.
-   An immutable object is an object that cannot change states after initialization.
-   The keyword record provides a mechanism for creating a class with immutable instances and is a subclass of the class java.lang.Record.

# 8. Nested Classes

## Concept of a Nested Class

A **nested class** is a class that is described inside another class. A nested class is always connected to an enclosing/limiting/outer class that limits and determines its scope of action. If a nested class is declared within the scope of action of an outer class, it will be a member of the class. It is also possible to declare a nested class within a block, thus making it a local class.

Nested classes are used for several reasons.

- **Grouping classes logically** 
- **Enhancing encapsulation**
- **Improving code readability**

There are two types of nested classes. One is declared using the access modifier **static**; these classes are called **_static nested classes_**. Classes without this modifier are called **_inner classes_**.

https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html

### **Conclusion**

In this lesson, you have seen that:

-   A nested class is a class that is described inside another class.
-   Nested classes are used to group classes logically, enhance encapsulation, and make code easier to read and maintain.
-   One category of nested classes is declared using the access modifier static; these classes are called static nested classes. Classes that lack this modifier are called inner classes. Inner classes are divided into local classes, anonymous classes, and class members.

## Inner Classes

You can learn more about inner classes in [_Oracle's official documentation_](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html). For more examples of using inner classes, check out [_this article_](https://docs.oracle.com/javase/tutorial/java/javaOO/innerclasses.html).

In this lesson, you have seen that:

-   An inner class is a non-static nested class described in the body of another class. An inner class has access to all the fields and methods of the enclosing class and can access them directly.
-   These classes are used when their objects cannot exist or are not needed outside the body of the enclosing class.

You also studied the specifics of and rules for describing and using inner classes and their corresponding objects.

## Local Сlasses

In this lesson, you have seen that:

-   Local classes are inner classes declared in the block of an outer class where a method's body is the common block.
-   Local classes are usually used to conceal the implementation of actions of the outer class.

You also studied the specifics of describing and using local classes and analyzed different examples.


## Anonymous Classes

In this lesson, you have seen that:

-   An anonymous class is a class without a name. In addition, if it is necessary to create a sole class object, there is no need to assign a name to this class.
-   Anonymous classes are used to create an interface object or an abstract class, i.e., for a sole implementation of abstract methods.

You have also studied the rules for describing and using anonymous classes and analyzed different examples.

## Static Nested Сlasses

In this lesson, you have seen that:

-   A static nested class is a class described inside another class with the modifier static.
-   Behavior-wise, a static nested class is a top-level class nested inside another top-level class to make packing easier.

You also explored the specifics of describing and using static nested classes and analyzed some examples of applying them.

## Specifics of Nested Classes


#  9. Working with Strings 

https://docs.oracle.com/en/java/javase/14/docs/api/java.base/java/lang/String.html

In this lesson, you have seen that:

-   A string is a sequence of characters.
-   Strings can be concatenated, compared, and formatted.

## The Classes StringBuilder and StringBuffer

In this lesson, you have seen that:

-   To solve the problem of ineffective memory use, the classes **StringBuffer** and **StringBuilder** were added to Java. Basically, this is an expandable string where changes can be made without compromising performance.
-   When calling methods of the objects **StringBuffer/StringBuilder**, changes are made in the content of the current object, and no new object is created.
-   The **StringJoiner** class was added to Java 8. Its main purpose is to join several strings into one and set a separator, a prefix, and a suffix.

## Regular Expressions

Therefore, in this lesson you have found out:

-   Which metacharacters exist and what they are used for.
-   How to match and use regular expressions.
-   The purpose of some methods of the classes **Pattern** and **Matcher** and how they are used.
-   What methods exist to extract information about groups.


# 10. Exceptions

## Exceptions and Their Types

In this lesson, you have found out that:

-   An exceptional event (exception) is an event that occurs during the execution of a program and disrupts the normal flow of the program's commands or instructions.
-   Handling an exception means to create an alternative path of program execution.
-   When an error occurs, the program creates an exception, throws, and handles it.
-   Depending on the kind and category of an exception, it may be caught and processed. There are two categories of exceptions: checked and unchecked. Unchecked exceptions can be divided into two kinds—errors and runtime exceptions.

## Handling Exceptions

In this lesson, you have studied how to:

-   Handle exceptions in Java using the **try-catch** blocks. For this, a part of code where an exception may occur, is enclosed within the **try** block, after which follows the **catch** block. The **catch** block is a handling block for a specific exception specified in the block's parameters.
-   Apply of the **try-finally** blocks to cleanup the code.

Now in your own programs, you can foresee exceptions and resolve them successfully.

## Throwing and Passing Exceptions

In this lesson, you have found out that:

In this lesson, you have found out that:

-   To throw an exception, the **throw** statement with a parameter is used.
-   To pass an exception to other methods for handling, a component **throws \<exception types\>** is added to the declaration of a method.
-   Passive exception passing means that you just let the exception pass up the call stack until the appropriate handler without catching it along the way.
-   Active passing means that you catch the exception, execute some actions, and re-throw it, or wrap it in a new exception and then throw it: when you need to add additional information about the exception or about the actions that were undertaken in relation to the data when the exception occurred.
-   Overriding superclass methods when they have a **throws** component has its specifics.

## Custom Exceptions

In this lesson, you learned to write custom (user) exceptions as a subclass of the **Throwable** class.

You also received practical recommendations to be used for handling exceptions:

-   Specify exceptions
-   Use the handling mechanism correctly
-   Log events in handlers
-   Do not lose the initial exception
-   Do not generalize exceptions
-   Avoid unnecessary wraps of exceptions



