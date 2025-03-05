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

<br>

## HTTP is Stateless, but Not Sessionless

HTTP is a stateless protocol, meaning each request from a client to a server is treated as independent, with no memory of previous interactions. However, this can be problematic for web applications that require stateful behavior, such as login sessions or shopping carts.

To solve this, HTTP cookies allow the use of stateful sessions, maintaining context across multiple HTTP requests.

---

### Example: Stateless HTTP Request
Since HTTP does not remember past interactions, let's look at two separate requests from the same user:

#### 1st Request – Login Page
The user requests the login page:

```http
GET /login HTTP/1.1  
Host: example.com  
```

**Server Response:**

```http
HTTP/1.1 200 OK  
Content-Type: text/html  
```

The server serves the login page but does not track this user’s request history.

---

#### 2nd Request – Dashboard (Without a Session Cookie)
Now, if the user immediately requests the dashboard:

```http
GET /dashboard HTTP/1.1  
Host: example.com  
```

**Server Response:**

```http
HTTP/1.1 401 Unauthorized  
Content-Type: text/html  
```

The server has no memory of the login request, so it denies access to the dashboard.

---

### Using Cookies for Stateful Sessions
To maintain a session, the server sends a session cookie upon login.

#### 1st Request – Login with Session Creation

```http
POST /login HTTP/1.1  
Host: example.com  
Content-Type: application/x-www-form-urlencoded  

username=user&password=pass  
```

**Server Response (with a session cookie):**

```http
HTTP/1.1 200 OK  
Set-Cookie: session_id=abc123; Path=/; HttpOnly  
```

Now, the client stores `session_id=abc123` and includes it in future requests.

---

#### 2nd Request – Dashboard (With a Session Cookie)
Now, when accessing the dashboard, the browser includes the session cookie:

```http
GET /dashboard HTTP/1.1  
Host: example.com  
Cookie: session_id=abc123  
```

**Server Response:**

```http
HTTP/1.1 200 OK  
Content-Type: text/html  
```

Since the session ID matches the logged-in user, the request is accepted, and the dashboard is shown.

---

### Why This Matters
- **Stateless by Design**: HTTP itself does not track requests between clients and servers.
- **Stateful Sessions with Cookies**: Servers use cookies to maintain user state across requests.
- **Session Management**: This enables essential web features like authentication, shopping carts, and user preferences.  

<br>

## HTTP and Connections

HTTP operates at the application layer, while connections are managed by the transport layer (such as TCP or UDP). HTTP itself does not require a connection-based transport protocol but does require a reliable one. Since TCP (Transmission Control Protocol) is reliable (ensuring no data loss), HTTP is typically built on top of TCP.

### Example: HTTP Over TCP (Default HTTP/1.0 Behavior)

In HTTP/1.0, a new TCP connection is opened for every request-response cycle, which leads to inefficiencies.

#### 1st Request – New Connection Created
```
GET /index.html HTTP/1.0
Host: example.com
```
- TCP connection opens → HTTP request sent → Server responds → TCP connection closes.

#### 2nd Request – Another New Connection Needed
```
GET /about.html HTTP/1.0
Host: example.com
```
- A new TCP connection must be established again for this request.

**Problem:** Opening and closing connections repeatedly increases latency and resource usage.

### HTTP/1.1 – Persistent Connections and Pipelining

To optimize performance, HTTP/1.1 introduced persistent connections and pipelining.

#### Persistent Connections Example

In HTTP/1.1, a connection can remain open for multiple requests using the `Connection: keep-alive` header.

**Client Request 1 (Keeps Connection Open)**
```
GET /index.html HTTP/1.1
Host: example.com
Connection: keep-alive
```
- TCP connection remains open for further requests.

**Client Request 2 (Uses Same Connection)**
```
GET /about.html HTTP/1.1
Host: example.com
```

**Benefit:** Reduces the need to open/close connections repeatedly, improving efficiency.

**Pipelining** (introduced in HTTP/1.1) allows sending multiple requests at once without waiting for responses, but it proved difficult to implement and was rarely used.

### HTTP/2 – Multiplexing for Even Better Performance

HTTP/2 solves connection inefficiencies by introducing multiplexing, which allows multiple HTTP requests to be sent simultaneously over a single TCP connection.

#### Example of HTTP/2 Multiplexing

Instead of sending one request at a time, HTTP/2 streams multiple requests and responses in parallel.

