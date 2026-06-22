# Networking Hardware: Deep Dive into the Hub (Historical)

Since we just covered the Switch and the Router, we need to take a quick step back in time. You cannot truly appreciate how smart modern networks are until you understand the device they replaced: **The Hub**.

Today, Hubs are completely obsolete in modern networking. You cannot even buy one at a standard electronics store anymore. However, they are still a crucial part of networking education because they perfectly illustrate _why_ network collisions occur and why Layer 2 (MAC addressing) was invented.

## 1. What Exactly was a Hub?

A Hub was a physical box with multiple Ethernet ports, used to connect multiple computers together in a LAN. Physically, it looked exactly like a Switch.

However, unlike a Switch (which operates at Layer 2) or a Router (Layer 3), a Hub operated entirely at **Layer 1 (The Physical Layer)** of the OSI model.

Because it was a Layer 1 device, it had no "brain." It didn't know what an IP address was, and it didn't even know what a MAC address was. It only understood raw electricity.

## 2. How a Hub Worked: The "Dumb Repeater"

A Hub functioned as a simple electrical repeater. Here is how data moved through it:

1. Computer A wants to send a file to Computer B.
    
2. Computer A sends the electrical signals (the 1s and 0s) down the cable into Port 1 of the Hub.
    
3. The Hub receives the electrical pulse. Because it has no memory and no MAC table, it simply amplifies that electrical pulse and **blindly shoots it out of every single other port** (Ports 2, 3, 4, 5, etc.).
    
4. Every single computer on the network receives the file. The computers that aren't the intended recipient have to use their own CPU power to read the envelope, realize it's not for them, and delete it. Computer B accepts it.
    

If the Switch is a smart mailroom that delivers a letter directly to your desk, the Hub was a guy with a megaphone standing in the middle of the office, shouting your private mail for everyone to hear.

## 3. Why the Hub Died (The Massive Problems)

Because the Hub indiscriminately blasted electricity everywhere, it created two fatal flaws for growing networks.

### Flaw 1: Network Collisions (Half-Duplex)

Imagine you have 10 computers plugged into a Hub. Computer A is sending a massive file to Computer B. That means the Hub is currently blasting electrical signals out of all 10 ports.

What happens if Computer C tries to talk to Computer D at the exact same time?

- The electrical signals from Computer C enter the Hub and physically crash into the electrical signals from Computer A.
    
- This is called a **Collision**. Both signals are corrupted and destroyed.
    
- All the computers detect the collision, stop talking, wait a random number of milliseconds, and try again.
    

Because of this, Hubs forced a network to operate in **Half-Duplex** mode. This means a device could either send data _or_ receive data, but it could never do both at the same time. The entire Hub was one single **Collision Domain**.

### Flaw 2: Zero Security

Because every single packet of data was sent to every single port, security was non-existent. If you were plugged into the office Hub, you could run a simple packet-sniffing program (like Wireshark) and read all of your coworkers' emails, passwords, and file transfers as they flew across the wire, because your computer was receiving them anyway!

## 4. The Final Evolution

The Switch completely killed the Hub because the Switch isolated every single port. On a Switch, every port is its own separate Collision Domain, allowing all devices to talk and listen simultaneously (**Full-Duplex**) in complete privacy.

|**Feature**|**The Hub (Historical)**|**The Switch (Modern)**|
|---|---|---|
|**OSI Layer**|Layer 1 (Physical)|Layer 2 (Data Link)|
|**How it forwards**|Broadcasts to ALL ports|Forwards directly to ONE port|
|**Communication**|Half-Duplex (Send OR Receive)|Full-Duplex (Send AND Receive)|
|**Collisions**|High collision rate|Zero collisions|

### Module Summary

The Hub was a primitive, "dumb" Layer 1 device that connected computers but suffered from terrible efficiency, high data collisions, and massive security flaws because it blindly copied electrical signals to every device on the network.