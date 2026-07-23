# Hypertext Transfer Protocol (HTTP)

## Overview

Hypertext Transfer Protocol (HTTP) is an application-layer protocol used to transfer web pages and other resources between web clients and web servers. It follows a request-response model, where a client sends a request and the server returns a response.

By itself, HTTP does **not** provide encryption, authentication, or integrity protection.

## Key Concepts

### Request-Response Model

HTTP communication begins when a client, such as a web browser, sends a request to a web server.

The server processes the request and returns an HTTP response containing:

- Status code
- Headers
- Requested content (if available)

### HTTP Methods

Common HTTP methods include:

- **GET** – Retrieve a resource
- **POST** – Submit data to a server
- **PUT** – Create or replace a resource
- **DELETE** – Remove a resource

These methods tell the server what action the client wants to perform.

### Status Codes

Servers include status codes in their responses to indicate the outcome of a request.

Common status codes include:

- **200 OK** – Request succeeded
- **301 Moved Permanently** – Resource has moved
- **403 Forbidden** – Access denied
- **404 Not Found** – Resource does not exist
- **500 Internal Server Error** – Server encountered an error

### Port 80

HTTP uses **TCP port 80** by default.

Because traffic is transmitted in plaintext, anyone who intercepts the communication may be able to read its contents.

### Stateless Protocol

HTTP is stateless, meaning each request is processed independently.

Web applications use mechanisms such as cookies and session tokens to maintain user sessions across multiple requests.

## Why It Matters

Understanding HTTP is essential because nearly all web applications rely on it. Security professionals analyze HTTP traffic during penetration testing, web application assessments, malware investigations, and incident response.

Since HTTP provides no encryption, sensitive information should never be transmitted over HTTP when HTTPS is available.

## Common Uses

- Browsing websites
- Accessing web applications
- Communicating with web servers
- REST APIs
- Downloading web content

## Best Practices

- Use HTTPS instead of HTTP whenever possible.
- Never transmit sensitive information over plaintext HTTP.
- Understand common HTTP methods and status codes.
- Inspect HTTP traffic during web application testing.
- Redirect HTTP traffic to HTTPS when appropriate.