**Client Sends Multiple Requests Over a Single Connection**
```
[Stream 1] → GET /index.html
[Stream 2] → GET /about.html
[Stream 3] → GET /contact.html
```

**Server Responds As Data Becomes Available**
```
[Stream 2] ← 200 OK (about.html)
[Stream 1] ← 200 OK (index.html)
[Stream 3] ← 200 OK (contact.html)
```

**Benefit:**
- No need for separate TCP connections for each request.
- Faster page loads as requests and responses are processed in parallel.
- Better network resource utilization.

### Summary of HTTP Connection Improvements

| HTTP Version | Connection Behavior |
|-------------|---------------------|
| HTTP/1.0    | Opens a new TCP connection for every request-response. |
| HTTP/1.1    | Supports persistent connections (`Connection: keep-alive`), reducing overhead. |
| HTTP/2      | Uses multiplexing to send multiple requests/responses simultaneously over one connection. |

<br>

### What is Multiplexing?
Multiplexing is a technique that allows multiple signals or data streams to be transmitted simultaneously over a single communication channel. In the context of HTTP/2, multiplexing enables multiple HTTP requests and responses to be sent and received in parallel over a single TCP connection, eliminating the need to wait for one request to complete before starting another.

### How Multiplexing Works in HTTP/2
In HTTP/1.1, if a client sends multiple requests, they are processed one after another in a queue (causing delays due to "head-of-line blocking"). With HTTP/2 multiplexing, multiple requests are sent together, and responses are received as soon as they are ready, without waiting for other responses to finish.

### Example Without Multiplexing (HTTP/1.1)
#### Scenario: A Browser Requests Three Files
A web page requires:
- `index.html`
- `style.css`
- `script.js`

Without multiplexing (HTTP/1.1), each request must wait for the previous one to complete:

```
Client: → GET /index.html   (Request 1)  
Server: ← 200 OK (index.html)  

Client: → GET /style.css    (Request 2)  
Server: ← 200 OK (style.css)  

Client: → GET /script.js    (Request 3)  
Server: ← 200 OK (script.js)  
```

**Problem:** Each request is sent sequentially, causing delays and inefficient resource use.

### Example With Multiplexing (HTTP/2)
#### Same Scenario, But Using HTTP/2 Multiplexing
With HTTP/2, all three requests can be sent simultaneously, and responses arrive as they are processed.

```
Client: → [Stream 1] GET /index.html  
        → [Stream 2] GET /style.css  
        → [Stream 3] GET /script.js  
```

**Server processes them in parallel and responds as soon as each file is ready:**

```
Server: ← [Stream 2] 200 OK (style.css)  
        ← [Stream 1] 200 OK (index.html)  
        ← [Stream 3] 200 OK (script.js)  
```

**Benefit:** No waiting! Files are downloaded in parallel, speeding up webpage loading.

### Key Benefits of Multiplexing in HTTP/2
- **Faster Page Load** – Multiple files are sent and received at the same time.
- **Eliminates Head-of-Line Blocking** – No need to wait for one request to finish before sending another.
- **Efficient Use of a Single TCP Connection** – Reduces network congestion and improves performance.
- **Reduces Latency** – Requests and responses happen asynchronously instead of sequentially.

### Summary: HTTP/1.1 vs. HTTP/2 Multiplexing
| Feature                  | HTTP/1.1 (No Multiplexing) | HTTP/2 (With Multiplexing) |
|--------------------------|--------------------------|---------------------------|
| Requests per Connection  | One at a time (sequential) | Multiple at the same time |
| Head-of-Line Blocking    | Yes, requests must wait   | No, responses arrive independently |
| Efficiency               | Slower, multiple connections needed | Faster, single connection |

Multiplexing in HTTP/2 significantly improves the performance of web applications by allowing multiple requests and responses to be handled simultaneously, reducing latency and making better use of network resources.


<br>

## What Can Be Controlled by HTTP

The extensible nature of HTTP has allowed for more control and functionality over time. Features such as caching and authentication were implemented early, while others, like relaxing the origin constraint, were introduced later. Below are common features controllable via HTTP, along with examples.

---

### 1. Caching

HTTP allows control over how documents are cached by instructing proxies and clients on what to cache and for how long.

#### Example: Controlling Cache Behavior

**Server Response:**
```http
HTTP/1.1 200 OK  
Cache-Control: max-age=3600, public  
```
This response tells clients and proxies to cache the document for one hour (3600 seconds).

