# Multi-Threaded Proxy Web Server

This project implements a multi-threaded proxy web server in C. It can handle multiple client requests concurrently and features a caching mechanism to improve performance.

## Project Flow

1.  **Initialization:**
    *   The proxy server starts up and binds to a specified port.
    *   It creates a pool of worker threads to handle incoming client requests.

2.  **Client Connection:**
    *   A client (e.g., a web browser) establishes a connection to the proxy server.
    *   The proxy server accepts the connection and assigns it to an available worker thread.

3.  **Request Handling:**
    *   The worker thread receives the HTTP request from the client.
    *   It parses the request to extract the target server and the requested resource.
    *   It checks if the requested resource is in the cache.
        *   If found, it retrieves the cached response and sends it to the client.
        *   If not found, it proceeds to fetch the resource from the target server.

4.  **Target Server Interaction:**
    *   The worker thread establishes a connection to the target server.
    *   It forwards the client's request to the target server.
    *   It receives the response from the target server.

5.  **Response Handling:**
    *   The worker thread parses the response from the target server.
    *   It stores the response in the cache (if caching is enabled).
    *   It forwards the response to the client.

6.  **Connection Closing:**
    *   The worker thread closes the connection to the target server.
    *   The client closes the connection to the proxy server.

## Project Architecture

The project follows a modular design, with the following key components:

*   **`main.c`:** Entry point of the program, responsible for initializing the proxy server and managing worker threads.
*   **`proxy_core.c`:** Handles the core logic of the proxy server, including accepting client connections, assigning them to worker threads, and managing the request/response cycle.
*   **`proxy_parse.c`:**  Provides functions for parsing HTTP requests and responses.
*   **`proxy_cache.c`:** Implements the caching mechanism, storing and retrieving web pages to improve performance.
*   **`proxy_utils.c`:** Contains utility functions for logging, error handling, and other common tasks.

The code is organized into a `src` directory for source files and an `include` directory for header files.
 **structure**

Proxy_web_server/
├── res/
├── src/
│   ├── proxy_core.c
│   ├── proxy_parse.c
│   ├── proxy_cache.c
│   ├── proxy_utils.c
│   └── main.c
├── include/
│   ├── proxy_core.h
│   ├── proxy_parse.h
│   ├── proxy_cache.h
│   └── proxy_utils.h
└── Makefile
