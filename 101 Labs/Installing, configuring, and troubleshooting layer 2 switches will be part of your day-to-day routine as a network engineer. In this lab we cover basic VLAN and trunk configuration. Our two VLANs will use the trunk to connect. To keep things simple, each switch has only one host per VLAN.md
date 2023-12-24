Configuring VLANs (Virtual Local Area Networks) and trunks on layer 2 switches is a fundamental task for network engineers. Here's a basic example lab that covers VLAN and trunk configuration with two switches. Each switch will have one host per VLAN.

### Lab Configuration Overview:

- **Switch 1 (SW1):**
  - VLAN 10 (Data VLAN): Host 1 (PC1) - 192.168.10.1
  - VLAN 20 (Voice VLAN): Host 2 (PC2) - 192.168.20.1
  - Trunk Interface: GigabitEthernet0/1

- **Switch 2 (SW2):**
  - VLAN 10 (Data VLAN): Host 3 (PC3) - 192.168.10.2
  - VLAN 20 (Voice VLAN): Host 4 (PC4) - 192.168.20.2
  - Trunk Interface: GigabitEthernet0/1

### Basic Steps:

#### 1. **Physical Connections:**
   - Physically connect the switches using appropriate cables. Ensure proper connectivity between the trunk interfaces (GigabitEthernet0/1) on SW1 and SW2.

#### 2. **Access Switch Console:**
   - Access the console of each switch using a terminal emulator.

#### 3. **Enter Privileged EXEC Mode:**
   - Enter privileged EXEC mode on each switch:
     ```bash
     SW1> enable
     SW2> enable
     ```

#### 4. **Enter Global Configuration Mode:**
   - Enter global configuration mode on each switch:
     ```bash
     SW1# configure terminal
     SW2# configure terminal
     ```

#### 5. **Create VLANs:**
   - Create VLANs on each switch:
     ```bash
     SW1(config)# vlan 10
     SW1(config-vlan)# name DataVLAN

     SW1(config)# vlan 20
     SW1(config-vlan)# name VoiceVLAN

     SW2(config)# vlan 10
     SW2(config-vlan)# name DataVLAN

     SW2(config)# vlan 20
     SW2(config-vlan)# name VoiceVLAN
     ```

#### 6. **Assign VLANs to Interfaces:**
   - Assign VLANs to the interfaces on each switch:
     ```bash
     SW1(config)# interface GigabitEthernet0/1
     SW1(config-if)# switchport mode trunk
     SW1(config-if)# switchport trunk allowed vlan 10,20

     SW2(config)# interface GigabitEthernet0/1
     SW2(config-if)# switchport mode trunk
     SW2(config-if)# switchport trunk allowed vlan 10,20
     ```

#### 7. **Assign IP Addresses to Hosts:**
   - Assign IP addresses to hosts in their respective VLANs:
     - PC1: 192.168.10.1
     - PC2: 192.168.20.1
     - PC3: 192.168.10.2
     - PC4: 192.168.20.2

#### 8. **Verify Connectivity:**
   - Verify connectivity between hosts in different VLANs:
     - Ping from PC1 to PC3 (Data VLAN).
     - Ping from PC2 to PC4 (Voice VLAN).

### Note:
- The IP addresses and VLAN IDs used in this example are for illustration purposes. Actual configurations will depend on your network requirements.
- The specific commands may vary based on the switch models and software versions. Consult the documentation for your switches.

This lab sets up a basic VLAN and trunk configuration. In a production environment, additional configurations, such as VLAN routing, security measures, and dynamic trunking protocols, may be implemented based on the network design and requirements.
