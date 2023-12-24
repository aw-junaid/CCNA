Configuring Network Time Protocol (NTP) on a Cisco router involves setting up the router as an NTP server and configuring other devices to synchronize their clocks with the router. Here's a step-by-step guide:

### Step 1: Configure NTP on the Cisco Router

1. **Enter Global Configuration Mode:**
   ```bash
   Router> enable
   Router# configure terminal
   ```

2. **Specify NTP Server:**
   ```bash
   Router(config)# ntp master
   ```

   This command configures the router as an NTP master, allowing it to provide time to other devices.

3. **Set Stratum Level (Optional):**
   ```bash
   Router(config)# ntp master stratum 8
   ```

   Optionally, you can set the stratum level. The default is 8.

4. **Specify NTP Source Interface (Optional):**
   ```bash
   Router(config)# ntp source Loopback0
   ```

   If your router has multiple interfaces, you can specify the source interface for NTP.

5. **Configure NTP Authentication (Optional but Recommended):**
   ```bash
   Router(config)# ntp authenticate
   Router(config)# ntp authentication-key 1 md5 YourSecretKey
   Router(config)# ntp trusted-key 1
   Router(config)# ntp update-calendar
   ```

   Replace `YourSecretKey` with the desired secret key. This step adds a layer of security by enabling NTP authentication.

### Step 2: Configure NTP on Other Devices

6. **Enter Global Configuration Mode:**
   ```bash
   Device> enable
   Device# configure terminal
   ```

7. **Specify NTP Server:**
   ```bash
   Device(config)# ntp server RouterIPAddress
   ```

   Replace `RouterIPAddress` with the actual IP address of your Cisco router.

8. **Configure NTP Authentication on Devices (Optional):**
   ```bash
   Device(config)# ntp authenticate
   Device(config)# ntp authentication-key 1 md5 YourSecretKey
   Device(config)# ntp trusted-key 1
   ```

   If you configured NTP authentication on the router, repeat the authentication configuration on the devices.

### Step 3: Verify NTP Configuration

9. **Verify NTP Status:**
   ```bash
   Router# show ntp status
   ```

   Check the NTP status on the router to ensure it is synchronized.

10. **Verify NTP Peers on Devices:**
   ```bash
   Device# show ntp associations
   ```

   Check the NTP associations on the devices to verify synchronization with the router.

### Notes:

- **NTP Versions:**
  - The commands above are applicable to Cisco routers running IOS. For routers running IOS-XE, IOS-XR, or other operating systems, the commands might be slightly different.

- **Security Considerations:**
  - Using NTP authentication is recommended for security. Ensure that the key used for authentication is kept secure.

- **Stratum Levels:**
  - The stratum level represents the "distance" from the authoritative time source. Lower stratum values indicate more accurate time sources.

- **Loopback Interface (Optional):**
  - Using a loopback interface as the NTP source helps in case of interface failures.

- **Time Zone Configuration:**
  - Ensure that the time zone is correctly configured on both the router and other devices.

This guide provides a basic setup for NTP on a Cisco router and synchronization with other devices. Adjustments might be necessary based on your network and device models.