**Client Request to Ignore Cache:**
```http
GET /index.html HTTP/1.1  
Cache-Control: no-cache  
```
The client requests a fresh copy of the document, ignoring any cached version.

---

### 2. Relaxing the Origin Constraint

Web browsers enforce strict separation between sites to prevent unauthorized access to user data. However, HTTP headers can relax these constraints for controlled cross-origin resource sharing (CORS).

#### Example: Enabling CORS

**Server Response Allowing Cross-Origin Requests:**
```http
HTTP/1.1 200 OK  
Access-Control-Allow-Origin: *  
```
This allows any website to request data from the server.

For restricted access, specific domains can be allowed:
```http
Access-Control-Allow-Origin: https://example.com  
```
Only `example.com` can request data from the server.

---

### 3. Authentication

Some web pages require authentication before granting access. HTTP provides built-in authentication mechanisms.

#### Example: Basic Authentication

**Server Response Requesting Authentication:**
```http
HTTP/1.1 401 Unauthorized  
WWW-Authenticate: Basic realm="Secure Area"  
```

**Client Request with Credentials:**
```http
GET /secure-page HTTP/1.1  
Authorization: Basic dXNlcjpwYXNzd29yZA==  
```
The `Authorization` header contains a Base64-encoded username and password (`user:password`).

---

### 4. Proxy and Tunneling

Proxies enable HTTP requests to traverse network boundaries. They can cache responses, filter requests, or anonymize client identities.

#### Example: Proxy Usage

**Client Request via Proxy:**
```http
GET http://example.com/index.html HTTP/1.1  
Host: example.com  
Proxy-Authorization: Basic dXNlcjpwYXNzd29yZA==  
```
The request is sent through a proxy, with optional authentication.

---

### 5. Sessions

Because HTTP is stateless, cookies enable session management by maintaining user-specific data across requests.

#### Example: Session Management with Cookies

**Server Response Setting a Session Cookie:**
```http
HTTP/1.1 200 OK  
Set-Cookie: session_id=abc123; Path=/; HttpOnly  
```

**Client Request with Session Cookie:**
```http
GET /dashboard HTTP/1.1  
Cookie: session_id=abc123  
```
The server identifies the user session using the `session_id` cookie.

---  

<br>

## HTTP Flow

When a client wants to communicate with a server—whether the final server or an intermediate proxy—it follows these steps:

### 1. Open a TCP Connection
The TCP connection is used to send one or more requests and receive responses. The client may:
- Open a new connection.
- Reuse an existing connection.
- Open multiple TCP connections to the server.

### 2. Send an HTTP Message
HTTP messages (before HTTP/2) are human-readable. With HTTP/2, these messages are encapsulated in frames, making them unreadable directly, though the underlying principle remains the same.

#### Example: Client Request
```http
GET / HTTP/1.1  
Host: developer.mozilla.org  
Accept-Language: fr  
```


### 3. Read the Server Response
The server processes the request and responds accordingly.

#### Example: Server Response
```http
HTTP/1.1 200 OK  
Date: Sat, 09 Oct 2010 14:28:02 GMT  
Server: Apache  
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT  
ETag: "51142bc1-7449-479b075b2891b"  
Accept-Ranges: bytes  
Content-Length: 29769  
Content-Type: text/html  

<!doctype html>… (29769 bytes of the requested web page)  
```


### 4. Close or Reuse the Connection
The client can either close the connection or keep it open for further requests.

If **HTTP pipelining** is activated, multiple requests can be sent without waiting for the first response to be fully received. However, HTTP pipelining proved difficult to implement due to network incompatibilities. In **HTTP/2**, pipelining has been replaced by a more efficient multiplexing mechanism within a single connection.

<br>

## HTTP Messages  
HTTP messages, as defined in HTTP/1.1 and earlier, are human-readable. In HTTP/2, these messages are embedded into a binary structure, a frame, allowing optimizations like compression of headers and multiplexing.   
<br>
There are two types of HTTP messages, requests and responses, each with its own format.  
<br>

### Requests  

An example HTTP request:  

<img src="../Assets/HTTP/http-request.svg" alt="HTTP Diagram" width="600"> 

### HTTP Request Elements

An HTTP request consists of the following elements:

#### 1. HTTP Method
An HTTP method is usually a verb like `GET`, `POST`, or a noun like `OPTIONS` or `HEAD` that defines the operation the client wants to perform. Common operations include:
- **GET**: Fetch a resource.
- **POST**: Submit data (e.g., form values) to be processed.
- **PUT**: Update an existing resource or create a new one.
- **DELETE**: Remove a specified resource.
- **OPTIONS**: Retrieve available communication options for the target resource.
- **HEAD**: Fetch only the headers of a resource (without the body).

