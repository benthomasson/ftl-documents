

# How to secure a linux server

**Dependencies**

- A provisioned linux machine

**Tools Required**

- dnf_tool
- hostname_tool
- ssh_keygen_tool
- ssh_useradd_tool
- sshd_config_tool
- firewall_tool

**Questions**

- What is the name of the server?
- What is the IP address of the server?
- What is the username for the SSH user?
- What is the password for the SSH user?
- What is the public key for the SSH user?
- What is the private key for the SSH user?
- What is the port number for the SSH service?
- What is the firewall rule to allow SSH traffic?
- What is the firewall rule to deny all other traffic?

**Implementation Steps**

1. Install dnf_tool on the server.
2. Run hostname_tool to set the hostname of the server.
3. Run ssh_keygen_tool to generate a new SSH key pair for the user.
4. Run ssh_useradd_tool to add the user with the public key and password.
5. Run sshd_config_tool to configure the SSH service to use the private key and allow only the specified port number.
6. Run firewall_tool to open the specified port number for incoming traffic and deny all other traffic.
7. Restart the SSH service to apply the changes.
8. Secure the SSH configuration file by setting appropriate permissions and disabling root login.
9. Restart the SSH service to apply the changes.

**Verification Steps**

1. Test the SSH connection with the user credentials.
2. Verify that the server is accessible from outside the network using the public IP address of the server.
3. Test the SSH connection with the user credentials again.
4. Verify that the server is not accessible from outside the network using the public IP address of the server.
