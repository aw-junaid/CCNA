EUI-64 (Extended Unique Identifier-64) addressing is a method used in IPv6 to automatically configure interface identifiers based on the interface's MAC (Media Access Control) address. This process involves converting the 48-bit MAC address into a 64-bit interface identifier by inserting a 16-bit value (FFFE) in the middle of the MAC address. This helps in creating a unique 64-bit interface identifier for the IPv6 address.

Here's a brief overview of the EUI-64 process:

1. **MAC Address:**
   - Consider a typical MAC address, such as `00:1A:2B:3C:4D:5E`.

2. **Insert FFFE:**
   - Insert the 16-bit value `FFFE` in the middle of the MAC address. The modified address becomes `00:1A:2B:FF:FE:3C:4D:5E`.

3. **Modify U/L Bit:**
   - The seventh bit of the MAC address, known as the Universal/Local (U/L) bit, is inverted to create the interface identifier. If the U/L bit is `0`, it becomes `1`, and if it is `1`, it becomes `0`.

4. **Create IPv6 Interface Identifier:**
   - The modified 64-bit MAC address is then used as the interface identifier in the IPv6 address.

### Example EUI-64 Configuration:

Assuming a MAC address of `00:1A:2B:3C:4D:5E`, the EUI-64 process would create an IPv6 interface identifier of `021A:2BFF:FE3C:4D5E`. Here's how you might configure an interface with EUI-64 addressing:

```bash
Router(config)# interface GigabitEthernet0/0/0
Router(config-if)# ipv6 address 2001:DB8::021A:2BFF:FE3C:4D5E/64 eui-64
```

In this example, replace `GigabitEthernet0/0/0` with the actual interface name, and `2001:DB8::` with the desired IPv6 network prefix.

### Notes:

- **EUI-64 Advantages:**
  - EUI-64 addressing is convenient for autoconfiguration, especially for hosts or devices with a known MAC address. It simplifies the process of generating unique interface identifiers.

- **Privacy Considerations:**
  - EUI-64 addresses, by including a modified MAC address, may compromise privacy as it exposes the device's hardware address. Some IPv6 deployments use other methods, such as privacy extensions, to address this concern.

- **Configuration Options:**
  - While EUI-64 is a common method for autoconfiguration, it's not the only option. Some networks may use alternative methods or manual configuration depending on the specific requirements and policies.

Understanding EUI-64 addressing is important for IPv6 administrators, especially when dealing with device autoconfiguration and addressing in IPv6 networks.
