# Networking 🌐

My notes covers foundational networking concepts, which are essential for working with AWS.

## Key Takeaways

- **Networking is essential** for all AWS interactions.
- Understanding networking is necessary whether you're an architect, developer, or systems administrator.
- The focus will be on foundational networking concepts, starting with **LANs** and how data moves between devices.

## Topics Covered

1. **LANs**: Local Area Networks
   - How data moves between devices on your LAN.
   - The starting and ending points for data moving over the Internet.

2. **Routing**: How data travels over the Internet
   - Data moves across many interconnected networks.
   - Understanding LANs is crucial to understanding the Internet.

3. **Segmenting Data**: For reliable transfer
   - Topics include network ports, sessions, and how they ensure reliable data transfer.

4. **OSI Model**: Understanding networks via the 7-layer model
   - Divides networks into seven components: from physical to application.
   - Provides a foundation to understand how each component works and interacts with others.

## OSI Model Overview

- **Layer 1**: Physical Link  
- **Layer 2**: Data Link  
- **Layer 3**: Network  
- **Layer 4**: Transport  
- **Layer 5**: Session  
- **Layer 6**: Presentation  
- **Layer 7**: Application  

This is also referred to as the **Networking Stack**, which exists on all devices including laptops, phones, routers, and servers.

### Layer Groupings

- **Media Layers** (bottom):
  - Physical Link
  - Data Link
  - These layers handle **data transfer** between points (can be local or global).

- **Host Layers** (top):
  - Transport
  - Session
  - Presentation
  - Application
  - These layers handle **how data is formatted, chopped up, and reassembled** for transmission and understanding between network connections.

## Networking in Practice

At a high level:
- Layer 7 (Application): Might involve a web browser like Firefox on one end and a web server on the other side.
- Layer 1 (Physical): Involves physical network cards/interfaces.
- Data flows through these layers to move between devices and servers, allowing communication across networks.

---

## Layer 1: The Physical Layer

- **Purpose**: Focuses on the physical medium used to transmit data between devices.
- **Example**: Two laptops connected via a copper cable.

### Types of Physical Media:
- **Copper cables**: Transmit electrical signals.
- **Fiber optics**: Transmit light signals.
- **Wi-Fi**: Uses radio frequencies.

### Key Concepts:
- **Standards**: Defines how raw bit streams (0s and 1s) are sent and received.
  - Includes specifications like voltage levels, data rates, distance limits, and connector types.
- **Transmission**: Uses defined voltages (e.g., 1 volt for binary 1, -1 volt for binary 0) to transmit data.
- **Layer 1 Devices**: Understand only Layer 1, while Layer 3 devices handle Layers 1–3.
  
### Hub and Collision Domain:
- **Hub**: A Layer 1 device that connects multiple devices.
  - Sends received signals from any port to all other ports, including errors and collisions.
- **Collision Domain**: Layer 1 networks are broadcast mediums.
  - When multiple devices transmit simultaneously, collisions occur, corrupting the data.
  - There is no access control at this layer to prevent collisions.

### Limitations of Layer 1:
- **No device addressing**: It’s a broadcast medium, so all devices receive transmissions.
- **Collisions**: Multiple devices can transmit simultaneously, causing data corruption.
- **No Media Access Control (MAC)**: There's no mechanism to control transmission timing, making collisions likely as more devices are added.

---

### Summary of Layer 1
- Layer 1 focuses on the **shared physical medium** (e.g., copper cables, Wi-Fi) and the **standards** for transmitting data.
- All devices on a Layer 1 network use the same medium and standards but lack device-to-device communication control.
- Understanding Layer 1 is fundamental as it defines how data travels physically between devices.

---

## Layer 2: Data Link Layer

The **Data Link Layer** (Layer 2) is responsible for enabling device-to-device communication over the same network. It builds on the physical transmission (Layer 1) and ensures that data is correctly formatted and sent to the intended device.

