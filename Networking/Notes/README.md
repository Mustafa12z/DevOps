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
