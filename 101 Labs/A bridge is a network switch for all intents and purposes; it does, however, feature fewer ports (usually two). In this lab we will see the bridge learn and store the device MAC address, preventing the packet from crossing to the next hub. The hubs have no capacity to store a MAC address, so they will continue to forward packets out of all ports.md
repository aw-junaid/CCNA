In this lab, we will set up a basic network with a bridge and two hubs. The bridge will learn and store MAC addresses to make forwarding decisions, while the hubs will simply forward packets out of all ports without MAC address learning capabilities.

### Lab Configuration Overview:

- **Bridge (Switch):**
  - Ports: Port 1 and Port 2
  - Learning MAC Addresses

- **Hub 1:**
  - Connected to the Bridge (Port 1)

- **Hub 2:**
  - Connected to the Bridge (Port 2)

### Basic Steps:

#### 1. **Physical Connections:**
   - Connect the bridge and two hubs using appropriate cables.
   - Bridge Port 1 to Hub 1.
   - Bridge Port 2 to Hub 2.

#### 2. **Configure Bridge (Switch):**
   - Access the console or management interface of the bridge.

#### 3. **Enter Privileged EXEC Mode:**
   - Enter privileged EXEC mode on the bridge:
     ```bash
     Bridge> enable
     ```

#### 4. **Enter Global Configuration Mode:**
   - Enter global configuration mode on the bridge:
     ```bash
     Bridge# configure terminal
     ```

#### 5. **Configure Bridge Ports:**
   - Configure the bridge ports (Port 1 and Port 2):
     ```bash
     Bridge(config)# interface fastethernet0/1
     Bridge(config-if)# spanning-tree portfast
     Bridge(config-if)# end

     Bridge(config)# interface fastethernet0/2
     Bridge(config-if)# spanning-tree portfast
     Bridge(config-if)# end
     ```

#### 6. **Verify Bridge Configuration:**
   - Verify the bridge configuration:
     ```bash
     Bridge# show running-config
     ```

#### 7. **Connect Hosts to Hubs:**
   - Connect devices (hosts or computers) to the hubs.

#### 8. **Observe MAC Learning:**
   - Observe MAC address learning on the bridge. When devices on the hubs communicate, the bridge will learn and store their MAC addresses.

#### 9. **Observe Forwarding Behavior:**
   - Observe how the bridge forwards traffic based on MAC addresses.
   - Devices connected to different hubs will communicate through the bridge, and the bridge will forward packets only to the relevant port where the destination MAC address is located.

### Note:
- Bridges, which are essentially switches, learn MAC addresses and build a MAC address table to make forwarding decisions.
- Hubs operate at the physical layer and do not have the capability to store MAC addresses. They simply broadcast packets to all connected ports.
- The specific commands and steps may vary based on the bridge or switch model and software. Consult the documentation for your equipment.

This lab demonstrates the basic functionality of a bridge (switch) in a network, highlighting its ability to learn and store MAC addresses for efficient packet forwarding.
