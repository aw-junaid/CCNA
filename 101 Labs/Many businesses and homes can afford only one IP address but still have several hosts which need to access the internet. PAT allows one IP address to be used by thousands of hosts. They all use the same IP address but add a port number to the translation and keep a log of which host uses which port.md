Port Address Translation (PAT), also known as Dynamic NAT Overload or NAT with Overloading, is a form of Network Address Translation (NAT) that allows multiple private IP addresses within a local network to share a single public IP address. It achieves this by using unique port numbers to distinguish between connections from different devices.

Here's a brief overview of how PAT works:

1. **Shared Public IP Address:**
   - Multiple devices within the private network share a single public IP address for accessing resources on the internet. This public IP address is the one visible to external servers.

2. **Port Numbers:**
   - Each device is assigned a unique port number when it initiates a connection to the internet. The combination of the shared public IP address and the unique port number is used to distinguish between different devices.

3. **Translation Table:**
   - The router or firewall performing PAT maintains a translation table that keeps track of the mapping between private IP addresses, port numbers, and the shared public IP address.

4. **Dynamic Allocation:**
   - Port numbers are dynamically allocated as needed, and when a connection is terminated, the port number is returned to the pool for reuse.

### Example Configuration:

Here's a basic example of how you might configure PAT on a router:

```bash
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip address 203.0.113.1 255.255.255.0
Router(config-if)# exit

Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# ip nat inside
Router(config-if)# exit

Router(config)# ip nat inside source list 1 interface GigabitEthernet0/0 overload

Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
```

In this example:

- The router has two interfaces (`GigabitEthernet0/0` and `GigabitEthernet0/1`), where `GigabitEthernet0/0` is connected to the internet and `GigabitEthernet0/1` is connected to the private network (192.168.1.0/24).

- The `ip nat inside source list 1 interface GigabitEthernet0/0 overload` command specifies that NAT translation should be applied to traffic from the devices in the `192.168.1.0/24` network, and the `overload` keyword indicates the use of PAT.

- An access control list (ACL) is used (`access-list 1 permit 192.168.1.0 0.0.0.255`) to identify the range of private IP addresses subject to NAT.

This configuration allows multiple devices in the private network to share a single public IP address using different port numbers.

PAT is a widely used technique in scenarios where a limited number of public IP addresses are available, and it's a cost-effective way to enable internet connectivity for a large number of devices within a private network.
