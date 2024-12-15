

### **1. Introduction to Computer Networks**  
- History and Development of Computer Networks  
- Network Topologies  

### **2. Layering and Protocols**  
- OSI Model  
- TCP/IP Protocol Stack  
- Basics of Packet Switching  
- Circuit Switching  
- Virtual Circuit Switching  

### **3. Physical Layer**  
- **Guided Transmission Media**  
  - Twisted Pairs  
  - Coaxial Cable  
  - Fiber Optics  
- **Wireless Transmission**  

### **4. Data Link Layer**  
- **Design Issues**  
- **Framing**  
- **Error Detection and Correction**  
- **Elementary Data Link Protocols**  
  - Simplex Protocol  
  - Simplex Stop-and-Wait Protocol (Error-Free Channel)  
  - Simplex Stop-and-Wait Protocol (Noisy Channel)  
- **Sliding Window Protocols**  
  - One-Bit Sliding Protocol  
  - Go-Back-N Protocol  
  - Selective Repeat Protocol  
- **Example Data Link Protocols**  

### **5. Medium Access Sub-Layer**  
- **The Channel Allocation Problem**  
- **Multiple Access Protocols**  
  - ALOHA  
  - Carrier Sense Multiple Access (CSMA)  
  - Collision-Free Protocols  
- **Wireless LANs**  
- **Data Link Layer Switching**  
  - Ethernet Bridging  

### **6. Network Layer**  
- **Design Issues**  
- **Routing Algorithms**  
  - Shortest Path Routing  
  - Flooding  
  - Hierarchical Routing  
  - Broadcast and Multicast Routing  
  - Distance Vector Routing  
  - Link State Routing  
- **Congestion Control Algorithms**  
- **Quality of Service (QoS)**  
- **Internetworking**  
- **Fragmentation**  
- **The Network Layer in the Internet**  
  - IP Addressing (IPv4, IPv6)  
  - CIDR (Classless Inter-Domain Routing)  
  - NAT (Network Address Translation)  
  - Basics of IP Support Protocols  
    - ARP (Address Resolution Protocol)  
    - DHCP (Dynamic Host Configuration Protocol)  
    - ICMP (Internet Control Message Protocol)  

### **7. Transport Layer**  
- **Transport Services**  
- **Elements of Transport Protocols**  
- **Connection Management**  
- **Error and Flow Control**  
- **Congestion Control**  
- **TCP (Transmission Control Protocol)**  
- **UDP (User Datagram Protocol)**  
- **Sockets**  

### **8. Application Layer**  
- **Domain Name System (DNS)**  
- **Electronic Mail (Email)**  
- **World Wide Web (WWW)**  
  - HTTP (HyperText Transfer Protocol)  
  - FTP (File Transfer Protocol)  
  - Streaming Audio and Video  

--- 


























---

---
---
---
---
---

## sample viva  **Computer Networking 

---

### **1. Introduction to Computer Networks**

**Q1. What are the different types of computer networks?**

**Answer:**  
The types of computer networks are:
- **LAN (Local Area Network):** A network within a small geographical area like a building or a campus.
- **MAN (Metropolitan Area Network):** A network that covers a larger geographical area, such as a city.
- **WAN (Wide Area Network):** A network that spans across large geographical distances, such as between cities or countries.
- **PAN (Personal Area Network):** A network typically used for personal devices like smartphones or laptops within a very short range.

**Q2. What is the history and development of computer networks?**

**Answer:**  
The development of computer networks began in the late 1950s with the creation of ARPANET, the first wide-area packet-switched network, funded by the U.S. Department of Defense. This evolved into the Internet in the 1990s. Networking technologies such as Ethernet, TCP/IP, and wireless networks have since revolutionized communications, enabling global connectivity.

---

### **2. Layering and Protocols**

**Q1. Explain the OSI model.**

**Answer:**  
The OSI (Open Systems Interconnection) model consists of **7 layers**:
1. **Physical Layer:** Deals with the transmission of raw bits over a physical medium.
2. **Data Link Layer:** Ensures reliable data transfer over the physical layer (framing, error detection).
3. **Network Layer:** Responsible for routing and forwarding packets.
4. **Transport Layer:** Manages end-to-end communication and flow control (e.g., TCP, UDP).
5. **Session Layer:** Manages sessions between applications.
6. **Presentation Layer:** Translates data formats (e.g., encryption, compression).
7. **Application Layer:** Provides network services to end-users (e.g., HTTP, FTP).

**Q2. What is the difference between packet switching and circuit switching?**

