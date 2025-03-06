# Two-Week HTTP & REST Study Plan  

This structured study plan is designed to help you systematically cover HTTP and REST concepts over 14 days. The schedule follows a logical progression, starting with HTTP fundamentals, moving to REST, and concluding with advanced topics.  

---

## **Week 1: HTTP Fundamentals & REST Basics**  

### **Day 1: Introduction to HTTP**  
**Read:**  
- [HTTP Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)  
- [HTTP Basics (NTU)](https://personal.ntu.edu.sg/ehchua/programming/webprogramming/HTTP_Basics.html)  

**Hands-on Practice:**  
- Open Chrome/Firefox DevTools and inspect HTTP requests in the Network tab.  

### **Day 2: HTTP Methods & Status Codes**  
**Read:**  
- [HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)  
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)  

**Hands-on Practice:**  
- Use Postman or cURL to send HTTP requests (GET, POST, PUT, DELETE) and observe status codes.  

### **Day 3: HTTP Headers & Request/Response Structure**  
**Read:**  
- [HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)  

**Hands-on Practice:**  
- Inspect request and response headers using browser DevTools.  
- Experiment with custom headers in Postman.  

### **Day 4: Introduction to RESTful Web Services**  
**Read:**  
- [IBM RESTful Web Services Guide](https://developer.ibm.com/articles/ws-restful/)  
- [REST API Tutorial](https://www.restapitutorial.com/)  

**Hands-on Practice:**  
- Make a request to an open REST API (e.g., JSONPlaceholder) using Postman.  

### **Day 5: REST API Design & Principles**  
**Read:**  
- [REST Cookbook](http://restcookbook.com/)  
- Learn about statelessness, resource-based URLs, and CRUD operations in REST.  

**Hands-on Practice:**  
- Compare REST with traditional web APIs (SOAP/XML-RPC).  

### **Day 6: REST APIs and JSON**  
**Read:**  
- [JSON Format (Wikipedia)](https://en.wikipedia.org/wiki/JSON)  
- [JSON Specification](https://www.json.org/json-en.html)  

**Hands-on Practice:**  
- Use Postman to send REST API requests and receive JSON responses.  
- Create a simple JSON file and parse it using JavaScript.  

### **Day 7: REST API Best Practices & Authentication**  
**Read:**  
- RESTful API Security  
- [Introduction to Authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication)  

**Hands-on Practice:**  
- Explore authentication methods such as API keys, OAuth, and JWT tokens.  

---

## **Week 2: HTTP Advanced Topics & Optional Readings**  

### **Day 8: HTTP Caching & Cookies**  
**Read:**  
- [HTTP Caching](https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching)  
- [HTTP Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)  

**Hands-on Practice:**  
- Examine Cache-Control headers in Chrome DevTools.  
- Set and modify cookies using JavaScript.  

### **Day 9: Cross-Origin Resource Sharing (CORS)**  
**Read:**  
- [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)  

**Hands-on Practice:**  
- Attempt making an API request from a different origin and observe CORS errors.  

### **Day 10: HTTP Connection Management & Evolution**  
**Read:**  
- [Connection Management in HTTP/1.x](https://developer.mozilla.org/en-US/docs/Web/HTTP/Connection_management_in_HTTP_1.x)  
- [Evolution of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP)  

**Hands-on Practice:**  
- Compare HTTP/1.1 and HTTP/2 performance using browser DevTools.  

### **Day 11: Advanced REST – Richardson Maturity Model**  
**Read:**  
- [Richardson Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html)  

**Hands-on Practice:**  
- Analyze an existing API's REST maturity level.  

### **Day 12: HTTPS – Secure HTTP**  
**Read:**  
- [What is HTTPS? (Wikipedia)](https://en.wikipedia.org/wiki/HTTPS)  
- [Why HTTPS Matters (Google)](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https)  
- [Intro to Security Terminology](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/intro-to-security-terminology)  
- [Enable HTTPS](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https)  
- [Google HTTPS Guide](https://support.google.com/webmasters/answer/6073543?hl=en)  

**Hands-on Practice:**  
- Use OpenSSL to inspect an HTTPS certificate: `openssl s_client -connect example.com:443`  

### **Day 13: Caching Deep Dive (Optional)**  
**Read:**  
- [Things Caches Do](https://tomayko.com/blog/2008/things-caches-do)  
- [Cache Documentation](https://www.mnot.net/cache_docs/)  
- [Optimizing Content Efficiency](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)  
- [RFC 7234 - Caching](https://tools.ietf.org/html/rfc7234) (Optional)  

**Hands-on Practice:**  
- Experiment with browser cache settings and examine HTTP cache headers.  

### **Day 14: Final Review & Hands-on Practice**  
- Revise key topics and revisit any unclear concepts.  
- Develop a small REST API using Node.js/Express or Django REST Framework.  
- Discuss learnings in forums or with peers.  

---

## **Study Tips**  
- Focus on understanding concepts rather than memorization.  
- Use browser DevTools to observe real-world HTTP interactions.  
- Use Postman or cURL for testing API requests.  
- If a concept is unclear, continue studying—it will make sense over time.  

This study plan balances reading, practical exercises, and revision to ensure a solid understanding of HTTP and REST. Let me know if any modifications are needed.

