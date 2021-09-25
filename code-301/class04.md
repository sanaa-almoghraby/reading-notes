# React Docs - Forms
### 1. What is a ‘Controlled Component’?

A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange . A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component

# 2.Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.

In HTML, form elements such as <input>, <textarea>, and <select> typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

# 3.How do we target what the user is entering if we have an event handler on an input field?

When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.


# The Conditional (Ternary) Operator Explained
![](https://miro.medium.com/max/2000/1*z2KBmBJYD3_4-lfKjhO_DQ.png)

condition ? value if true : value if false
* The condition is what you’re actually testing. The result of your condition should be true or false or at least coerce to either boolean value.
* A ? separates our conditional from our true value. Anything between the ? and the : is what is executed if the condition evaluates to true.
* Finally a : colon. If your condition evaluates to false, any code after the colon is executed.


## 1.Why would we use a ternary operator?

Use the ternary operator to simplify your if-else statements that are used to assign values to variables. The ternary operator is commonly used when assigning post data or validating forms.
## 2.Rewrite the following statement using a ternary statement:
* ternary operator :

x===y ? console.log( true ): console.log(fulse );

## Things I want to know more about
evry thing  :`)