### Key Functions:

- **Frames**: At this layer, data is organized into **frames**. A frame acts as a container that holds the data, along with necessary addressing and error-checking information.
  
  **Example**: Think of frames like envelopes. The data is the letter, while the envelope has a return address (source MAC), a recipient's address (destination MAC), and a stamp (Frame Check Sequence) to ensure delivery.

- **MAC Address**: Each device connected to a Layer 2 network is identified by a unique 48-bit **MAC address**. This hardware address ensures that data reaches the correct destination on a local network.

  **Example**: Your laptop's network interface has a MAC address like `00:1A:2B:3C:4D:5E`. When sending data on a local network, other devices use this address to communicate specifically with your laptop.

- **Encapsulation**: Layer 2 encapsulates higher-layer data (from Layer 3, such as IP packets) inside frames. It acts as a translator between Layer 3's packet-based communication and the raw data transmission of Layer 1.

  **Example**: When accessing a website, the data sent to your device includes an IP packet (Layer 3), which is encapsulated in an Ethernet frame (Layer 2).

- **Media Access Control (MAC)**: Layer 2 controls access to the physical transmission medium, ensuring that only one device transmits at a time. **CSMA/CD** (Carrier Sense Multiple Access with Collision Detection) helps manage access and deal with collisions.

  **Example**: In a crowded network where multiple devices try to send data at once (like people speaking over each other), CSMA/CD listens to the medium (network cable) to ensure it's clear before sending data, and if a collision happens, devices wait a random time before retrying.

- **Error Detection**: Frames include a **Frame Check Sequence (FCS)**, which uses a **Cyclic Redundancy Check (CRC)** to detect errors during transmission.

  **Example**: Imagine sending a file over the network. The FCS acts like a checksum, ensuring the data wasn’t corrupted in transit. If the receiving device detects an error, it can request a resend.

### Frame Structure:

- **Preamble & Start Frame Delimiter**: Marks the beginning of a frame.
- **Destination & Source MAC Address**: Specifies the recipient and sender device.
- **EtherType**: Indicates which protocol (e.g., IP) is being used at Layer 3.
- **Payload**: Contains the actual data being transmitted.
- **Frame Check Sequence (FCS)**: Used to verify data integrity.

### Devices Operating at Layer 2:

- **Switches**: These are intelligent Layer 2 devices that forward frames based on MAC addresses. Switches reduce network collisions by ensuring that frames are only sent to the correct port, effectively dividing the network into multiple collision domains.

  **Example**: In a network with four computers connected to a switch, if Computer A sends a message to Computer B, the switch ensures only Computer B receives it. In contrast, a hub would send the message to all devices, leading to inefficiency.

- **Hubs**: Layer 1 devices that forward data to all connected devices without regard to MAC addresses. This can lead to more collisions compared to switches.

  **Example**: Imagine yelling in a crowded room—everyone hears you, even if you're only trying to talk to one person. That's how a hub operates.

### Key Protocols:

- **Ethernet**: The most common Layer 2 protocol used in LANs (Local Area Networks).
- **CSMA/CD**: Ensures that devices share the medium (network cable) efficiently by detecting and handling collisions.

### Unicast, Broadcast, and Multicast:

- **Unicast**: Communication between a single sender and a single recipient. 

  **Example**: Sending a direct message to one person.

- **Broadcast**: Communication where a frame is sent to all devices on the network.

  **Example**: A DHCP server broadcasting an IP address offer to all devices on the network.

- **Multicast**: Communication where a frame is sent to a specific group of devices.

  **Example**: Streaming a live event to multiple specific users without broadcasting to everyone.

Layer 2 ensures that data reaches the correct device on a local network, playing a crucial role in network communication and traffic management.

---

## Layer 3: Network Layer

The Network Layer (Layer 3) is responsible for routing data from one location to another, typically over multiple interconnected networks. This layer enables communication across geographically separated networks, such as those used when accessing the Internet.

