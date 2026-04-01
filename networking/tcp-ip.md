# TCP/IP Model

The TCP/IP model is a networking model used to understand how data travels across the internet.

It has **4 layers**.

## Layers of TCP/IP Model

### 4) Application Layer
Responsible for communication between applications and the network.

Examples:
- HTTP
- HTTPS
- FTP
- DNS
- SMTP

Purpose: Provides services to user applications.

---

### 3) Transport Layer
Responsible for end-to-end communication and data delivery.

Protocols:
- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

Purpose: Ensures data is delivered correctly between devices.

---

### 2) Internet Layer
Responsible for logical addressing and routing of packets.

Protocol:
- IP (Internet Protocol)

Purpose: Determines how packets travel across networks.

---

### 1) Network Access Layer
Responsible for transmitting data over the physical network.

Examples:
- Ethernet
- WiFi

Purpose: Handles physical transmission of data.

---

## Simple Data Flow

Application → Transport → Internet → Network Access → Network

## Diffrence b/w OSI and TCP/IP Model :-

- Layers vs. Practicality  
The OSI model consists of 7 layers, which makes it great for teaching and fixing specific hardware problems. The TCP/IP model has 4 layers, focusing on efficiency and speed instead of strict separation.  

- History and Development  
TCP/IP was developed first; the protocols came first, and the model was created to describe them. OSI followed a different path—the model was created first as a set of standards, then protocols were built to fit those standards.  

- Vertical Integration  
In the OSI model, the Session and Presentation layers are separate. In the TCP/IP model, these functions are all part of the Application layer. This is why network engineers often mention "Layer 7" (Application) when discussing web traffic, even if they are actually on a TCP/IP network.  

- Reliable vs. Best-Effort  
The OSI model strictly uses connection-oriented methods at the network layer. In contrast, the TCP/IP model supports both connection-oriented (TCP) and "best-effort" connectionless (UDP) communication, making it more flexible for things like live video streamings.


