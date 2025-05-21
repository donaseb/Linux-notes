# OSI Model Explained with Google.com Example

The OSI (Open Systems Interconnection) model explains how data travels from your computer to a web server (like Google.com) and back. It has **7 layers**, each representing a step in this communication process.

---

## 🌐 Real-World Example: Accessing `https://www.google.com`

### Preliminary Steps (Before OSI Layers)

Before the OSI model even comes into play, **two key processes happen**:

1. **DNS Resolution**
2. **TCP Handshake**

#### 1. DNS Resolution

* When you search for `https://www.google.com`, your router checks its local cache for an IP address.
* If not found, the query goes to your **ISP's DNS server** to resolve the domain name into an IP address.
* This mapping is stored in DNS records.

#### 2. TCP Handshake (Three-Way Handshake)

* Initiated once the IP is resolved.
* Steps:

  * Your device sends `SYN`
  * Google server responds with `SYN-ACK`
  * Your device replies with `ACK`

---

## 🧱 OSI 7-Layer Model

Once DNS resolution and TCP handshake are complete, your browser initiates a secure HTTP request. Here's how the data travels through the OSI model:

### **L7: Application Layer**

* Initiates the **HTTPS request**.
* Adds headers, cookies, authentication tokens.

### **L6: Presentation Layer**

* Handles **encryption (SSL/TLS)** and formatting.
* Converts data to a format the network understands.

### **L5: Session Layer**

* **Manages session** creation and validation.
* Ensures ongoing connection between your browser and the server.

> 🔸 Layers 5, 6, and 7 are managed by the **browser**.

### **L4: Transport Layer**

* Performs **segmentation** (splitting data into segments).
* Decides whether to use **TCP or UDP** (here, it's TCP).

### **L3: Network Layer**

* **Adds source and destination IP addresses**.
* Routes data via routers as **packets**.

### **L2: Data Link Layer**

* Converts packets into **frames**.
* Adds MAC addresses for local delivery (to switches).

### **L1: Physical Layer**

* Converts frames into **electrical/optical signals**.
* Transmits data over **cables or Wi-Fi**.

---

## 🔁 Return Journey: Server to Client

* Google server processes the request.
* Sends a response that **travels back** through the OSI layers:

  * From **L1 to L7** on your laptop.
  * The browser receives and renders the webpage.

---

## 📘 Summary Table

| Layer | Name         | Function                                    |
| ----- | ------------ | ------------------------------------------- |
| L7    | Application  | HTTP/HTTPS request & response               |
| L6    | Presentation | Data encryption/decryption (SSL/TLS)        |
| L5    | Session      | Session creation and management             |
| L4    | Transport    | Data segmentation, TCP/UDP selection        |
| L3    | Network      | IP addressing and packet routing            |
| L2    | Data Link    | Frame creation, MAC addressing              |
| L1    | Physical     | Transmission via electrical/optical signals |

---

## ✅ OSI vs TCP/IP

* The **OSI model** has **7 layers** and is used as a **standard reference**.
* The **TCP/IP model** merges OSI **Layers 5, 6, and 7** into a single layer called **Application Layer**.

OSI remains useful for teaching and understanding **network communication in detail**.

---

## 🔄 Direction of Data Flow

* **Sender Side:** L7 → L1
* **Receiver Side:** L1 → L7