---

### **Key Functions:**

- **Purpose of Layer 3**: It allows data to travel from a source to a destination across multiple networks. For example, when watching a video, the data is transferred from a server (source) to your local device (destination).

- **Need for Layer 3**: If two Layer 2 networks are geographically distant (e.g., LAN1 on the east coast and LAN2 on the west coast), Layer 3 allows them to communicate without needing direct point-to-point links, which would be expensive and unscalable.

- **Example**: Without Layer 3, companies with multiple offices would have to use direct links, which is inefficient.

---

### **Challenges in Layer 2 Networking:**

- **Different Layer 2 Protocols**: Not all Layer 2 networks use the same protocols (e.g., Ethernet, PPP, MPLS, ATM). This presents a challenge since devices on different Layer 2 networks can't easily communicate.

- **Example**: Ethernet is used in local networks (LANs), but point-to-point links or satellite connections might use other protocols, which requires a Layer 3 protocol to unify communication across them.

---

### **Role of IP (Internet Protocol):**

- **IP as Layer 3 Protocol**: Layer 3 introduces the Internet Protocol (IP), which assigns IP addresses to devices, allowing communication across networks.

- **Routing via IP**: Devices use IP addresses to send and receive data across networks. Routers, which operate at Layer 3, move packets between networks.

- **Example**: Your device has an IP address, and the server hosting the video you're watching also has an IP address. The data from the server is routed through multiple networks to your device.

---

### **Packet Encapsulation:**

- **Encapsulation Process**: IP packets are encapsulated inside Layer 2 frames for transmission across networks. When moving between networks, the Layer 2 frame is replaced, but the IP packet remains the same.

- **Example**: As video data moves from a server to your device, IP packets are placed inside Ethernet frames for the LAN segment. When the packet moves to another network, the frame is stripped, and a new one is added for the next segment.

---

### **Structure of an IP Packet:**

- **Source & Destination IP Addresses**: These fields store the IP addresses of the device generating the packet and the destination device.

- **Example**: A PC on the west coast sends data to a laptop on the east coast, with both devices having unique IP addresses.

- **Protocol Field**: This field specifies the Layer 4 protocol used within the IP packet, such as TCP, UDP, or ICMP.

- **Example**: A TCP packet has a protocol field value of 6, while a ping (ICMP) packet has a value of 1.

- **Time-to-Live (TTL) Field**: This field limits the number of hops a packet can take across networks before being discarded.

- **Example**: If a packet cannot reach its destination, the TTL prevents it from circulating indefinitely.

---

### **Layer 3 Devices:**

- **Routers**: These devices operate at Layer 3 and are responsible for forwarding IP packets between networks. They encapsulate packets in the appropriate Layer 2 frame for each segment of the journey.

- **Example**: Routers along the route of a video transmission strip and re-encapsulate packets to move them across multiple networks.

---

### **IPv4 vs. IPv6:**

- **IP Version 4 (IPv4)**: The most widely used version, providing sufficient IP addresses for most devices. It uses 32-bit addresses.

- **IP Version 6 (IPv6)**: A newer version that offers a larger address space using 128-bit addresses, providing more scalability for future devices.

- **Example**: IPv6 is necessary as the number of devices connected to the Internet increases, and IPv4 addresses become limited.

- **TTL vs. Hop Limit**: In IPv6, the TTL field is replaced by a "hop limit" field, serving the same purpose of limiting the number of hops a packet can take.

---

## **IP Addressing and Subnetting**

### **IP Addressing Basics**

- **IP Address**: Identifies devices using a Layer 3 IP network. In this session, we focus on IPv4 (e.g., 133.33.3.7).
  
- **Decimal Notation**: IP addresses are represented in decimal, consisting of four numbers (0–255) separated by periods (e.g., 133.33.3.7).
  
