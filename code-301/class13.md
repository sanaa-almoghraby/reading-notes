# Status Codes Based On REST Methods
### 1.In your own words, describe what each group of status code represents:
100’s =Information responses
200’s =Successful responses
300’s =Multiple Choices redirect status response code indicates that the request has more than one possible responses
400’s = Bad Request response status code indicates that the server cannot or will not process the request due to something that is perceived to be a client error 
500’s =Internal Server Error server error response code indicates that the server encountered an unexpected condition that prevented it from fulfilling the request
### 2.What is a status code 202?
 the request was valid, but its processing will finish sometime in the future
### 3.What is a status code 308?
Permanent Redirect - This tells the client to use another URL to access the resource and not use the current URL anymore. It’s helpful when we have multiple endpoints for one resource, but don’t want to implement reading from all of them.
### 4.What code would you use if an update didn’t return data to a client?
204 No Content - A proper code for updates that don’t return data to the client, for example when just saving a currently edited document.
### 5.What code would you use if a resource used to exist but no longer does?
410 Gone - This is like 404 but we know that the resource existed in the past, but it got deleted or somehow moved, and we don’t know where.
### 6.What is the ‘Forbidden’ status code?
403 Forbidden - The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.
=======================================================================================================
# Build A REST API With Node.js, Express, & MongoDB - Quick
### 1. Why do we need to pull our MongoDB database string out of our server and put it into our .env?
becuse when we deploy our application we're going to want to use something thats not our localhost
### 2.What is middleware?
Middleware is software that provides common services and capabilities to applications outside of what’s offered by the operating system. Data management, application services, messaging, authentication, and API management are all commonly handled by middleware.
### 3.What does app.use(express.json()) do?
allow us to use any middleware that we want which is essentially code that runs when the server gets arequest  
### 4.What does the /:id mean in a route?
this means that this is a parameter that we can access by typing in request.
access to whatever they pass in after the first slash
### 5.What is the difference beween PUT and PATCH?
patch becausee we only want to update based on what the user passes .
put it would update all the information
### 6.How do you make a defalut value in a schema?
{default:Data.now}
data it just going to default it to the current date now 

### 7.What does a 500 error status code mean? 
500 status code means that theres an error on your server
### 8.What is the difference between a status 200 and a status 201?
201 means successfully created an object ,it more spacific way when created something 
200 everuthing was successful 