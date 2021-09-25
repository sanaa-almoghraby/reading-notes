# React Docs - lists and keys
## 1. What does .map() return?
Return value
A new array with each element being the result of the callback function.

## 2. If I want to loop through an array and display each value in JSX, how do I do that in React?
Use the .map() method to render data.
Parse and display data in an array of objects
### EX
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
we loop through the numbers array using the JavaScript map() function. We return a <li> element for each item. Finally, we assign the resulting array of elements to listItems

## 3.Each list item needs a unique ____.
“key” 
A “key” is a special string attribute you need to include when creating lists of elements. 

## 4.What is the purpose of a key?
 Keys are used to React to identify which items in the list are changed, updated, or deleted. In other words, we can say that keys are used to give an identity to the elements in the lists.
 =======================================================================================================
 # The Spread Operator
## 1.What is the spread operator?
The spread operator is a useful and quick syntax for adding items to arrays, combining arrays or objects, and spreading an array out into a function’s arguments.
InJavaScript, spread syntax refers to the use of an ellipsis of three dots (…) to expand an iterable object into the list of arguments.
## 2.List 4 things that the spread operator can do.

Copying an array
Concatenating or combining arrays
Using Math functions
Using an array as arguments
## 3. Give an example of using the spread operator to combine two arrays.
### EX
const myArray = [`🤪`,`🐻`,`🎌`]
const yourArray = [`🙂`,`🤗`,`🤩`]
const ourArray = [...myArray,...yourArray]
console.log(...ourArray) // 🤪 🐻 🎌 🙂 🤗 🤩 

## 4.Give an example of using the spread operator to add a new item to an array.
### EX
const fruits = ['🍏','🍊','🍌','🍉','🍍']
const moreFruits = [...fruits];
console.log(moreFruits) // Array(5) [ "🍏", "🍊", "🍌", "🍉", "🍍" ]
fruits[0] = '🍑'
console.log(...[...fruits,'...',...moreFruits]) //  🍑 🍊 🍌 🍉 🍍 ... 🍏 🍊 🍌 🍉 🍍

## 5.Give an example of using the spread operator to combine two objects into one.
### EX
The following example uses the spread operator (...) to merge the person and job objects into the employee object
let person = {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    ssn: '123-456-2356'
};


let job = {
    jobTitle: 'JavaScript Developer',
    location: 'USA'
};

let employee = {
    ...person,
    ...job
};

console.log(employee);
========================================================================================================

# How to Pass Functions Between Components
## 1.In the video, what is the first step that the developer does to pass functions between components?

creat the function wherever the state is we're going to change 

## 2.In your own words, what does the increment function do?

change the value of stare 

## 3.How can you pass a method from a parent component into a child component?
by pass it as a props
## 4.How does the child component invoke a method that was passed to it from a parent component? 
call the methot that was pass as props.
will invoke the state method and pass the data.

## Things I want to know more about
* learn more about state

* learn more about pass functions between components
