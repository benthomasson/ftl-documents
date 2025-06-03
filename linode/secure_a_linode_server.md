
# Setup and Secure a Compute Instance

**Requirements**
- SSH or LISH Console access
- Root privileges
- Internet connection for updates

**Tools Needed**
- apt_tool
- bash_tool
- chmod_tool
- chown_tool
- hostname_tool
- user_tool
- service_tool

**User Questions**
- What is the IP address of your Compute Instance?
- Do you have an existing SSH key pair, or would you like to generate one?

**Implementation Steps**

## 1. Connect to the Compute Instance
### As Root User
```bash
ssh root@192.0.2.17
```

## 2. Perform System Updates
Run the following command to update your system:
```bash
apt update && apt upgrade -y
```

## 3. Set Timezone
Set the timezone using timedatectl:
```bash
timedatectl list-timezones
timedatectl set-timezone 'America/New_York'
timedatectl show --property=Timezone
```

## 4. Configure Custom Hostname
Set a custom hostname:
```bash
hostnamectl set-hostname web-server.example.com
```
Edit `/etc/hosts` to include the new hostname and FQDN.

## 5. Add Limited User Account
Create a new user and add to sudo group:
```bash
adduser example_user
adduser example_user sudo
```

## 6. Harden SSH Access

### Create and Upload SSH Key Pair
Generate an SSH key pair on your local machine:
```bash
ssh-keygen -t ed25519 -C "user@domain.tld"
```
Upload the public key to the server using `ssh-copy-id` or manually append it to `~/.ssh/authorized_keys`.

### Configure SSH Settings
Edit `/etc/ssh/sshd_config`:
```bash
PermitRootLogin no
PasswordAuthentication no
AddressFamily inet
```

## 7. Restart SSH Service
Restart SSH to apply changes:
```bash
systemctl restart sshd
```

**Verification Steps**
- Confirm system updates are applied by checking package versions.
- Verify timezone settings with `date`.
- Check hostname resolution by pinging the FQDN.
- Ensure SSH login is restricted to your user and key-based authentication only.

**Produces**
- A secure, updated Compute Instance ready for production use.
