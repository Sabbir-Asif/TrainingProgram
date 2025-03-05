# HTTP (Hyper Text Transfar Protocol)

## What is HTTP
HTTP is a protocol for fetching resources such as HTML documents. It is the foundation of any data exchange on the Web.  
- A protocol is a system of rules that define how data is exchanged within or between computers. Communications between devices require that the devices agree on the format of the data that is being exchanged. The set of rules that defines a format is called a protocol.  

## **HTTP** is a client server protocol.  
A client-server protocol is a set of rules that govern communication between a client and a server over a network. The client requests services or resources, while the server processes those requests and responds accordingly.
### Why HTTP is a Client-Server Protocol
HTTP is a client-server protocol because it follows the client-server architecture, where:  
- **Client Requests:** A web browser (client) sends an HTTP request to a web server to fetch a webpage, image, or other resources.  

- **Server Response:** The web server processes the request and responds with the requested data, usually in HTML, JSON, or other formats.

- **Stateless Communication:** Each HTTP request is independent, meaning the server does not retain information about previous requests unless additional mechanisms like cookies or sessions are used.  

For example, when you type a URL into your browser:

- The browser (client) sends an HTTP request (e.g., GET /index.html).  

- The server processes this request and sends back the requested page (200 OK response with HTML content).  

- The browser renders the page for the user.  

Since HTTP follows this request-response model between a client and a server, it is classified as a client-server protocol.

<img src="../Assets/HTTP/HTTP1.svg" alt="HTTP Diagram" width="600" height="400">

## **HTTP** is an application layer protocol.  
An Application Layer Protocol is a set of rules that govern how software applications communicate over a network, providing services like web browsing, email, and file transfer.  

### Why is HTTP an Application Layer Protocol?

- **Handles End-User Communication** – HTTP enables users to access web pages by defining how requests and responses are exchanged between a client (browser) and a server.  
  *Example:* A browser sends an HTTP request to `example.com`, and the server responds with an HTML page.  

- **Defines Request and Response Rules** – HTTP standardizes how clients request resources and how servers respond (e.g., using `GET`, `POST`, `PUT`, `DELETE` methods).  
  *Example:* `GET /index.html` fetches a webpage, while `POST /login` submits user data.  

- **Relies on the Transport Layer (TCP/UDP)** – HTTP does not manage data transmission directly; instead, it relies on **TCP (Transmission Control Protocol)** at the **Transport Layer (Layer 4)** to ensure reliable delivery.  
  *Example:* TCP ensures all HTTP packets are received correctly, preventing missing or duplicate data.  

- **No Involvement in Data Transmission** – HTTP only structures and interprets data but does not handle packet routing, addressing, or network management (handled by lower OSI layers).  
  *Example:* HTTP requests are converted into TCP/IP packets by lower layers before transmission.  

- **Uses Human-Readable Data Formats** – HTTP communicates using **plain text, JSON, XML, and HTML**, which are designed for application-level interactions.  
  *Example:* A REST API returns JSON-formatted data over HTTP.  

## Components of HTTP-based systems  

<img src="../Assets/HTTP/client-server-chain.svg" alt="HTTP Diagram" width="600">

Each individual HTTP request is sent to a server, which handles it and provides an answer called the response. Between the client and the server there are numerous entities, collectively called proxies, which perform different operations and act as gateways or caches. 

### Role of Proxies  
- Proxies sit between the client and server, performing different tasks:  
  - Forward Proxy: A forward proxy sits between the client and the internet. It processes client requests and forwards them to the destination server on behalf of the client. (VPN, filtering).  
  - Reverse Proxy: A reverse proxy sits in front of a web server, handling requests from clients before they reach the server (load balancing, security, chaching).  
- Requests may pass through multiple proxies before reaching the server, and responses follow the same route back.  

### Network Components Between Client and Server  
- Other hidden network devices include:  
  - Routers: Direct traffic across networks.  
  - Modems: Convert digital signals for internet transmission.  
  - Switches: Manage internal network traffic.  
- These devices operate at lower OSI layers (Network & Transport), while HTTP functions at the Application Layer.  

### HTTP at the Application Layer  
- HTTP focuses only on communication between the client and server.  
- It does not handle routing, addressing, or transmission, which are managed by lower layers (TCP/IP).  

## HTTP uses TCP protocol

