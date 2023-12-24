EIGRP for IPv6, also known as EIGRPv6, is an extension of EIGRP designed to support IPv6 networks. While EIGRP for IPv4 and EIGRPv6 share many similarities, there are some configuration differences, including the need to configure EIGRPv6 under the interface. Here are the basic steps for configuring EIGRPv6:

### Basic EIGRPv6 Configuration:

#### 1. **Enter Global Configuration Mode:**
   ```bash
   Router> enable
   Router# configure terminal
   ```

#### 2. **Enter Interface Configuration Mode:**
   ```bash
   Router(config)# interface INTERFACE_NAME
   ```

#### 3. **Enable EIGRPv6 on the Interface:**
   ```bash
   Router(config-if)# ipv6 eigrp AS_NUMBER
   ```
   - Replace `AS_NUMBER` with the EIGRP autonomous system number.

#### 4. **Specify EIGRPv6 Router ID (Optional):**
   ```bash
   Router(config-if)# ipv6 eigrp router-id ROUTER_ID
   ```
   - Optionally, you can specify the router ID for the EIGRP process.

#### 5. **Exit Interface Configuration Mode:**
   ```bash
   Router(config-if)# exit
   ```

#### 6. **Configure EIGRPv6 Globally (Optional):**
   - Optionally, you can configure EIGRPv6 globally if you want to set parameters that apply to the entire routing process.
   ```bash
   Router(config)# ipv6 router eigrp AS_NUMBER
   Router(config-rtr)# router-id ROUTER_ID
   ```

#### 7. **Verification Commands:**
   - After configuring EIGRPv6, you can use the following commands to verify its operation:
   ```bash
   Router# show ipv6 eigrp neighbors
   Router# show ipv6 eigrp topology
   ```

### Notes:

- **EIGRPv6 AS Number:**
  - EIGRPv6 uses a separate AS number for IPv6 networks. Ensure consistency in the AS number across routers within the same EIGRPv6 domain.

- **Interface-Level Configuration:**
  - Unlike EIGRP for IPv4, where configuration is typically done at the global level, EIGRPv6 requires configuration under each interface participating in EIGRP.

- **Router ID:**
  - A router ID is used to uniquely identify a router within an EIGRP AS. If not configured manually, EIGRPv6 will automatically select a router ID.

- **Global EIGRPv6 Configuration:**
  - Some EIGRPv6 parameters, such as router ID, can be configured globally, but the main configuration is done under each interface.

### Example Configuration:

Here's an example of basic EIGRPv6 configuration:

```bash
Router(config)# interface GigabitEthernet0/0/0
Router(config-if)# ipv6 eigrp 100
Router(config-if)# exit

Router(config)# ipv6 router eigrp 100
Router(config-rtr)# router-id 1.1.1.1
```

In this example, replace `100` with the EIGRP AS number and `1.1.1.1` with the desired router ID.

EIGRPv6 provides efficient and scalable routing for IPv6 networks. The configuration, while similar to EIGRP for IPv4, includes specific adjustments to accommodate IPv6 addressing and network requirements.
