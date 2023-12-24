Setting up routers in a branch office and headquarters involves several steps, and the specific configurations may vary based on the networking requirements and equipment used. Here, I'll outline a basic example of connecting two routers, one in the branch office (R1) and one in the headquarters (R0), with a focus on essential steps.

### Lab Configuration Overview:

- **Headquarters (HQ): R0**
  - IP Address: 192.168.1.1/24
  - Interface: GigabitEthernet0/0 (connected to the branch office router)

- **Branch Office: R1**
  - IP Address: 192.168.1.2/24
  - Interface: GigabitEthernet0/0 (connected to the headquarters router)

### Basic Steps:

#### 1. **Physical Connections:**
   - Physically connect the routers using appropriate cables. Ensure proper connectivity between the GigabitEthernet interfaces on R0 and R1.

#### 2. **Access Router Console:**
   - Access the console of each router using a terminal emulator (such as PuTTY or HyperTerminal).

#### 3. **Enter Privileged EXEC Mode:**
   - Enter privileged EXEC mode on each router by typing:
     ```bash
     R0> enable
     R1> enable
     ```

#### 4. **Enter Global Configuration Mode:**
   - Enter global configuration mode on each router:
     ```bash
     R0# configure terminal
     R1# configure terminal
     ```

#### 5. **Assign IP Addresses to Interfaces:**
   - Assign IP addresses to the interfaces of R0 and R1:
     ```bash
     R0(config)# interface GigabitEthernet0/0
     R0(config-if)# ip address 192.168.1.1 255.255.255.0
     R0(config-if)# no shutdown

     R1(config)# interface GigabitEthernet0/0
     R1(config-if)# ip address 192.168.1.2 255.255.255.0
     R1(config-if)# no shutdown
     ```

#### 6. **Configure Routing:**
   - Configure routing on each router. For simplicity, let's use static routing:
     ```bash
     R0(config)# ip route 192.168.2.0 255.255.255.0 192.168.1.2

     R1(config)# ip route 192.168.1.0 255.255.255.0 192.168.1.1
     ```

#### 7. **Verify Connectivity:**
   - Verify connectivity between the routers by pinging each other:
     ```bash
     R0# ping 192.168.1.2

     R1# ping 192.168.1.1
     ```

### Note:
- The IP addresses and subnet masks used in this example are for illustration purposes. Actual configurations will depend on your network requirements.
- Depending on your specific routers and their interfaces, the configuration commands may vary. Consult the documentation for your router model.

This is a basic setup, and in a real-world scenario, additional configurations (such as security measures, dynamic routing protocols, etc.) may be necessary based on the network design and security policies. Always refer to the specific documentation for your router models and networking requirements.