- **Binary Representation**: While humans use decimal notation, devices interpret IP addresses as binary numbers, with each octet consisting of 8 bits. A complete IPv4 address has 32 bits.
  
- **Example**: 133.33.3.7 in binary:
  - 133 → 10000101
  - 33 → 00100001
  - 3 → 00000011
  - 7 → 00000111

---

### **Network and Host Portions**

An IP address has two parts:
- **Network Portion**: Identifies the network.
- **Host Portion**: Identifies the device on that network.

- **Example**: In 133.33.3.7, 133.33 could represent the network, while 3.7 refers to specific devices on that network.

---

### **Subnetting**

- **Subnet Masks**: Determine which part of the IP address represents the network and which part is for the host. They are often represented in binary or with a slash notation (e.g., /16).

- **Example**: A subnet mask of 255.255.0.0 in binary is 11111111.11111111.00000000.00000000 (which corresponds to /16).

If two IP addresses have matching network portions, they are on the same network.

---

### **Subnet Mask in Action:**

To calculate the start and end of a network, you convert both the IP address and subnet mask to binary and then apply the mask.

- **Example**: For IP 133.33.3.7 with subnet mask 255.255.0.0:
  - Start of the Network: 133.33.0.0
  - End of the Network: 133.33.255.255

---

### **Static vs. Dynamic IP Addressing:**

- **Static IP**: Manually assigned by a human.
- **Dynamic IP (DHCP)**: Automatically assigned using the Dynamic Host Configuration Protocol (DHCP).

---

### **Routing**

- **Default Gateway**: The local network device where packets are forwarded if the destination is not on the local network. Devices like your home router act as a default gateway to forward traffic destined for external networks (e.g., Netflix, AWS).

---

### **Routing Tables**

Each router maintains a routing table, which contains routes (a destination and a next hop). When a packet arrives, the router examines the destination IP and looks for a matching route. More specific routes (higher prefix) are preferred.

- **Example Routing Table**:
  - Route 1: 52.217.13.0/24 (specific to AWS)
  - Route 2: 0.0.0.0/0 (default route for all IP addresses)

If the AWS route matches, the router forwards the packet to AWS. The forwarding is done at Layer 2 by wrapping the packet in a frame, adding the MAC address of the AWS router.

---

### **Conclusion**

Understanding how IP addresses and subnet masks work is crucial for determining whether devices are on the same network or not. Routing tables and subnetting enable devices to decide whether to send packets locally or use routers to forward them across the internet.

---

### **Address Resolution Protocol (ARP)**

- **Purpose**: ARP is used when a Layer 3 packet (with an IP address) needs to be encapsulated inside a Layer 2 frame and sent to a MAC address. It resolves the MAC address for a given IP address.

- **Example**: If you want to send packets to AWS through your home router (the default gateway), ARP finds the MAC address of the router to send the frame.

---

### **ARP Example: LAN with Two Laptops**

- **Scenario**: Two laptops on the same LAN, one sending game data to the other. The left laptop has the game data and knows the IP address (133.33.3.10) of the right laptop but not the MAC address.

- **Steps**:
  1. The left laptop creates a packet with the source and destination IP addresses.
  2. To create the frame, it needs the right laptop's MAC address, so it uses ARP.
  3. ARP broadcasts a request asking, "Who has 133.33.3.10?"
  4. The right laptop responds with its MAC address (e.g., 5B:78).
  5. The left laptop now builds the frame, encapsulates the packet, and sends it to the MAC address of the right laptop.
  6. The right laptop receives the frame, decapsulates it, and delivers the data to the application (game).

- **Key Point**: Devices on the same LAN use Layer 2 frames for local communication, even if they are operating at Layer 3.

---

### **Routing Example: Communication Between Networks**

- **Scenario**: Three networks (orange, green, pink) with routers (R1, R2). Two laptops on the orange network (D1, D2), and a third laptop on the pink network (D3).

