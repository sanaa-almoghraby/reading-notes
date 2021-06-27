# React Lifecycle Events #
![](https://miro.medium.com/max/2800/0*0saPKFiTUk6W3FYp)

## 1. Based off the diagram, what happens first, the ‘render’ or the ‘componentDidMount’?

render.
componentDidMount will only be called once after the first render.

## 2.What is the very first thing to happen in the lifecycle of React?

static getDerivedStateFromProps() The static getDerivedStateFromProps is the first React lifecycle method to be invoked during the updating phase

## 3. Put the following things in the order that they happen: componentDidMount, render, constructor, componentWillUnmount, React Updates

1. constructor 
2. render
3. React Updates
4. componentDidMount
5. componentWillUnmount

## 4.What does componentDidMount do?
This method is invoked immediately after a component is mounted.
This method is a good place to set up any subscriptions.
---------------------------------------------------------------------------
# React State Vs Props
## 1. What types of things can you pass in the props?
* The values can be any data type, from strings to functions, objects, etc
* initial values 
* values we did not change them. 
## 2. What is the big difference between props and state?
props you bass into a component and state is handled and update inside of that component and props are handled and update outside of the component
## 3. When do we re-render our application?
when we change the state inside app

## 4.What are some examples of things that we could store in state?
inside of a form


## Things I want to know more and more about react 
 ### sources ###
[](https://www.youtube.com/watch?v=IYvD9oBCuJI)
[](https://www.youtube.com/watch?v=IYvD9oBCuJI)