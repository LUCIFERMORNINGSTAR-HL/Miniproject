## Decentralized AD-HOC LoRa Mesh Framework for Infrastructure-less Emergency Communication
A robust, infrastructure-free communication system for first responders
The development of a decentralized mesh network using LoRa technology, aimed at establishing connectivity in disaster-stricken areas where traditional centralized networks have failed.

## About
<!--Detailed Description about the project-->
Decentralized AD-HOC LoRa Mesh Framework is a project designed to provide a resilient communication backbone during natural disasters like cyclones or floods. Traditional communication infrastructures (cellular/internet) are vulnerable to single-point failures and power outages. This project overcomes these challenges by creating a peer-to-peer mesh network where every low-cost ESP32-based node acts as a router, smartly forwarding data to expand range and bypass obstacles without needing a central gateway.

## Features
<!--List the features of the project as shown below-->
- Infrastructure-less Operation: Does not require internet, cellular towers, or central gateways.



- Smart Flooding Protocol: Implements a lightweight forwarding mechanism with duplicate suppression and HopLimits to prevent broadcast storms.



- Decentralized Architecture: Every node is both a sender and a relay, making the network self-organizing and self-healing.


- Low Latency: Optimized for emergency alerts with an average 2-hop latency of 1.12 seconds.


- High Reliability: Achieved a 98.5% Packet Delivery Rate (PDR) in Non-Line-Of-Sight (NLOS) conditions.


- Cost-Effective: Built using standard ESP32 microcontrollers and SX1276 LoRa transceivers.

## Requirements
<!--List the requirements of the project as shown below-->
- Microcontroller: ESP32 Development Board.


- LoRa Module: SX1276/78 Transceiver (operating in 867 MHz ISM band).


-Development Environment: Arduino IDE for firmware development.

- Programming Language: C/C++ (Arduino Framework).

- Libraries: Standard LoRa libraries (e.g., Sandeep Mistry’s LoRa) adapted for the Smart Flooding logic.

- Power Supply: Battery packs for mobile node deployment.
## System Architecture
<!--Embed the system architecture diagram as shown below-->

The system consists of homogeneous nodes arranged in a mesh topology. Each node executes a "Smart Flooding" algorithm that maintains a 'Seen-List' to track processed packets. When a packet is received, the node checks the list; if the packet is new and the HopLimit is valid, it rebroadcasts the message to neighbors.

<div align="center">
  <img width="634" height="375" alt="image" src="https://github.com/user-attachments/assets/255f785f-9d0e-44e4-9ddf-6f16049d0a25" />
</div>

## Output

<!--Embed the Output picture at respective places as shown below as shown below-->
#### Output1 - Latency Performance The system demonstrates stable latency performance.
The graph below shows the end-to-end latency for packets, fluctuating gently around the mean of 1.12s without sporadic spikes.
<div align="center">
  <img width="722" height="433" alt="image" src="https://github.com/user-attachments/assets/9e3be8d2-68af-4eab-a3cb-b5f55d100a7f" />
</div>

#### Output2 - Packet Reception
The cumulative packet reception graph shows a linear progression, indicating stable network performance and minimal packet loss over the experiment duration.
<div align="center">
  <img width="655" height="393" alt="image" src="https://github.com/user-attachments/assets/a555b5a1-05fa-40de-b628-d4db394ab14d" />
</div>

## Results and Impact
<!--Give the results and impact as shown below-->
The Decentralized LoRa Mesh Framework significantly enhances emergency response capabilities by providing a reliable communication link when standard infrastructure collapses. The experimental results validate that a simple, stateless smart-flooding protocol can achieve high reliability (98.5% PDR) even in difficult Non-Line-Of-Sight environments. This project serves as a foundation for scalable, off-grid communication solutions for first responders, enabling near real-time situational awareness.

This project serves as a foundation for future developments in assistive technologies and contributes to creating a more inclusive and accessible digital environment.

## Articles published / References
1. J. H. Kim, D. G. Lee, and S. W. Choi, “A Lightweight Synchronous Flooding Protocol for LoRa-Based Multi-Hop Networks in Emergency Scenarios,” ICOIN, 2025.

2. M. A. Kim, S. H. Lee, and J. Park, “Performance Analysis of LoRa-Based Multi-Hop Communication for Emergency Response Applications,” ICSECE, 2024.

3. A. Susanto, R. Setyawan, and E. Purnomo, “Design and Implementation of a LoRa-Based Mesh Network for an Early Warning Flood Disaster System,” ICITEE, 2023.