### **Intra-network Communication (D1 to D2):**

- D1 uses ARP to get D2's MAC address and encapsulates the packet into a frame.
- The frame is sent directly to D2, no router involved.

---

### **Inter-network Communication (D2 to D3):**

- D2 knows D3 is on a different network using its subnet mask.
- It creates a packet with D3's IP address and uses ARP to find the MAC address of router R1 (the default gateway).
- The packet is forwarded to R1, where it is decapsulated.
- R1 checks its routing table, sees that the next hop is R2, and encapsulates the packet into a new frame for R2.
- R2 receives the frame, decapsulates the packet, and forwards it to D3 using ARP to get D3's MAC address.
- D3 receives the frame, decapsulates the packet, and the data is delivered to the application.

---

### **Key Concepts of Layer 3**

- **IP Addresses**: Layer 3 introduces IP addresses (IPv4/IPv6) for addressing devices over networks.

- **Routing**: Layer 3 includes routing and routing tables that help direct packets across different networks.

- **Routers**: Routers operate at Layer 3 and are responsible for forwarding packets between different networks by encapsulating them in new Layer 2 frames as needed.

- **Packet Encapsulation**: As packets travel through different networks, they are encapsulated in different Layer 2 frames.

- **Order of Packets**: IP does not guarantee that packets will arrive in order. Layer 3 only delivers packets based on IP addresses, and packets might take different paths.

---

### **Limitations of Layer 3**

- **Single Stream**: Layer 3 only provides one communication stream per pair of devices. Different applications on the same devices cannot have separate communication channels.

- **Out-of-Order Delivery**: Packets may arrive in a different order due to varying network paths, which is a problem Layer 4 protocols address.

---

# Layer 4 & 5: Transport and Session Layers

## **TCP Segment Structure Overview**
- **TCP** (Transmission Control Protocol) enables communication between two devices, such as a laptop and a game server. 
- TCP is **connection-based**, providing a reliable communication channel.
  
### **TCP Segment Structure Fields**:
1. **Source and Destination Ports**:
   - **Source Port**: The port number on the sending device.
   - **Destination Port**: The port number on the receiving device.
   
2. **Sequence Number**:
   - Each TCP segment has a **sequence number** to ensure proper data ordering.
   - **Example**: Client sends a segment with a sequence number `CS`; the server responds acknowledging this with `CS+1`.
   
3. **Acknowledgment Number**:
   - Acknowledges receipt of data. 
   - If data is successfully received, the acknowledgment number is **Sequence Number + 1**.
   
4. **Flags Field**:
   - Controls aspects of the connection using various flags.
     - **SYN**: Synchronizes sequence numbers (used in the initial connection).
     - **ACK**: Acknowledges the receipt of segments.
     - **FIN**: Terminates the connection.
   - **Example**: A SYN is sent by the client to initiate a connection, the server replies with SYN-ACK, and the client finishes with ACK.
   
5. **Window Size**:
   - Controls the **flow of data**, determining how much data can be sent before requiring an acknowledgment.

6. **Checksum**:
   - Ensures integrity by verifying that the segment's data has not been corrupted during transmission.

---

## **TCP Communication and Connection Establishment**
TCP segments are encapsulated in **IP packets** at Layer 3, but TCP provides added capabilities, like **error checking** and **data reordering**.

### **Three-Way Handshake**:
Before data transfer can happen, a connection must be established using a **three-way handshake**:
1. **Client → Server**: 
   - The client sends a **SYN** packet with a **random sequence number (ISN)**.
   - **Example**: Client initiates with sequence number `CS`.
   
2. **Server → Client**:
   - The server responds with a **SYN-ACK**:
     - Server sets its own sequence number `SS`.
     - The acknowledgment number is `CS + 1`, acknowledging receipt of the client's segment.
   
3. **Client → Server**:
   - The client acknowledges the server's sequence number by sending an **ACK** with `SS + 1`.

