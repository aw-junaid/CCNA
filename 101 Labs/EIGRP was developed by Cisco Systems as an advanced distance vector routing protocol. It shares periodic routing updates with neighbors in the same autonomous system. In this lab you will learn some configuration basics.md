Enhanced Interior Gateway Routing Protocol (EIGRP) is indeed developed by Cisco Systems, and it falls under the category of advanced distance vector routing protocols. EIGRP is designed to provide faster convergence and more features compared to traditional distance vector protocols like RIP. Here are some basics of EIGRP configuration:

### Basic EIGRP Configuration:

#### 1. **Enter Global Configuration Mode:**
   ```bash
   Router> enable
   Router# configure terminal
   ```

#### 2. **Enable EIGRP on the Router:**
   ```bash
   Router(config)# router eigrp AS_NUMBER
   ```
   - Replace `AS_NUMBER` with the Autonomous System (AS) number. It is a unique identifier for the EIGRP autonomous system.

#### 3. **Specify Networks to Advertise:**
   ```bash
   Router(config-router)# network NETWORK_ADDRESS
   ```
   - Replace `NETWORK_ADDRESS` with the network or subnet you want to include in EIGRP updates.

#### 4. **Adjust Hello and Hold Timers (Optional):**
   ```bash
   Router(config-router)# timers hello HELLO_INTERVAL hold HOLD_TIME
   ```
   - Optionally, you can adjust the hello and hold timers. The default hello interval is 5 seconds, and the default hold time is 15 seconds.

#### 5. **Specify Passive Interfaces (Optional):**
   ```bash
   Router(config-router)# passive-interface INTERFACE
   ```
   - Optionally, you can specify interfaces as passive to prevent EIGRP updates from being sent or received on those interfaces.

#### 6. **Exit Configuration Mode:**
   ```bash
   Router(config-router)# exit
   ```

#### 7. **Save Configuration:**
   ```bash
   Router# write memory
   ```

### Verification Commands:

#### 1. **Show EIGRP Configuration:**
   ```bash
   Router# show running-config | section eigrp
   ```
   - This command displays the EIGRP configuration in the running configuration.

#### 2. **Show EIGRP Neighbors:**
   ```bash
   Router# show ip eigrp neighbors
   ```
   - This command displays a list of EIGRP neighbors along with their addresses.

#### 3. **Show EIGRP Topology Table:**
   ```bash
   Router# show ip eigrp topology
   ```
   - This command shows the current EIGRP topology table.

#### 4. **Show EIGRP Interfaces:**
   ```bash
   Router# show ip eigrp interfaces
   ```
   - This command displays a summary of EIGRP-enabled interfaces.

### Notes:

- **EIGRP AS Number:**
  - The AS number is used to identify the EIGRP autonomous system. All routers within the same EIGRP AS share routing information.

- **Hello and Hold Timers:**
  - Adjusting timers can influence how quickly EIGRP routers detect the loss of a neighbor and converge.

- **Passive Interfaces:**
  - Configuring interfaces as passive helps in scenarios where you don't want EIGRP updates to be sent or received on specific interfaces.

- **Metric Calculation:**
  - EIGRP uses a composite metric that includes bandwidth, delay, reliability, load, and MTU. By default, EIGRP uses bandwidth and delay in its metric calculation.

This basic configuration is a starting point for deploying EIGRP in a network. Further adjustments and advanced features can be explored based on network requirements and design.
