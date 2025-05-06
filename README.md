# Networking


#### 🥇 1. Application Layer (Layer 7)
Most important for developers.

Provides the interface that allows users and software applications to communicate over a network.

It is responsible for user-level interactions, meaning it's the layer where you send or receive data using your apps.

Think of it as the "face" of the system where humans interact with technology.


Involves protocols like:

HTTP/HTTPS (web apps)

SMTP (email)

FTP/SFTP (file transfers)

WebSocket, gRPC, REST APIs

🛠️ Why it matters: When you're building REST APIs, web applications, or integrating services, you're directly working at this layer.

#### 🥈 2. Transport Layer (Layer 4)
The Transport Layer is responsible for ensuring end-to-end communication between two devices (or programs) over a network. It does the following:

Breaks down data into smaller chunks called segments (for example, a large file is split into smaller parts).

Ensures data is delivered reliably by managing error detection, flow control, and data acknowledgment.

Reorders the segments if they arrive out of order.

Provides flow control to prevent data overload (so the receiver can handle it).

The two main protocols used in this layer are TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).

TCP (reliable, used in HTTP)

UDP (faster, used in streaming/gaming)

🛠️ Why it matters: Developers must understand TCP vs UDP, port numbers, and connection handling for tuning performance or debugging network issues.



#### 🥉 3. Network Layer (Layer 3)
Handles routing and IP addressing.

Protocol: IP (IPv4/IPv6)

🛠️ Why it matters: Useful for understanding IP whitelisting, firewalls, VPNs, and network configurations (e.g., in cloud deployments).

🔧 Optional but Helpful:
Data Link Layer (Layer 2) and Physical Layer (Layer 1) are more relevant for hardware/network engineers.

Session (Layer 5) and Presentation (Layer 6) are mostly handled by libraries/frameworks and rarely need direct developer attention.


#### Session Layer 

It is responsible for managing and controlling the dialogue (the conversation) between two devices or applications. It ensures that the communication sessions between devices are properly established, maintained, and terminated.

