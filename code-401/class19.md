### Using WebSocket to build an interactive web application
This guide walks you through the process of creating a “Hello, world” application that sends messages back and forth between a browser and a server. WebSocket is a thin, lightweight layer above TCP. This makes it suitable for using “subprotocols” to embed messages. In this guide, we use STOMP messaging with Spring to create an interactive web application. STOMP is a subprotocol 
operating on top of the lower-level WebSocket.

* Starting with Spring Initializr
1. Navigate to https://start.spring.io. This service pulls in all the dependencies you need for an application and does most of the setup for you.


2. Choose either Gradle or Maven and the language you want to use. This guide assumes that you chose Java.
3. Click Dependencies and select Websocket.

4. Click Generate.

5. Download the resulting ZIP file, which is an archive of a web application that is configured with your choices.

* Adding Dependencies
* Create a Resource Representation Class
* Configure Spring for STOMP messaging
* Create a Browser Client
With the server-side pieces in place, you can turn your attention to the JavaScript client that will send messages to and receive messages from the server side.

* Make the Application Executable
* Build an executable JAR

