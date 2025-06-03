
<!-- based on  https://github.com/containers/podman.io/blob/main/docs/installation.md -->


# Podman Installation Instructions

## Requirements
- Internet connection for downloading packages
- Compatible operating system (macOS, Windows, Linux distributions, FreeBSD)

## Tools Needed
- apt_tool - For Debian/Ubuntu-based systems
- dnf_tool - For Fedora/CentOS Stream/RHEL-based systems
- pacman_tool - For Arch Linux/Manjaro
- apk_tool - For Alpine Linux
- zypper_tool - For openSUSE
- brew_tool - Optional for macOS (not recommended)
- git_tool - For cloning source repositories
- make_tool - For building from source

## User Questions
- Which operating system are you using?
- Do you prefer to install Podman via package manager or build from source?

## Implementation Steps
### On Linux
1. **Debian/Ubuntu-based systems**:
   ```bash
   sudo apt-get update && sudo apt-get -y install podman
   ```
2. **Fedora/CentOS Stream/RHEL-based systems**:
   ```bash
   sudo dnf -y install podman
   ```
3. **Arch Linux/Manjaro**:
   ```bash
   sudo pacman -S podman
   ```
4. **Alpine Linux**:
   ```bash
   sudo apk add podman
   ```

### On macOS
1. Download and install Podman from [Podman.io](https://podman.io).
2. Initialize and start the first machine:
   ```bash
   podman machine init && podman machine start
   ```
3. Verify installation:
   ```bash
   podman info
   ```

### On Windows
1. Install Podman for Windows from [GitHub](https://github.com/containers/podman/blob/main/docs/tutorials/podman-for-windows.md).
2. Follow the guide for setup and usage.

### Building from Source
1. Clone the repository:
   ```bash
   git clone https://github.com/containers/podman.git
   ```
2. Build and install:
   ```bash
   cd podman && make BUILDTAGS="selinux seccomp" PREFIX=/usr && sudo make install PREFIX=/usr
   ```

## Verification Steps
1. Check if Podman is installed:
   ```bash
   podman --version
   ```
2. Verify container functionality by pulling an image:
   ```bash
   podman pull docker.io/library/alpine
   podman run -it docker.io/library/alpine sh
   ```

## Produces
- Installed and functional Podman environment
```
