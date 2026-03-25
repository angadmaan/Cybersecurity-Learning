## What is HTTP
HTTP (HyperText Transfer Protocol) is a protocol used for communication between a web browser and a web server.

When a user visits a website, the browser sends an HTTP request to the server and the server sends back an HTTP response.

Example:
Browser → HTTP Request → Web Server  
Server → HTTP Response → Browser

---

## What is HTTPS
HTTPS (HyperText Transfer Protocol Secure) is the secure version of HTTP.

It uses encryption through SSL/TLS to protect data during communication between the browser and the server.

Example:
https://github.com

HTTPS prevents attackers from intercepting or modifying data.

---

## HTTP Request

An HTTP request is sent from the client (browser) to the server.

A request usually contains:
- Request Method
- URL
- Headers
- Body (optional)

Example request line:

GET /index.html HTTP/1.1

---

## HTTP Response

An HTTP response is sent from the server back to the client.

It usually contains:
- Status Code
- Headers
- Response Body

Example response:

HTTP/1.1 200 OK

---

## Common HTTP Methods

GET  
Used to request data from a server.

POST  
Used to send data to the server.

PUT  
Used to update existing data.

DELETE  
Used to remove data from the server.

---

## Common HTTP Status Codes

200 – Request successful

301 – Resource moved permanently

403 – Access forbidden

404 – Page not found

500 – Internal server error

---

## Why HTTP is Important in Cybersecurity

Many web attacks target HTTP communication.

Security professionals analyze HTTP traffic to detect vulnerabilities such as:

- SQL Injection
- Cross-Site Scripting (XSS)
- Authentication bypass

## HTTPS Request

An HTTPS request works the same way as an HTTP request but the communication is encrypted using SSL/TLS.

The browser first establishes a secure connection with the server before sending the request.

Example request line:

GET /index.html HTTPS/1.1


---

## HTTPS Response

The server sends an encrypted response back to the browser.

The data is protected during transmission so attackers cannot easily read or modify it.

Example response:

HTTPS/1.1 200 OK


---

## Features of HTTPS

Encryption  
Data is encrypted so that attackers cannot read the communication.

Authentication  
The server proves its identity using a digital certificate.

Data Integrity  
Ensures that the data is not modified during transmission.


---

## SSL/TLS

HTTPS uses SSL (Secure Sockets Layer) or TLS (Transport Layer Security) protocols to secure communication between the client and server.

TLS is the modern and more secure version.


---

## Why HTTPS is Important

Protects sensitive information such as:

- Passwords
- Login credentials
- Payment information
- Personal data

It prevents attacks like:

- Man-in-the-Middle attacks
- Data interception
