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
Manages end-to-end communication, reliability, and flow control.

Protocols:

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

