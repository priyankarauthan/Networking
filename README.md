# Networking & Security

### 🔹 Step 1: Browser says “Hello”

Your browser sends:

Hello Server,
I want a secure connection.
Here are encryption methods I support.


This is called Client Hello.

### 🔹 Step 2: Server sends SSL Certificate

Server replies with:

SSL Certificate (contains):

Server’s Public Key

Website name

Issuing Authority (CA)

Example:

Here is my certificate.
Here is my public key.

### 🔹 Step 3: Browser verifies the certificate

Your browser checks:

Is the certificate issued by a trusted CA?

Is it expired?

Is it for the same website?

If ❌ invalid → browser shows “Not Secure”

If ✅ valid → continue

### 🔹 Step 4: Browser creates a Secret Key

Now browser:

generates a random symmetric key (secret key)

encrypts it using server’s public key

sends it to server

Only the server can decrypt it using its private key

### 🔹 Step 5: Secure connection established

Now:

Browser and Server both have same secret key

All future data is encrypted using this key

This is fast and secure ✅

### 🔹 Step 6: Encrypted communication

When you:

submit a form

log in

make a payment

Data flow:

Browser → encrypts data → Server
Server → decrypts data


No one else can understand it 🚫

### 7️⃣ Why not use public/private key for everything?

Because:

Asymmetric encryption = slow

Symmetric encryption = fast

So SSL uses:

🔑 Asymmetric → only for key exchange

🔐 Symmetric → for actual data

### 8️⃣ Simple real-life analogy 🧠

Imagine:

Server gives you an open lock (public key)

You put your secret key inside a box

Lock it with that open lock

Only server has the key to open the lock (private key)

After that:

both use the same secret key to talk privately

### 9️⃣ What happens if SSL is not there?
Without SSL	With SSL
Password visible	Password encrypted
Data can be changed	Data integrity protected
Fake website risk	Website verified
HTTP	HTTPS
### 🔟 Summary (Quick revision)

SSL secures browser ↔ server

Uses certificates to verify identity

Uses encryption to protect data

HTTPS = HTTP + SSL

Protects passwords, payments, personal data


# 🔑 Public Key vs Private Key — explained simply

| Feature | Public Key | Private Key |
|------|-----------|-------------|
| Visibility | Shared openly | Kept secret |
| Who owns it | Shared with everyone | Only the owner (server/user) |
| Main purpose | Encrypt data | Decrypt data |
| Used by | Anyone who wants to send secure data | Only the key owner |
| Can it be shared? | ✅ Yes | ❌ Never |
| Stored where | SSL Certificate, Browser | Secure server / keystore |
| Risk if leaked | Low | Very high |
| Used in SSL/TLS | Yes (sent to browser) | Yes (kept on server) |
| Used for digital signature | Verify signature | Create signature |
| Speed impact | Slower (asymmetric) | Slower but critical |




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