#### 2. Resource Path
The path specifies the resource to fetch. It is the URL of the resource, stripped of elements that are obvious from the context. For example:
- Without the protocol (`http://` or `https://`)
- Without the domain (e.g., `developer.mozilla.org`)
- Without the TCP port (e.g., `80` for HTTP, `443` for HTTPS)

Example:
```
GET /articles/page1 HTTP/1.1
```

#### 3. HTTP Version
Specifies the version of the HTTP protocol being used. Common versions include:
- HTTP/1.0
- HTTP/1.1
- HTTP/2
- HTTP/3

#### 4. Headers
Optional headers provide additional information for the server. These include:
- `User-Agent`: Identifies the client (browser, bot, etc.).
- `Accept`: Defines acceptable response types (e.g., `text/html`, `application/json`).
- `Host`: Specifies the server's domain name.
- `Authorization`: Sends authentication credentials.

Example:
```
Host: developer.mozilla.org
User-Agent: Mozilla/5.0
Accept-Language: en-US
```

#### 5. Request Body (Optional)
Some HTTP methods, such as `POST` and `PUT`, include a request body containing the resource being sent. This is similar to response bodies but represents data submitted by the client.

Example (POST request with form data):
```
POST /submit-form HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

name=John&email=john@example.com
```

This structured format ensures that HTTP requests are processed correctly by servers.


### Responses  

An example response:  

<img src="../Assets/HTTP/http-response.svg" alt="HTTP Diagram" width="600">  

### HTTP Response Elements

An HTTP response consists of the following elements:

1. **Version**
   - The version of the HTTP protocol being used.

2. **Status Code**
   - A numeric code indicating whether the request was successful or not, and the reason for the status.
   - Examples:
     - `200 OK` (Successful request)
     - `404 Not Found` (Requested resource not found)
     - `500 Internal Server Error` (Server encountered an error)

3. **Status Message**
   - A short, human-readable description of the status code.
   
4. **HTTP Headers**
   - Provide additional information about the response, such as content type, caching policies, and server details.
   - Example headers:
     ```
     Content-Type: text/html
     Date: Tue, 05 Mar 2024 12:00:00 GMT
     Server: Apache
     ```
   
5. **Body (Optional)**
   - Contains the resource being returned, such as an HTML page, JSON data, or an image.
   - Example:
     ```html
     <!DOCTYPE html>
     <html>
     <head><title>Example</title></head>
     <body><h1>Hello, World!</h1></body>
     </html>
     
<br>

## APIs Based on HTTP

#### Fetch API
The most commonly used API based on HTTP is the Fetch API, which is used to make HTTP requests from JavaScript. The Fetch API replaces the older XMLHttpRequest API and provides a more flexible and modern approach to handling HTTP requests.

##### Example: Fetch API Usage
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
In this example:
- `fetch` is used to send a GET request to `https://api.example.com/data`.
- The response is converted to JSON using `response.json()`.
- The data is then logged to the console.
- Errors are caught and logged.

#### Server-Sent Events (SSE)
Server-Sent Events (SSE) is a one-way service that allows a server to send events to the client using HTTP as a transport mechanism. The client opens a connection using the `EventSource` interface and establishes event handlers.

##### Example: Server-Sent Events (SSE)

**Client-side JavaScript:**
```javascript
const eventSource = new EventSource('https://api.example.com/events');

eventSource.onmessage = function(event) {
  console.log('New event:', event.data);
};

eventSource.onerror = function(error) {
  console.error('EventSource failed:', error);
};
```
- The client creates a connection to `https://api.example.com/events`.
- The `onmessage` event handler processes incoming messages.
- The `onerror` handler deals with any connection issues.

**Server-side (Example using Node.js Express):**
```javascript
const express = require('express');
const app = express();

app.get('/events', (req, res) => {
  res.setHeader('Content-Type', 'text/event-stream');
  res.setHeader('Cache-Control', 'no-cache');
  res.setHeader('Connection', 'keep-alive');

  setInterval(() => {
    res.write(`data: ${JSON.stringify({ message: 'Hello, Client!' })}\n\n`);
  }, 3000);
});

app.listen(3000, () => console.log('Server running on port 3000'));
```
- The server sets necessary headers for SSE.
- It sends a new event to the client every 3 seconds.