**Answer:**  
- **Packet Switching:** Data is divided into packets and sent independently across the network. Each packet may take a different route. It is efficient for bursty data like the Internet.
- **Circuit Switching:** A dedicated communication path is established between the sender and receiver for the entire duration of the communication. It is commonly used in traditional telecommunication systems.

---

### **3. Physical Layer**

**Q1. What are the different guided transmission media?**

**Answer:**  
Guided transmission media refers to physical cables that guide the transmission of signals:
- **Twisted Pair Cable:** Pairs of insulated copper wires twisted together. It is commonly used in telephone lines and Ethernet networks.
- **Coaxial Cable:** A central conductor surrounded by insulation, shielding, and an outer jacket. Used in cable television and Internet connections.
- **Fiber Optic Cable:** Uses light to transmit data over glass or plastic fibers. It offers high bandwidth and is immune to electromagnetic interference.

**Q2. What is wireless transmission?**

**Answer:**  
Wireless transmission involves the transfer of data through the air using electromagnetic waves. Common types include:
- **Radio Waves:** Used in wireless LANs, cellular networks.
- **Microwaves:** Used for point-to-point communication, satellite communication.
- **Infrared:** Used for short-range communication (e.g., remote controls).

---

### **4. Data Link Layer**

**Q1. What is the sliding window protocol?**

**Answer:**  
The sliding window protocol is a flow control method used to manage the transmission of data packets between sender and receiver. It ensures that the sender does not overwhelm the receiver by controlling the number of unacknowledged packets in transit. Variants include:
- **Go-Back-N Protocol:** The sender can send several frames before waiting for acknowledgment, but if a frame is lost, all subsequent frames are retransmitted.
- **Selective Repeat Protocol:** The sender retransmits only the lost or corrupted frames.

**Q2. What is error detection and correction?**

**Answer:**  
Error detection and correction techniques are used to ensure data integrity during transmission. Common methods include:
- **Parity Bits:** A single bit added to the data to make the number of 1s either odd or even.
- **Checksums:** A value derived from the data and sent with it to detect errors.
- **Cyclic Redundancy Check (CRC):** A more robust error detection method that uses polynomial division.

---

### **5. Medium Access Sub-Layer**

**Q1. What is ALOHA?**

**Answer:**  
ALOHA is a simple protocol for multiple access in a shared communication medium. There are two versions:
- **Pure ALOHA:** A device transmits data at any time and listens for collisions. If a collision occurs, it retransmits after a random delay.
- **Slotted ALOHA:** Time is divided into slots, and a device only transmits at the beginning of a slot, reducing collisions.

**Q2. What are collision-free protocols?**

**Answer:**  
Collision-free protocols ensure that multiple devices can communicate on the same channel without interfering with each other. Examples include:
- **Token Passing Protocol:** A token circulates in the network, and only the device holding the token can transmit data.
- **Polling Protocol:** A central controller polls devices to ask if they want to transmit, reducing the chance of collisions.

---

### **6. Network Layer**

**Q1. What is IP addressing?**

**Answer:**  
IP addressing is the assignment of unique numerical addresses to devices on a network. There are two versions:
- **IPv4:** 32-bit address, written as four decimal numbers separated by periods (e.g., 192.168.0.1).
- **IPv6:** 128-bit address, written as eight hexadecimal groups separated by colons (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

**Q2. What is CIDR?**

**Answer:**  
CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing. It allows the division of IP addresses into subnets without the rigid boundaries of the traditional class-based system, improving IP address utilization.

---

### **7. Transport Layer**

**Q1. What is the difference between TCP and UDP?**

**Answer:**  
- **TCP (Transmission Control Protocol):** A connection-oriented protocol that ensures reliable data transfer through acknowledgment, error control, and flow control.
- **UDP (User Datagram Protocol):** A connectionless protocol that does not guarantee delivery or order of packets, providing faster communication but less reliability.

**Q2. What are sockets in the transport layer?**

**Answer:**  
A socket is an endpoint for sending or receiving data across a network. It combines an IP address and a port number to create a unique communication endpoint, allowing applications to send or receive data using TCP or UDP.

---

### **8. Application Layer**

**Q1. What is DNS?**

**Answer:**  
DNS (Domain Name System) translates human-readable domain names (e.g., www.example.com) into IP addresses that computers use to identify each other on the network.

**Q2. Explain the working of HTTP.**

**Answer:**  
HTTP (HyperText Transfer Protocol) is used for transferring web pages over the internet. It is a request-response protocol:
- The client (browser) sends a request to the server.
- The server processes the request and sends back the appropriate response (e.g., a webpage).
- HTTP operates on a stateless model, meaning each request is independent of the others.

---
 