At this point, both devices are **synchronized** and ready for data exchange.

---

## **TCP Data Transfer**
Once the connection is established, the **data exchange** begins:
- Data is segmented, numbered, and sent from one device to another.
- Each side **increments the sequence numbers** for new segments and **acknowledges** the received data.

### **Example**:
1. **Client → Server**: 
   - The client sends data starting at sequence number `CS`.
2. **Server → Client**: 
   - The server acknowledges the data by sending back an **ACK (CS + 1)**.

TCP provides **reliable communication** by allowing segments to be retransmitted if lost or damaged.

---

## **Ports and Ephemeral Ports**
- **Well-Known Ports**: Servers typically use well-known ports like **TCP 443** (HTTPS).
- **Ephemeral Ports**: Clients use **temporary high-numbered ports** (e.g., **23060**) for communication.

### **Example**:
- **Client**: 
  - Source Port: `23060`, Destination Port: `443` (server).
- **Server**:
  - Source Port: `443`, Destination Port: `23060` (client).

---

## **Session Management (Layer 5)**
- TCP allows devices to create **sessions**, representing an ongoing exchange of data.
- Once a session is established, **sequence numbers** ensure **synchronized communication** between the client and server.
  
### **Example**:
- **Client**: Acknowledges the server’s sequence `SS + 1`.
- **Server**: Acknowledges the client’s sequence `CS + 1`.

This process ensures the **connection is maintained** throughout the data transfer phase.

---

## **Stateful vs Stateless Firewalls**
### **Stateless Firewalls**:
- **Do not track the connection state** and require **two rules**: 
  - One for **outgoing traffic**.
  - One for **incoming response traffic**.
  
### **Stateful Firewalls**:
- **Track the state** of the TCP segments.
- Automatically allow **response traffic** once the initial connection is established.

### **Example**:
- **Stateless Firewall**:
  - A client using port `23060` to connect to a server on port `443` requires:
    - Rule 1: Allow **outgoing** traffic from port `23060` to `443`.
    - Rule 2: Allow **incoming** traffic from port `443` to `23060`.
- **Stateful Firewall**:
  - Only one rule is required: Allow **outgoing** traffic from `23060 → 443`. Response traffic is automatically permitted.

---

## **Flags and Connection Termination**
### **Common TCP Flags**:
1. **SYN**: Initiates connection.
2. **ACK**: Acknowledges receipt of data.
3. **FIN**: Gracefully terminates a connection.
4. **RST**: Abruptly resets the connection.

### **Connection Termination**:
1. **FIN** packet is sent by one side to initiate closure.
2. The other side responds with an **ACK** and sends its own **FIN**.
3. The original sender acknowledges with **ACK**, ending the session.

---

## **Firewall Rules for Secure Communication**
- TCP sessions can be secured using firewalls by setting appropriate rules for **incoming and outgoing traffic**.
- **Ephemeral ports** must often be allowed to enable proper communication.

### **Firewall Example**:
- **Outbound**: Allow traffic from the client IP (`23060`) to the server’s IP (`443`).
- **Inbound**: Allow traffic from the server IP (`443`) to the client IP (`23060`).

---

## **Session State and Security**
- **Stateless Firewalls**: Require separate rules for outgoing and incoming traffic.
- **Stateful Firewalls**: Automatically handle response traffic once an outgoing connection is permitted.

In AWS, **Network Access Control Lists (NACLs)** are **stateless**, while **Security Groups** are **stateful**.

---

## **Layer 4 vs Layer 5 Debate**
- **Layer 4 (Transport)**: Deals with **TCP segments**, **port numbers**, and **IP addresses**.
- **Layer 5 (Session)**: Manages **sessions** and maintains **persistent communication** between two devices.
  
However, in practice, Layer 4 (Transport) and Layer 5 (Session) are often discussed together, as they both involve managing **connections** and **data flow**.

---



