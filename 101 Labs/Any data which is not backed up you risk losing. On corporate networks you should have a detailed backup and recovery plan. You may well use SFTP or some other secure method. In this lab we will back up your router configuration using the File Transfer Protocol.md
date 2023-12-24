Having a robust backup and recovery plan is crucial for safeguarding important data, especially on corporate networks. This includes regularly backing up configurations, files, and critical data to prevent data loss in the event of hardware failures, accidental deletions, or other unforeseen issues.

### Using File Transfer Protocol (FTP) for Router Configuration Backup:

#### 1. **Prerequisites:**
   - Ensure that an FTP server is set up and accessible on your network. You may use a dedicated FTP server software or a server with FTP capabilities.

#### 2. **Router Configuration Backup:**
   - Log in to the router's command-line interface (CLI).
   - Identify and note the configuration file that you want to back up (e.g., `startup-config` or `running-config`).

#### 3. **FTP Configuration on the Router:**
   - Configure the router to transfer the configuration file to the FTP server. Here is an example:

     ```plaintext
     Router(config)# copy running-config ftp:
     Address or name of remote host []? <FTP_Server_IP_Address>
     Destination filename [router-config]? <Desired_File_Name>
     ```

   - Replace `<FTP_Server_IP_Address>` with the IP address of your FTP server and `<Desired_File_Name>` with the preferred name for the backup file.

   - Enter FTP server login credentials when prompted.

#### 4. **Verification:**
   - Verify that the backup file is successfully transferred to the FTP server.

#### Important Considerations:

1. **Security:**
   - Ensure that the FTP connection is secure. Consider using Secure FTP (SFTP) or FTPS to encrypt the data during transfer.

2. **Automation:**
   - Consider automating the backup process using scripts or scheduled tasks to ensure regular backups without manual intervention.

3. **Storage Location:**
   - Store backup files in a secure location, and if possible, keep multiple versions to facilitate recovery from different points in time.

4. **Testing:**
   - Periodically test the restoration process to ensure that backups can be successfully restored when needed.

5. **Documentation:**
   - Maintain documentation that includes details of the backup process, schedules, and recovery procedures.

6. **Offsite Backups:**
   - Consider storing backups offsite to protect against physical disasters affecting the primary data center.

### Example (Cisco Router):

Here is an example of backing up the running configuration to an FTP server on a Cisco router:

```plaintext
Router# copy running-config ftp:
Address or name of remote host []? 192.168.1.100
Destination filename [router-config]? router_backup
Writing router_backup !
[OK - 1116 bytes]
Router#
```

In this example, the running configuration is copied to an FTP server with the IP address 192.168.1.100, and the backup file is named "router_backup."

Regularly backing up router configurations and critical data is a proactive measure to ensure data integrity and streamline the recovery process in the event of unexpected incidents.
