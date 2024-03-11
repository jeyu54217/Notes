- [Token Storage](#token-storage)
  - [Local Storage](#local-storage)
  - [Session Storage](#session-storage)
  - [Cookies](#cookies)
  - [IndexedDB](#indexeddb)
  - [Memory (State Management Libraries)](#memory-state-management-libraries)
  - [HTTP Headers](#http-headers)

  
# Token Storage 
| Feature               | LocalStorage                           | SessionStorage                         | Cookies                             | IndexedDB                           | Redux                               | HTTP Headers                       |
|-----------------------|----------------------------------------|----------------------------------------|-------------------------------------|-------------------------------------|-------------------------------------|------------------------------------|
| Lifespan              | Persistent until manually cleared      | Lasts for the duration of the page session | Expires based on set duration       | Persistent until manually cleared   | Persistent until page reload        | Only during HTTP request/response  |
| Accessibility         | Any window/tab under the same origin   | Same tab/window                        | Any request to the server, across origins | Any window/tab under the same origin | Anywhere within React app           | Server and client during HTTP transactions |
| Size Limit            | ~5MB per domain                        | ~5MB per domain                        | ~4KB per cookie                     | No fixed limit, but practical limits apply | Limited by JavaScript heap size     | Limited by server/client processing capacity |
| Security              | Vulnerable to XSS attacks              | Vulnerable to XSS attacks              | Configurable for HttpOnly, secure; vulnerable to CSRF | Vulnerable to XSS attacks            | Secure, stored in JavaScript memory | Secure if used with HTTPS; not stored client-side |
| HTTP Access           | No                                     | No                                     | Yes, with every HTTP request        | No                                   | No                                  | Directly used in HTTP headers      |
| Use Case              | Long-term data persistence             | Short-term data persistence           | Authentication, state across requests | Large amounts of data, structured storage | Application state management        | Stateless authentication, API token transmission |
| Server Side Access    | No                                     | No                                     | Yes                                 | No                                   | No                                  | Yes, during request/response       |
| Synchronization       | Across all browser tabs/windows        | Limited to the creating tab/window     | Across all requests to the server   | Across all browser tabs/windows     | Within the single page application | Not applicable                     |
| Complexity            | Simple                                 | Simple                                 | Moderate, due to security configuration | Moderate to high, due to API complexity | Moderate, due to state management complexity | Simple, but requires server-side handling |


## Local Storage
  - **Advantages**: Simple API; large storage capacity; data persists across browser sessions.
    - Persistence: Data remains stored even after the browser is closed, allowing for persistent state across sessions.
    - Capacity: Offers more storage capacity (~5MB) compared to cookies.
    - Ease of Use: Simple API for storing and retrieving data.
  - **Disadvantages**: Not secure; accessible via JS; not suitable for sensitive data
    - Security Risks: Vulnerable to cross-site scripting (XSS) attacks. If an attacker can execute JavaScript on your site, they can retrieve the stored tokens.
    - No HTTP Access: Cannot be accessed by the server directly; requires JavaScript to send data in HTTP headers.
  
## Session Storage
- **Advantages**: Simple API; data isolated to the window/tab; automatically clears after session. 
  - Tab-Specific Data: Scoped to the lifetime of a tab, making it suitable for storing data that should not persist across sessions or tabs.
  - Capacity: Similar to LocalStorage, offers ~5MB of storage.
  - Isolation: Data stored is not shared between tabs, reducing the risk of data leakage between sessions.
- **Disadvantages**: Limited to window/tab scope; not secure; accessible via JS.
  - Limited Lifespan: Data is cleared when the tab is closed, limiting its use for long-term persistence.
  - Security Risks: Similar to LocalStorage, it's vulnerable to XSS attacks.

## Cookies
  - **Advantages**: Accessible by the server; configurable for security (HttpOnly, Secure attributes); domain and path scope.
    - Server Access: Can be accessed by the server, making them suitable for authenticating user requests.
    - Expiration Control: Can set expiration dates for automatic clearing.
    - Scope Control: Can configure domain and path scope for tighter security.
  - **Disadvantages**: Limited storage size; performance overhead on every HTTP request; complex to manage securely.
    - Size Limitation: Limited to ~4KB, making it unsuitable for storing large amounts of data.
    - Performance: Each HTTP request includes cookies, increasing the amount of data transmitted.
    - Security: Requires careful configuration (HttpOnly, Secure flags) to mitigate security risks (XSS, CSRF).

## IndexedDB
  - **Advantages**: Large storage capacity; supports structured data; operates asynchronously.
  - **Disadvantages**: API is more complex; requires more boilerplate code; vulnerable to XSS.
  - 
## Memory (State Management Libraries)
  - **Advantages**: Centralized state management; facilitates data flow between components; not directly accessible via JS console.
  - **Disadvantages**: Requires additional library and setup; state is not persistent without additional middleware or storage mechanism.
  
## HTTP Headers
  - **Advantages**: Secure transmission of tokens; not stored in client-side storage; supports stateless applications.
  - **Disadvantages**: Not a storage mechanism; requires backend implementation; tokens must be attached to every request.
