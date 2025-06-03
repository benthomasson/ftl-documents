
# Set Up and Secure a Compute Instance

## Requirements
- SSH access to the Compute Instance
- Root privileges or sudo access
- Internet connection for updates

## Tools Needed
- `ssh_tool` - Connect to remote servers via SSH
- `apt_tool`/`dnf_tool` - Update system packages
- `timedatectl_tool` - Set timezone
- `hostnamectl_tool` - Configure hostname
- `user_tool` - Create user accounts
- `sshd_config_tool` - Secure SSH access
- `firewalld_tool` - Configure firewall

## User Questions
- What is the IP address of the Compute Instance?
- Which Linux distribution is installed on the Compute Instance?

## Implementation Steps
1. **Connect to the Compute Instance**
   ```bash
   ssh root@<instance_ip>
   ```

2. **Update System Packages**
   - For Debian/Ubuntu:
     ```bash
     apt update && apt upgrade -y
     ```
   - For CentOS/RHEL:
     ```bash
     dnf upgrade -y
     ```

3. **Set Timezone**
   ```bash
   timedatectl set-timezone 'America/New_York'
   ```

4. **Configure Hostname**
   ```bash
   hostnamectl set-hostname example-hostname
   ```

5. **Create Limited User Account**
   - Add user:
     ```bash
     adduser example_user && passwd example_user
     ```
   - Grant sudo privileges:
     ```bash
     adduser example_user sudo
     ```

6. **Harden SSH Access**
   - Edit SSH config to disable root login and password auth:
     ```bash
     nano /etc/ssh/sshd_config
     ```
     Set `PermitRootLogin no` and `PasswordAuthentication no`.
   - Restart SSH service:
     ```bash
     systemctl restart sshd
     ```

7. **Upload SSH Key**
   ```bash
   ssh-copy-id example_user@<instance_ip>
   ```

8. **Configure Firewall**
   ```bash
   firewall-cmd --permanent --add-service=ssh
   firewall-cmd --reload
   ```

9. **Verify Configuration**
   - Check SSH status:
     ```bash
     systemctl status sshd
     ```
   - Test user login with SSH key.

## Verification Steps
1. **SSH Connection Test**
   - Attempt to connect as the new user without a password.
2. **Root Login Check**
   - Ensure root cannot log in via SSH.
3. **Package Updates Verified**
   - Confirm all updates are installed successfully.
4. **Firewall Rules**
   - Verify only necessary ports (e.g., SSH) are open.

## Produces
- A secure and updated Compute Instance with limited access and hardened security measures.