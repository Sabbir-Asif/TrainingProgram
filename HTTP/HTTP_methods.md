# HTTP Safe Methods and Idempotent Methods

## HTTP Safe Methods
HTTP safe methods are those that do not modify the server's state. They are only intended for retrieving data and do not cause any side effects when executed multiple times.

### Characteristics of Safe Methods:
- They **do not change** the server's state.
- They are **read-only** operations.
- They can be **cached** and **prefetched** without concern for unintended consequences.

### Examples of Safe Methods:
1. **GET** – Retrieves a resource from the server.
2. **HEAD** – Similar to GET but only returns headers, not the response body.
3. **OPTIONS** – Returns available communication options for a resource.
4. **TRACE** – Echoes the received request to diagnose connection issues.

## HTTP Idempotent Methods
An HTTP method is **idempotent** if making multiple identical requests has the same effect as making a single request. This means that repeated executions of the request **do not** change the system's state beyond the first request.

### Characteristics of Idempotent Methods:
- Multiple identical requests have the **same effect** as a single request.
- Useful for ensuring reliability in distributed systems.
- Helps avoid unintended side effects when retrying requests.

### Examples of Idempotent Methods:
1. **GET** – Repeated requests return the same response (assuming no updates to the resource).
2. **HEAD** – Similar to GET but without the response body.
3. **PUT** – Updates a resource or creates it if it does not exist. Sending multiple PUT requests results in the same state.
4. **DELETE** – Removing a resource multiple times results in the same outcome (resource is deleted or remains absent).
5. **OPTIONS** – Returns the allowed methods for a resource, which does not change with multiple requests.

### Non-Idempotent Methods:
- **POST** – Creates a new resource or triggers a process, which may generate different outcomes for each request.
- **PATCH** – Modifies a resource partially, and repeated requests may have different effects depending on the changes applied.

## Summary Table
| Method  | Safe | Idempotent |
|---------|------|------------|
| GET     | Yes  | Yes        |
| HEAD    | Yes  | Yes        |
| OPTIONS | Yes  | Yes        |
| TRACE   | Yes  | Yes        |
| PUT     | No   | Yes        |
| DELETE  | No   | Yes        |
| POST    | No   | No         |
| PATCH   | No   | No         |


