In this lab, we will observe the behavior of hubs, which do not have the capability to store MAC address tables. Every packet or frame received by a hub is simply broadcasted out of all ports, leading to potential network congestion. This lab will illustrate the lack of MAC address learning and forwarding limitations in a hub-based network.

### Lab Configuration Overview:

- **Hub:**
  - Connected to multiple devices (Hosts/Computers)
  - Every port on the hub will forward packets to all connected devices.

### Basic Steps:

#### 1. **Physical Connections:**
   - Connect a hub to multiple devices (hosts or computers) using appropriate cables.

#### 2. **Observe Hub Ports:**
   - Observe the behavior of the hub ports. Since hubs operate at the physical layer, every packet received on any port is broadcasted out of all other ports.

#### 3. **Connect Network Analyzer (Optional):**
   - If available, connect a network analyzer or packet sniffer to one of the hub ports to capture and analyze network traffic.

#### 4. **Generate Traffic:**
   - Generate network traffic by initiating communication between devices connected to the hub. For example, ping one device from another.

#### 5. **Observe Packet Broadcasting:**
   - Observe that every packet sent by one device is broadcasted to all devices connected to the hub, including the device that is the actual intended recipient.

#### 6. **Check for Network Congestion:**
   - As more devices communicate simultaneously, observe the potential for network congestion. Since every packet is sent to all ports, the overall bandwidth is shared among all devices.

#### 7. **Observe Lack of MAC Learning:**
   - Unlike switches, hubs do not learn MAC addresses, and they do not store a table of which devices are connected to which port. Therefore, each packet is treated as a broadcast and sent to all ports.

### Note:
- Hubs operate at the physical layer of the OSI model and lack intelligence compared to switches. They do not have the ability to learn MAC addresses or make forwarding decisions based on addresses.
- The lack of MAC address learning in hubs results in inefficient use of network bandwidth, as every packet is forwarded to all connected devices.
- This lab helps illustrate the limitations of hubs and the advantages of using switches in modern network configurations.

Remember that hubs are considered legacy devices, and in modern network setups, switches are used to provide more efficient and intelligent packet forwarding based on MAC address tables.
