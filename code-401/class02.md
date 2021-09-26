# Packages and Import
![]()
    Package = directory. Java classes can be grouped together in packages. A package name is the same as the directory (folder) name which contains the .java files. You declare packages when you define your Java program, and you name the packages you want to use from other libraries in an import statement.

* Package declaration 
    The first statement, other than comments, in a Java source file, must be the package declaration.

    Default package. Altho all Java classes are in a directory, it's possible to omit the package declaration. For small programs it's common to omit it, in which case Java creates what it calls a default package. Sun recommends that you do not use default packages.
* Package declaration syntax
    1.Package statment (optional).
    2.Imports (optional).
    3.Class or interface definitions.

    // This source file must be Drawing.java in the illustration directory.

    package illustration;

    import java.awt.*;

    public class Drawing {
        . . .
    }
# Common imports
    There are 166 packages containing 3279 classes and interfaces in Java 5.
    #### ex :

    import java.awt.*;	     Common GUI elements.

    import java.awt.event.*;	The most common GUI event listeners.

# import FAQ
    Q: Is the order of the imports important?
    A: No. Group them for readability.
    Q: I've imported java.awt.*, why do I also need java.awt.event.*?
    A: The wildcard "*" only makes the classes in this package visible, not any of the subpackages.

# A Guide to Java Loops
    Here are the types of loops that we can find in Java:

    1.Simple for loop
![](https://media.geeksforgeeks.org/wp-content/uploads/20191108131134/For-Loop.jpg)

    2.Enhanced for-each loop
 ![](https://1.bp.blogspot.com/-sbcx1gZN5Zs/XPeFw4TNCdI/AAAAAAAAU9A/d37MRLD2RsMX7DyiFc9DglQn27VtAvVZACLcBGAs/w1200-h630-p-k-no-nu/The%2BEnhanced%2Bfor%2Bloop%2Bin%2BJava%2B-%2BHostmann%2Bbook.png)
    3.While loop

![](https://media.geeksforgeeks.org/wp-content/uploads/20191118164726/While-Loop-GeeksforGeeks.jpg)
    4.Do-While loop

 ![](https://media.geeksforgeeks.org/wp-content/uploads/20191118154342/do-while-Loop-GeeksforGeeks2.jpg)
