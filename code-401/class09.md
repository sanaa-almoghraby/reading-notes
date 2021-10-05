## The HTTP Request Lifecycle
- Local Processing
- Resolve an IP
- Establish a TCP Connection
- Send an HTTP Request
- Tearing Down and Cleaning Up

### Step 1: Local Processing

1. Your browser extracts the: "scheme"/protocol, host, optional port number, resource path, and query strings.
2. Now that the browser has the intended hostname for the request, it needs to resolve an IP address.
3. then the browser look through its own cache of recently requested URLs, the operating system’s cache of recent queries, your router’s cache, and your DNS cache.

### Step 2: Resolve an IP

1. If the cache lookup fails (we will assume it does), your browser fires off a DNS request using UDP.
2. Your request will now have to travel many network devices to reach its target DNS server.
3. Once your request arrives at your configured DNS server, the server looks for the address associated with the requested hostname.

   - If it finds one, it sends a response.
   - If, on the other hand, the DNS server you have targeted cannot locate the given hostname, it passes the request along to another DNS server it is configured to defer to.
   - This happens recursively until the address is found, or an "authoritative" nameserver is hit.
   - If an address for the given domain cannot be resolved, the server responds with a failure and your browser returns an error.

4. If the response makes it back the requesting client now has a target IP.

### Step 3: Establish a TCP Connection

1. One of the key differences between TCP and UDP is that TCP ensures delivery and ordered data transmission.

2. what’s most relevant is that TCP connections are opened using what’s known as a three-way handshake. The server must already be "listening" on a port, performing a passive open, after which the client can initiate an active open, and the handshake works as follows:

   1. The client initiates the active open by sending a `SYN` "control" packet to the server.
   2. The server responds with a `SYN-ACK` message, which contains an acknowledgement number for the original message.
   3. In the third step, the client sends an `ACK` message back to the server to ensure that our data is being delivered reliably.

3. We now have a completed three-way handshake and an established connection where both the client and server have received acknowledgment of the connection from the other party.

### Step 4: Send an HTTP Request:

1. The request is made up of a "request line", request header, and a body.
2. Once the HTTP request is sent, it follows a similar routing procedure.
3. Once the server receives the request, processes it, and finds the resource being requested, it generates an HTTP response.
4. Once the response is generated, the server responds to the request. At the TCP layer.

### Step 5: Tearing Down and Cleaning Up

1. Once the response has been fully delivered, the client sends a FIN packet at the TCP level, to which the server responds with an ACK, and then generally sends a FIN of its own, which the client responds to with its own ACK signal.
2. browser begins processing what it has received.


# Do a Simple HTTP Request in Java
1. Overview
2. HttpUrlConnection
The HttpUrlConnection class allows us to perform basic HTTP requests without the use of any additional libraries. All the classes that we need are part of the java.net package.
The disadvantages of using this method are that the code can be more cumbersome than other HTTP libraries and that it does not provide more advanced functionalities such as dedicated methods for adding headers or authentication.
3. Creating a Request
We can create an HttpUrlConnection instance using the openConnection() method of the URL class.
4. Adding Request Parameters
5. Setting Request Headers
   con.setRequestProperty("Content-Type","application/json");
6. Configuring Timeouts
7. Handling Cookies
8. Handling Redirects
9. Reading the Response
