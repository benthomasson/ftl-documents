
# How to Set Up a Minecraft Java Edition Server

## Requirements
- A computer with sufficient hardware (refer to System and Performance below)
- Java 8 or newer installed (Java 21 recommended for latest versions)
- server.jar file downloaded from Mojang's official site
- Basic understanding of command-line operations

## Tools Needed
- **java_tool**: To run the Minecraft server.
- **bash_tool**: For creating and running shell scripts.
- **chmod_tool**: To set executable permissions on scripts.
- **wget_tool**: To download Java if not installed.

## User Questions
1. Do I need a GUI to run the server?
2. How do I configure port forwarding for external access?
3. What are the recommended system specifications?

## Implementation Steps

### 1. Install Java
- **Windows**:
  - Use Winget: `winget install EclipseAdoptium.Temurin.21.JRE`
- **Linux (Ubuntu/Debian-based)**:
  - Run: `sudo apt update && sudo apt install openjdk-21-jdk-headless`
- **macOS**:
  - Install via Homebrew: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` then `brew install --cask temurin@21`

### 2. Download Minecraft Server
- Visit [Mojang's official server download page](https://www.minecraft.net/en-us/download/server).
- Rename the downloaded file to `server.jar`.

### 3. Create a Server Directory
- Choose a location for your server files.
- Place `server.jar` in this directory.

### 4. Start the Minecraft Server
- Open a terminal or command prompt.
- Navigate to the server directory.
- Run: `java -jar server.jar --nogui`

### 5. Accept the EULA
- The first run generates an `eula.txt` file.
- Edit it and set `eula=true`.

### 6. Create a Startup Script (Optional)
- **Windows**:
  - Create a batch file (`start.bat`):
    ```batch
    @ECHO OFF
    java -Xms1024M -Xmx2048M -jar server.jar --nogui
    pause
    ```
- **Linux/macOS**:
  - Create a shell script (`start.sh`):
    ```sh
    #!/bin/sh
    cd "$(dirname "$0")"
    exec java -Xms1024M -Xmx2048M -jar server.jar --nogui
    ```
  - Make it executable: `chmod +x start.sh`

### 7. Configure Server Settings
- Edit `server.properties` to set port, whitelist, and other settings.
- Example: Set port to 25565:
  ```properties
  server-port=25565
  ```

### 8. Port Forwarding (For External Access)
- Log into your router's admin page.
- Add a new port forwarding rule:
  - External Port: 25565
  - Internal IP: Your server's internal IP
  - Internal Port: 25565

### 9. Whitelist and Operators
- Enable whitelist in `server.properties`:
  ```properties
  white-list=true
  ```
- Add players to `whitelist.json` or use the `/whitelist add <player>` command.

### 10. Secure Your Server
- Regularly update Minecraft server software.
- Backup your world directory.

## Troubleshooting Common Issues
1. **Connection Refused**:
   - Ensure port forwarding is correctly set up.
   - Check firewall settings to allow incoming connections on the specified port.

2. **Java Path Issues**:
   - Add Java to your PATH environment variable if scripts don't recognize `java`.

3. **Server Not Starting**:
   - Verify that `eula.txt` has `eula=true`.
   - Ensure no other process is using the port.

## Frequently Asked Questions
- **Q**: How do I increase server RAM?
  - Adjust `-Xms` and `-Xmx` in your startup script.
- **Q**: Why is my server unresponsive?
  - Check for high entity counts or insufficient hardware resources.
- **Q**: Can't connect from outside the LAN?
  - Ensure port forwarding is correctly configured and external IP is used.

By following these steps, you can successfully set up a Minecraft Java Edition server.