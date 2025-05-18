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





