# Networking Fundamentals: What is a Computer Network?

Welcome to the foundational module of Computer Networking. In this module, we will explore the core architecture, components, and classifications of modern digital networks.

## 1. The Core Definition

A **computer network** is a collection of interconnected devices (nodes) that communicate with each other to share resources, data, and services. These nodes are linked through physical or wireless communication channels and govern their interactions using standardized rules called **protocols**.

## 2. Essential Network Components

Every network, from a small home Wi-Fi setup to the global internet, relies on four fundamental building blocks:

- **End Devices (Nodes):** The source and destination of data (e.g., computers, servers, smartphones, IoT devices).
    
- **Transmission Media (Links):** The physical or wireless pathways carrying data (e.g., Fiber optic cables, Copper Ethernet/Cat6, Wi-Fi radio waves).
    
- **Intermediary Devices:** Hardware that connects and manages the flow of data between nodes.
    
    - _Switches:_ Connect devices within a single local network using MAC addresses.
        
    - _Routers:_ Connect multiple different networks together using IP addresses and determine the best path for data.
        
- **Protocols:** The software rules dictating how data is formatted, transmitted, and received (e.g., TCP/IP, HTTP, Ethernet).
    

## 3. Network Classifications by Scale

Networks are typically categorized by their geographic scope and administrative control:

|**Network Type**|**Scope**|**Use Case**|
|---|---|---|
|**LAN (Local Area Network)**|Single building or campus|Home Wi-Fi, corporate office networks. High speed, privately owned.|
|**WAN (Wide Area Network)**|Cities, Countries, Global|The Internet, Tier 1 ISP backbones. Connects multiple LANs together.|
|**WLAN (Wireless LAN)**|Local space (Wireless)|Standard Wi-Fi networks adhering to IEEE 802.11 standards.|
|**PAN (Personal Area Network)**|A few meters|Bluetooth connections between a phone and wireless headphones.|

## 4. Physical and Logical Topologies

Topology refers to the layout or structure of the network.

- **Star Topology:** All nodes connect to a central hub or switch. If one cable fails, only that node goes down. This is the most common setup in modern LANs.
    
- **Mesh Topology:** Every node connects to every other node. Offers maximum redundancy but is expensive to wire. Used in critical infrastructure and wireless routing.
    
- **Bus & Ring Topologies:** Legacy topologies where nodes shared a single main cable (Bus) or formed a closed loop (Ring). These are mostly obsolete in modern LANs.
    

## 5. The Standardized Framework: OSI Model

To understand how networks function, engineers use the Open Systems Interconnection (OSI) model, which breaks network communication into 7 distinct layers:

1. **Physical (Layer 1):** Cables, radio waves, bits (1s and 0s).
    
2. **Data Link (Layer 2):** MAC addresses, switches, Ethernet frames.
    
3. **Network (Layer 3):** IP addresses, routers, packets. (This is where NAT and BGP operate).
    
4. **Transport (Layer 4):** TCP/UDP protocols, port numbers. Ensures reliable delivery.
    
5. **Session (Layer 5):** Establishes and terminates connections between applications.
    
6. **Presentation (Layer 6):** Data translation, encryption (SSL/TLS), compression.
    
7. **Application (Layer 7):** End-user protocols like HTTP, DNS, SMTP, FTP.
    

## 6. Core Performance Metrics

Network efficiency is measured using several key indicators:

- **Bandwidth:** The maximum capacity of a link, typically measured in Megabits per second (Mbps) or Gigabits per second (Gbps). Think of this as the width of a highway.
    
- **Throughput:** The actual, measured amount of data successfully transferred over a specific period. This is always lower than theoretical bandwidth due to network overhead and congestion.
    
- **Latency:** The time it takes for a packet to travel from source to destination, measured in milliseconds (ms). Think of this as the speed limit on the highway.
    
- **Packet Loss:** The percentage of data packets that fail to reach their destination, requiring retransmission and causing network slowdowns.