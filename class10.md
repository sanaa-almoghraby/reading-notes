# Understanding the JavaScript Call Stack
### 1.What is a ‘call’?

At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).

### 2.How many ‘calls’ can happen at once?
It is single-threaded. Meaning it can only do one thing at a time.

### 3.What does LIFO mean?
 Last In, First Out data structure.
### 4.Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.

Here is the example code:

function firstFunction(){
  console.log("Hello from firstFunction");
}

function secondFunction(){
  firstFunction();
  console.log("The end from secondFunction");
}

secondFunction();
### 5.What causes a Stack Overflow?
when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.
=================================================================================================
# JavaScript error messages
![](https://miro.medium.com/max/1000/1*LHpmsxV3f2znpxhuAFuIqA.png)
This is a sample of an error, the green is the overall error message, the light blue is to note if the error was properly handled, the brownish (dark yellow) is the type of error and the red is the call stack
### 1.What is a ‘refrence error’?
Reference errors
This is as simple as when you try to use a variable that is not yet declared you get this type os errors.
console.log(foo) // Uncaught ReferenceError: foo is not defined

### 2.What is a ‘syntax error’?

this occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.
JSON.parse( {'foo': 'bar'} ) // Uncaught SyntaxError: Unexpected token o in JSON at position 1

### 3.What is a ‘range error’?

r is thrown when trying to pass a number as an argument to a function that does not allow a range that includes that number. This can be encountered when to create an array of an illegal length with the Array constructor, or when passing bad values to the numeric methods Number.
### 4.What is a ‘tyep error’?
The TypeError object represents an error when an operation could not be performed, typically (but not exclusively) when a value is not of the expected type. A TypeError may be thrown when: an operand or argument passed to a function is incompatible with the type expected by that operator or function
### 5.What is a breakpoint?
 which will make your program stop at that point only if a condition is met, 
### 6.What does the word ‘debugger’ do in your code?
A debugger is a software tool that can help the software development process by identifying coding errors at various stages of the operating system or application development. Some debuggers will analyze a test run to see what lines of code were not executed.
