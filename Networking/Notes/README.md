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

