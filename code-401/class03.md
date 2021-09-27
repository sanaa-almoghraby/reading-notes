# Primitives vs. Objects
    Every object contains a single value of the corresponding primitive type. The wrapper classes are immutable (so that their state can't change once the object is constructed) and are final (so that we can't inherit from them).
# Pros and Cons

    The decision what object is to be used is based on what application performance we try to achieve, how much available memory we have, the amount of available memory and what default values we should handle.
    Just for the reference, the primitive type variables have the following impact on the memory:

    1.  boolean – 1 bit
    2. byte – 8 bits
    3.  short, char – 16 bits
    4. int, float – 32 bits
    5. long, double – 64 bits
 * 2. Memory Footprint for Arrays
    The situation becomes more interesting if we compare how much memory occupy arrays of the types under consideration.
    The situation becomes more interesting if we compare how much memory occupy arrays of the types under consideration.
* 3. Performance
 already mentioned, the primitive types live in the stack while the reference types live in the heap. This is a dominant factor that determines how fast the objects get be accessed.
 * 4. Default Values 
    Default values of the primitive types are 0 (in the corresponding representation, i.e. 0, 0.0d etc) for numeric types, false for the boolean type, \u0000 for the char type. For the wrapper classes, the default value is null.
# Usage
As we've seen, the primitive types are much faster and require much less memory. Therefore, we might want to prefer using them.

On the other hand, current Java language specification doesn't allow usage of primitive types in the parametrized types (generics),  in the Java collections or the Reflection API.

When our application needs collections with a big number of elements, we should consider using arrays with as more “economical” type as possible, as it's illustrated on the plot above.


# Exceptions in Java
## What Is an Exception?
An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.

## The Catch or Specify Requirement
The Three Kinds of Exceptions:
1. The first kind of exception is the checked exception
2. The second kind of exception is the error.
3. The third kind of exception is the runtime exception
## Catching and Handling Exceptions
This section describes how to use the three exception handler components — the try, catch, and finally blocks — to write an exception handler. Then, the try-with-resources statement, introduced in Java SE 7, is explained. The try-with-resources statement is particularly suited to situations that use Closeable resources, such as streams.
# Using Scanner to read in a file in Java
Objects of type Scanner are useful for breaking down formatted input into tokens and translating individual tokens according to their data type.

* Breaking Input into Tokens
By default, a scanner uses white space to separate tokens. (White space characters include blanks, tabs, and line terminators. For the full list, refer to the documentation for Character.isWhitespace.) To see how scanning works, let's look at ScanXan, a program that reads the individual words in xanadu.txt and prints them out, one per line.

