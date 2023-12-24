Extended Access Control Lists (ACLs) offer more granularity and flexibility compared to Standard ACLs. While Standard ACLs focus on filtering traffic based solely on the source IP address, Extended ACLs provide additional criteria for filtering, including source and destination IP addresses, port numbers, and protocols.

Here's a breakdown of the key differences:

### Standard ACLs:

- **Filtering Criteria:**
  - Standard ACLs are limited to filtering traffic based on the source IP address only.
- **Use Cases:**
  - Standard ACLs are typically used when the filtering decision is based solely on the source network or host, without considering the destination or specific services.

#### Example Standard ACL:

```bash
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip access-group 1 in
```

In this example, Standard ACL 1 permits all traffic from the source network `192.168.1.0/24`.

### Extended ACLs:

- **Filtering Criteria:**
  - Extended ACLs allow filtering based on various criteria, including source and destination IP addresses, port numbers, and protocols.
- **Use Cases:**
  - Extended ACLs are suitable for scenarios where more specific control is needed, such as allowing or denying traffic based on source and destination, specific applications (using port numbers), or protocols.

#### Example Extended ACL:

```bash
Router(config)# access-list 101 permit tcp 192.168.1.0 0.0.0.255 host 203.0.113.5 eq 80
Router(config)# access-list 101 deny ip any any
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip access-group 101 in
```

In this example, Extended ACL 101 permits TCP traffic from the source network `192.168.1.0/24` to the destination host `203.0.113.5` on port `80`, while denying all other IP traffic.

### Key Advantages of Extended ACLs:

1. **Destination Filtering:**
   - Extended ACLs allow filtering based on destination IP addresses, providing more control over traffic flow.

2. **Port and Protocol Filtering:**
   - Extended ACLs enable filtering based on specific port numbers and protocols, allowing administrators to control access to specific services.

3. **Greater Granularity:**
   - The ability to specify multiple criteria in a single ACL entry provides greater granularity in defining filtering policies.

Extended ACLs are a powerful tool for network administrators when fine-tuned control over traffic is required, especially when considering both source and destination addresses, as well as specific applications or services.
