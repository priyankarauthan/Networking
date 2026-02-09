# Networking & Security

```

Browser / Client
    |
    | 1️⃣ Client Hello (supported ciphers)
    v
Server
    |
    | 2️⃣ Server Hello + Certificate (public key)
    v
Client
    |
    | 3️⃣ Verify certificate (CA check) - The client verifies a certificate by checking its signature, certificate chain, expiry, domain name, and trust against a known Certificate Authority (CA).
    | 4️⃣ Generate session key
    | 5️⃣ Encrypt session key using server public key
    v
Server
    |
    | 6️⃣ Decrypt using private key
    |
🔐 Secure encrypted communication starts
```


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

# HTTP vs HTTPS
| Feature | HTTP | HTTPS |
|------|------|------|
| Full form | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
| Security | ❌ Not secure | ✅ Secure |
| Data encryption | ❌ No encryption | ✅ Encrypted using SSL/TLS |
| Data visibility | Plain text (readable) | Encrypted (unreadable) |
| Protection from attackers | ❌ No | ✅ Yes |
| Website authentication | ❌ No verification | ✅ Server identity verified |
| URL prefix | http:// | https:// |
| Browser indicator | ❌ No lock / "Not Secure" | 🔒 Lock icon |
| Default port | 80 | 443 |
| Risk of data theft | High | Very low |
| Use case | Public or non-sensitive data | Login, payments, APIs |
| SEO ranking | Lower | Higher (preferred by Google) |
| Modern browser support | Limited / discouraged | Fully supported |



## What does “make an HTTPS API” mean?

It means:

Your API runs on HTTPS (not HTTP)

All requests & responses are encrypted

Browser / client sees 🔒 lock

👉 This is done by configuring SSL/TLS on your server, not by changing API code logic


## To make an HTTPS API, you need:

1) SSL certificate

2) Private key

3)Server configured to use them

4) API exposed over HTTPS port (443 or custom)

## How To make an HTTPS API Step-by-step 

####  Step 1: Get an SSL Certificate

You have 3 options:

###### Option A: Self-signed (for local/dev)

Used for learning & testing

Browser will warn “Not Secure”

###### Option B: CA-signed (prod)

From Let’s Encrypt, DigiCert, etc.

Browser trusts it

```
 Create a self-signed certificate (local)

Run this command:

keytool -genkeypair \
  -alias myapi \
  -keyalg RSA \
  -keysize 2048 \
  -storetype PKCS12 \
  -keystore keystore.p12 \
  -validity 365


This creates:

keystore.p12

Contains:

private key 🔐

public key 🔑

certificate 📜
```

### Step 2: Configure Spring Boot for HTTPS
application.yml (or application.properties)
```
server:
  port: 8443
  ssl:
    enabled: true
    key-store: classpath:keystore.p12
    key-store-password: changeit
    key-store-type: PKCS12
    key-alias: myapi
```


📌 Place keystore.p12 inside:

   src/main/resources/

### Step 3: Create a normal REST API
```
@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello over HTTPS!";
    }
}
```

No HTTPS code needed here ❗
HTTPS works at server level, not controller level.

### Step 4: Run and test

Start app and hit:

https://localhost:8443/api/hello


✔ Data is encrypted
✔ API is HTTPS
⚠ Browser warning (self-signed)
### Step 5: Redirect HTTP → HTTPS (important)

To prevent accidental HTTP usage:

server:
  port: 8443


And disable HTTP or redirect it via:

Spring Security

NGINX / Load Balancer

## Where is security actually coming from?

| Component | Role |
|---------|------|
| SSL Certificate | Server identity verification |
| Private Key | Decryption of encrypted data |
| Public Key | Encryption of data |
| HTTPS | Secure, encrypted communication channel |
| JWT / OAuth | API authentication and authorization |




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

