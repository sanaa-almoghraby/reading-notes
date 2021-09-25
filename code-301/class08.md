# API Design Best Practices

## 1.What does REST stand for?
REST stands for Representational State Transfer. (It is sometimes spelled "ReST".) It relies on a stateless, client-server, cacheable communications protocol -- and in virtually all cases, the HTTP protocol is used. REST is an architecture style for designing networked applications

## 2.REST APIs are designed around a ____.

REST APIs are designed around resources, which are any kind of object, data, or service that can be accessed by the client. REST APIs use a uniform interface, which helps to decouple the client and service implementations

## 3.What is an identifer of a resource? Give an example.
A resource has an identifier, which is a URI that uniquely identifies that resource. For example, the URI for a particular customer order might be:

HTTP

Copy
https://adventure-works.com/orders/1

## 4.What are the most common HTTP verbs?

The most common operations are GET, POST, PUT, PATCH, and DELETE.

## 5.What should the URIs be based on?

 resource URIs should be based on nouns (the resource) and not verbs (the operations on the resource).

## 6.Give an example of a good URI.
## 7.What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?

 all web requests impose a load on the web server. The more requests, the bigger the load. Therefore, try to avoid "chatty" web APIs that expose a large number of small resources 
 it a bad thing
## 8.What status code does a successful GET request return?
A successful GET method typically returns HTTP status code 200 (OK). 
## 9.What status code does an unsuccessful GET request return?
 the method should return 404 (Not Found).
## 10.What status code does a successful POST request return?
return HTTP status code 200 and include the result of the operation in the response body.

## 11.What status code does a successful DELETE request return?
operation is successful, the web server should respond with HTTP status code 204, indicating that the process has been successfully handled

## Things I want to know more about
 servar ==> request and response in http