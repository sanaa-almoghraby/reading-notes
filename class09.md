# Functional Programming Concepts
### 1.What is functional programming?
Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data 

### 2.What is a pure function and how do we know if something is a pure function?
Pure Function is a function (a block of code ) that always returns the same result if the same arguments are passed. It does not depend on any state, or data change during a program's execution rather it only depends on its input arguments.

* It returns the same result if given the same arguments (it is also referred as deterministic)
* It does not cause any observable side effects


### 3.What are the benefits of a pure function?
The code’s definitely easier to test. We don’t need to mock anything
Unchanging over time or unable to be changed.

### 5.What is Referential transparency?
Basically, if a function consistently yields the same result for the same input, it is referentially transparent.
===============================================================================
# Node JS Tutorial for Beginners #6 - Modules and require()
### 1.What is a module?
JS modules (also known as “ES modules” or “ECMAScript modules”) are a major new feature, or rather a collection of new features. You may have used a userland JavaScript module system in the past
### 2.What does the word ‘require’ do?
The require() method is used to load and cache JavaScript modules. So, if you want to load a local, relative JavaScript module into a Node. js application, you can simply use the require() method.
### 3.How do we bring another module into the file the we are working in?
with require function pass the file path in the require function as string
### 4.What do we have to do to make a module available?
using module.exports = to the part we want