<img src="../Assets/HTTP/TCP-Gif.gif" alt="HTTP Diagram" width="500">  

<br>  

- TCP uses three way handshaking method before sending data over the network.  
- Reliable data transfar protocol.
- Full Duplex. (both sender and reciever can send and recieve data at the same time)
- Flow Contorl ( hints to the sender on how much data can be received)

### **HTTP Server**
- The server responds to client requests by serving the requested documents.  
- It may appear as a single machine but can actually be a **cluster of servers** using **load balancing** and additional software (caches, databases, etc.).  
- Multiple **server instances** can run on the same machine, and with **HTTP/1.1 Host headers**, they can even share the same IP address.  

## **How the HTTP Host Header Allows Multiple Servers on the Same Machine**  

The **Host** header in HTTP/1.1 allows multiple websites (or virtual hosts) to run on a **single server** with the same IP address. This is known as **virtual hosting** and is commonly used by web hosting providers.  

### **How It Works**  
- When a client (browser) sends an HTTP request, it includes a **Host** header specifying the domain name (e.g., `Host: example.com`).  
- The web server uses this header to determine **which website** the client is trying to access.  
- Based on the Host value, the server directs the request to the correct **website configuration or virtual host**.  

### **Example of an HTTP Request with a Host Header**  
```http
GET /index.html HTTP/1.1  
Host: example.com  
```  

Here, the server checks `example.com` and serves the corresponding website files.  

## **Types of Virtual Hosting Using the Host Header**  

### **1. Name-Based Virtual Hosting**  
- Multiple websites share the **same IP address**.  
- The **Host** header differentiates them.  
- Example: `example.com` and `test.com` run on the same server.  

### **2. IP-Based Virtual Hosting**  
- Each website has a **separate IP address**, even on the same machine.  
- Less common due to **IPv4 limitations**.  

### **Example: Apache Virtual Host Configuration**  
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/example
</VirtualHost>

<VirtualHost *:80>
    ServerName test.com
    DocumentRoot /var/www/test
</VirtualHost>
```  
## Basic aspects of HTTP

### HTTP is Simple and Human-Readable  
HTTP (Hypertext Transfer Protocol) is designed to be simple and easy to understand, even for humans. Unlike other complex protocols that require special encoding, HTTP messages are plain text and can be manually created, read, and debugged without special tools.  

Even though HTTP/2 introduced binary framing (which is less readable), HTTP/1.1 remains human-readable, making it easier for developers to test and debug web communication.  

### Example: Human-Readable HTTP Request and Response  

#### Example of an HTTP Request (Sent by a Browser to a Web Server)  
When you visit a website (e.g., example.com), your browser sends a request like this:  

```http
GET /index.html HTTP/1.1  
Host: example.com  
User-Agent: Mozilla/5.0  
Accept: text/html  
```

#### Explanation:  
- `GET /index.html` → The browser is requesting the homepage (index.html).  
- `Host: example.com` → The domain name of the website.  
- `User-Agent: Mozilla/5.0` → Identifies the browser (e.g., Chrome, Firefox).  
- `Accept: text/html` → Requests an HTML response.  

A developer can easily read this request and understand what the browser is asking for.  

#### Example of an HTTP Response (Sent by the Web Server to the Browser)  
The server replies with a plain-text response:  

```http
HTTP/1.1 200 OK  
Content-Type: text/html  
Content-Length: 1024  

<html>  
  <head><title>Example</title></head>  
  <body><h1>Welcome to Example.com!</h1></body>  
