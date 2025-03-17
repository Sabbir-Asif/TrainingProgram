# Evolution of HTTP  
**HTTP** (HyperText Transfer Protocol) was developed by Tim Berners-Lee and his team between 1989-1991.  

## Protocol  
A protocol is a set of rules that define how data is transmitted and received over a network. It ensures that communication between devices is standardized and reliable.  
### Examples of Protocols: 

**HTTP (Hypertext Transfer Protocol)**  
Used for transferring web pages and resources on the internet.  
```
GET /index.html HTTP/1.1
Host: example.com
```
This request asks the server at ```example.com``` for the ```index.html``` page.  

**HTTPS (Hypertext Transfer Protocol Secure)**  
Secure version of HTTP, encrypting data using SSL/TLS.  
For example:  
When you visit ```https://google.com```, the connection is encrypted to protect your data.

**FTP (File Transfer Protocol)**  
Used for transferring files between a client and a server.
```
ftp://ftp.example.com
```
This connects to an FTP server to upload or download files.  

**SMTP (Simple Mail Transfer Protocol)**  
Used for sending emails.  

**TCP/IP (Transmission Control Protocol / Internet Protocol)**  
TCP/IP is the foundation of the internet. It is a suite of protocols that define how data is sent and received across networks.
Here,  

- **IP (Internet Protocol):** Responsible for addressing and routing data packets.  
- **TCP (Transmission Control Protocol):** Ensures reliable data transmission by checking for errors and delivering packets in order.  

**DNS (Domain Name System)**  

DNS translates human-readable domain names (like ```google.com```) into IP addresses (like ```142.250.190.46```), which computers use to communicate.  

How DNS Works:

- You type ```example.com``` in your browser.  
- Your device queries a DNS server to find the IP address.  
- The DNS server responds with the correct IP (e.g., ```93.184.216.34```).
- Your browser connects to the server at that IP address to load the webpage.  
```
nslookup google.com
```
This command returns the IP address of ```google.com``` from a DNS server.  

## Invention of the World Wide Web

In 1989, Tim Berners-Lee, while working at CERN, proposed a hypertext system over the internet. Initially called "Mesh," it was later renamed the **World Wide Web** in 1990.

The Web was built on existing **TCP/IP** protocols and had four key components:

1. **HTML (HyperText Markup Language)** – A format to represent hypertext documents.  
2. **HTTP (HyperText Transfer Protocol)** – A protocol to exchange these documents.  
3. **WorldWideWeb** – The first web browser, which could display and edit pages.  
4. **httpd** – The first web server to host and serve web pages.  

By the end of 1990, these components were complete. The first web servers started running outside CERN in early 1991.  

On **August 6, 1991**, Tim Berners-Lee announced the project on the <a href="https://www.w3.org/People/Berners-Lee/1991/08/art-6484.txt">alt.hypertext </a> newsgroup. This is considered the official public launch of the World Wide Web.  

## What is httpd?  
```httpd``` stands for HTTP Daemon, which is a software program that runs in the background and serves web pages to clients (browsers) over the HTTP protocol. It acts as a web server, processing requests and delivering HTML, images, and other resources to users.  
### Key Points About httpd  
- **First Web Server**: The earliest version of httpd was developed by Tim Berners-Lee in 1990 at CERN, as part of the World Wide Web.  
- **Daemon Process**: The "d" in httpd stands for daemon, meaning it runs continuously, waiting for requests.  
- **Handles HTTP Requests**: When a user visits a website, httpd receives the request, finds the requested file, and sends it back to the browser.  
- **Apache HTTP Server**: Today, the most widely used ```httpd``` implementation is the Apache HTTP Server, which is commonly called Apache.  

## Difference Between Apache HTTP Server (`httpd`) and Express Server (Node.js)

### **1. Apache HTTP Server (`httpd`)**
- **Type**: Traditional, full-featured web server.
- **Purpose**: Primarily serves static files (HTML, images, CSS) and supports dynamic content through modules (e.g., PHP, CGI).
- **Configuration**: Configured via text files (`httpd.conf`) and typically serves content or forwards requests to other software.
- **Programming Language**: Written in C/C++; no coding required unless using PHP or other modules.
- **Performance**: Uses a process-based architecture, handling many simultaneous requests but can be less efficient under high loads.
- **Usage**: Often used in **LAMP stacks** (Linux, Apache, MySQL, PHP) for serving websites and PHP applications.


### 2. Express Server (Node.js)
- **Type**: A lightweight web framework for Node.js, designed for dynamic applications.
- **Purpose**: Handles both static and dynamic content, often used for **REST APIs** and real-time apps.
- **Configuration**: Configured via JavaScript code, defining routing, middleware, and request handling.
- **Example Code**:
    ```javascript
    const express = require('express');
    const app = express();

    app.get('/', (req, res) => {
        res.send('Hello World!');
    });

    app.listen(3000, () => {
        console.log('Server is running on port 3000');
    });
    ```
- **Programming Language**: Written in JavaScript (Node.js), offering flexibility for server-side logic.
- **Performance**: Uses asynchronous, non-blocking I/O, making it highly scalable and efficient for I/O-heavy applications.
- **Usage**: Commonly used for REST APIs, single-page applications, and real-time applications**.

### **Key Differences**

| Feature                | **Apache HTTP Server (`httpd`)**        | **Express Server (Node.js)**       |
|------------------------|----------------------------------------|------------------------------------|
| **Type**               | Full-featured web server              | Web framework for Node.js         |
| **Static vs Dynamic**  | Serves static files, dynamic via modules | Handles both static and dynamic content via JavaScript |
| **Programming Language** | C/C++ (low-level)                    | JavaScript (Node.js)              |
| **Server Setup**       | Configured via `httpd.conf`            | Configured via JavaScript         |
| **Performance**        | Process-based, good for static content | Asynchronous, non-blocking, great for real-time apps |
| **Common Use Cases**   | Websites, PHP apps                    | REST APIs, real-time apps, SPAs   |


## How HTTP Requests Differ

**Apache HTTP Server**:  
  - When a request is made (e.g., `GET /index.html`), Apache retrieves and serves the file from the disk based on configuration files.
  
**Express Server**:  
  - When a request is made (e.g., `GET /api/data`), Express executes JavaScript code to dynamically generate a response.

### **Example Comparison**
**Apache (`httpd`)**:  
  - Request: `http://localhost/index.html`  
  - Response: Serves the `index.html` file directly from the server.

**Express (Node.js)**:  
  - Request: `http://localhost/api/data`  
  - Response: Fetches data from a database and returns JSON.

