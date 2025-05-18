# Networking Fundamentals

## IP Address

- An IP address is used to provide a unique address to a device connected to your network.
- IP addresses follow standards such as **IPv4** or **IPv6**.
- Using **IPv4**, a unique identification number is generated in formats like:
  - `172.16.3.4`
  - `10.1.2.4`
- To find the IP address of your device:
  - On Windows: `ipconfig`
  - On Linux/macOS: `ifconfig`
- An example IPv4 address is `192.3.5.7`. In this:
  - Each number before a dot (.) is called an **octet** and can range from `0` to `255`.
  - So the full range of IP addresses in IPv4 is calculated as:
    ```
    0-255.0-255.0-255.0-255
    ```
- Why is the range `0-255` and not `0-1000`?
  - Computers operate in **bits** and **bytes**.
  - Each number (octet) in the IP address is **1 byte**, or **8 bits**.
  - With 8 bits, you can represent `2^8 = 256` values (i.e., `0` to `255`).
- Therefore, an IPv4 address is:
  - `32 bits` long (or `4 bytes`)
  - Represented as:
    ```
    --------.--------.--------.--------
    (8 bits) (8 bits) (8 bits) (8 bits)
    ```
### Breakdown of Each 8-bit Byte in an IP Address

- Each part (octet) of an IPv4 address is 8 bits, and each bit represents a power of 2:
- Bit Position: 7 6 5 4 3 2 1 0
- Value: 2⁷ 2⁶ 2⁵ 2⁴ 2³ 2² 2¹ 2
- 
- This means each bit in a byte represents a value as follows:
  - `2⁰ = 1`
  - `2¹ = 2`
  - `2² = 4`
  - `2³ = 8`
  - `2⁴ = 16`
  - `2⁵ = 32`
  - `2⁶ = 64`
  - `2⁷ = 128`

- If all bits are set to `1`, the value of the byte is:
- 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255
- So, each octet in an IP address can range from `0` (all bits off) to `255` (all bits on).
- Let's break down `192.64.32.7`:

---

#### ✅ Octet 1: `192`

- Binary: `11000000`
- Explanation: 192 = 128 (2⁷) + 64 (2⁶) + 0 + 0 + 0 + 0 + 0 + 0= 128 + 64 = 192

---

#### ✅ Octet 2: `64`

- Binary: `01000000`
- Explanation:64 = 0 + 64 (2⁶) + 0 + 0 + 0 + 0 + 0 + 0 = 64
  
---

#### ✅ Octet 3: `32`

- Binary: `00100000`
- Explanation: 32 = 0 + 0 + 32 (2⁵) + 0 + 0 + 0 + 0 + 0 = 32

---

#### ✅ Octet 4: `7`

- Binary: `00000111`
- Explanation: 7 = 0 + 0 + 0 + 0 + 0 + 4 (2²) + 2 (2¹) + 1 (2⁰)= 4 + 2 + 1 = 7

---

### ✅ Final Binary Format of `192.64.32.7`:

- 11000000.01000000.00100000.00000111

- Each part is 8 bits (1 byte) long, and the full IPv4 address is 32 bits in total.
# Subnetting and Ports :

## 🔹 What is a Subnet?
- A **subnet** is short for "sub-network" — it refers to dividing a large network into smaller logical networks.
- For example, if a network has ~65,000 IP addresses, it can be split into multiple subnets based on departments or security needs:
  - One subnet can be used by the **Finance Team** (secure, isolated).
  - Another subnet can be used by **general employees** (open).

### 🔐 Why Subnetting?
- **Security**: A compromised device in one subnet does **not** affect devices in another.
- **Privacy and Isolation**: You can isolate sensitive resources from the rest of the network.

---

## 🔹 Types of Subnets
1. **Private Subnet**:
   - No direct access to the internet.
   - Ideal for databases, backend services, and secure internal applications.

2. **Public Subnet**:
   - Has internet access.
   - Internet access is enabled by associating a **route table** with a route pointing to an **Internet Gateway**.

---

## 🔹 CIDR (Classless Inter-Domain Routing)
- CIDR is used to define IP ranges in subnets.
- Format: `IP_address/CIDR_notation`

### Example:
- VPC CIDR block: `172.16.0.0/16` → Gives 65,536 IPs (`2^(32-16)`)
- Subnet CIDR block: `172.16.3.0/24` → Gives 256 IPs (`2^(32-24)`)

You can allocate:
- `172.16.3.0/24` → 256 IPs: 172.16.3.0 to 172.16.3.255
- `172.16.4.0/24`, `172.16.5.0/24` ... etc., for other 256-IP subnets.

---

## 🔹 Subnet CIDR Calculations

| CIDR Notation | Number of IPs | Usage Example                     |
|---------------|----------------|----------------------------------|
| /32           | 1              | Loopback or a single host        |
| /31           | 2              | Point-to-point links             |
| /30           | 4              | Very small subnet                |
| /26           | 64             | Small team or app cluster        |
| /24           | 256            | Commonly used for class C blocks |
| /16           | 65,536         | Class B, large enterprise        |
| /8            | 16 million+    | Class A, very large organizations|

---

## 🔹 IP Address Classes

| Class | CIDR Example   | Range           | Number of IPs     |
|-------|----------------|------------------|-------------------|
| A     | 10.0.0.0/8     | 10.0.0.0–10.255.255.255 | 16M+     |
| B     | 172.16.0.0/12  | 172.16.0.0–172.31.255.255 | 1M+   |
| C     | 192.168.0.0/16 | 192.168.0.0–192.168.255.255 | 65K+ |

> These ranges are **private IP ranges** — they are reserved and not routable over the public internet.

---

## 🔹 Ports

- A **port** identifies a specific application or service running on a machine.
- Each application listens on a specific port (e.g., web servers often use port `80` or `443`).
- You access an application like this: `IP:PORT` (e.g., `192.168.0.5:8080`).

---

### ✅ Summary
- Subnetting helps isolate and protect parts of your network.
- CIDR notation defines how many IPs a subnet contains.
- Private/public subnets are determined by their access to the internet.
- Ports are essential for distinguishing services on the same machine.

---