</html>
```

#### Explanation:  
- `HTTP/1.1 200 OK` → The server successfully found the page.  
- `Content-Type: text/html` → The response contains an HTML document.  
- `Content-Length: 1024` → The size of the content (in bytes).  

The HTML body follows, which the browser renders as a webpage. Since everything is in plain text, developers can easily read, modify, and debug the communication between the client and server.  

### Why Simplicity Matters  
- **Easy Testing**: Developers can send HTTP requests manually using tools like `curl` or Postman.  
- **Debugging**: If something goes wrong, HTTP messages are readable and can be analyzed directly.  
- **Learning Curve**: New developers can quickly understand how HTTP works without needing advanced networking knowledge.  

Even though HTTP/2 introduced binary message encoding for better performance, HTTP remains simple because tools like browsers and debuggers automatically convert messages for human readability.  

### HTTP/1.1 vs. HTTP/2: Request and Differences  
HTTP/2 introduced binary framing for better performance, multiplexing, and efficiency, but it still supports the same high-level request methods as HTTP/1.1. Below is a comparison of a basic HTTP/1.1 request with an HTTP/2 request, highlighting key differences.  

#### HTTP/1.1 Request Example  
In HTTP/1.1, requests and responses are sent as plain text.  

```http
GET /index.html HTTP/1.1  
Host: example.com  
User-Agent: Mozilla/5.0  
Accept: text/html  
Connection: keep-alive  
```

#### Characteristics of HTTP/1.1:  
- Human-readable (plain-text format).  
- One request per connection unless `keep-alive` is used.  
- Head-of-line blocking issue (next request must wait for the previous response).  
- More redundant headers (sent in every request).  

#### HTTP/2 Request Example (Binary Framing)  
In HTTP/2, the same request is sent but in binary format, improving performance.  

##### Binary Representation (Not Human-Readable)  
HTTP/2 encodes the request into binary frames, making it more efficient but less readable. Here’s an abstract representation:  

```binary
0000 0010 0011 0101 0100 0010 0110 1101 ... (Binary data)  
```

Since this isn’t human-readable, let's break it down into its frame structure:  

##### HTTP/2 Framing Example (Readable Format)  
HTTP/2 uses frames instead of plain text:  

```sql
[STREAM 1] -> HEADER frame:  
  :method = GET  
  :path = /index.html  
  :authority = example.com  
  :scheme = https  
  user-agent = Mozilla/5.0  
  accept = text/html  

[STREAM 1] -> DATA frame:  
  (Contains additional request body if needed)  
```

#### Key Differences in HTTP/2:  
- **Binary Framing** – Uses binary encoding for efficiency.  
- **Multiplexing** – Multiple requests can be sent simultaneously on the same connection.  
- **Header Compression (HPACK)** – Reduces redundant headers using compression.  
- **No Head-of-Line Blocking** – Requests/responses don’t block each other.  
- **No Need for Connection Keep-Alive** – A single connection handles multiple requests efficiently.  

## **HTTP is Extensible**  
HTTP is designed to be extensible, allowing new features to be added without modifying the core protocol. This extensibility is primarily achieved through **HTTP headers**, which were introduced in HTTP/1.0.  

HTTP headers enable clients and servers to **agree on new functionalities** dynamically. If both the client and server understand a custom header, they can use it to exchange additional information beyond the standard HTTP fields.  

---  

### **Example: Custom HTTP Headers**  

#### **1. Standard HTTP Request**  
A typical HTTP request includes common headers:  

```http
GET /index.html HTTP/1.1  
Host: example.com  
User-Agent: Mozilla/5.0  
Accept: text/html  
```

#### **2. Using a Custom Header**  
A client can send a custom header to provide additional data, such as an **API version**:  

```http
GET /index.html HTTP/1.1  
Host: example.com  
User-Agent: Mozilla/5.0  
Accept: text/html  
X-API-Version: 2.0  
```

Here, `X-API-Version: 2.0` is **not a standard HTTP header**, but if the server understands it, it can serve version 2.0 of the API.  

---  

### **3. Example: Feature Negotiation**  
A client and server can **agree** to use a custom header to enable a new feature.  

#### **Client Request with a Custom Header**  

```http
GET /data HTTP/1.1  
Host: api.example.com  
Accept: application/json  
X-Enable-Compression: gzip  
```

#### **Server Response with Compression**  

```http
HTTP/1.1 200 OK  
Content-Type: application/json  
Content-Encoding: gzip  

{Compressed JSON Data}  
```

Here, the `X-Enable-Compression: gzip` header informs the server that the client supports gzip compression. If the server recognizes this, it responds with a **gzip-compressed JSON response**.  

---  

### **Why HTTP's Extensibility Matters**  
- **Backward Compatibility** – New headers do not break older clients/servers that do not recognize them.  
- **Custom Features** – Developers can introduce new features like security mechanisms, tracking, or optimizations.  
- **APIs & Versioning** – APIs can evolve without breaking existing clients.  
- **Experimentation** – Developers can test new features before standardization.  

This ability to **add new headers** without modifying the protocol itself makes HTTP a **flexible and evolving** communication standard.


