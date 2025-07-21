# Ethical Hacking - Day 02 Notes

## 📚 Course Overview
**Date:** 18/07/2025 
**Duration:** 2 hours  
**Focus:** Booting Kali Linux

# VirtualBox Kali Linux Setup Guide

This guide provides step-by-step instructions for downloading VirtualBox and setting up Kali Linux in a virtual machine environment.

## Important Note for Mac Users

**If you're using a Mac with Apple Silicon (M1, M2, M3 chips), VirtualBox may not work properly or at all.** VirtualBox has limited support for ARM-based processors. In such cases, **UTM is recommended as an alternative** virtualization solution that works excellently with Apple Silicon Macs.

### Alternative for Mac Users: UTM
- Download UTM from: https://mac.getutm.app/
- UTM provides better performance and compatibility on Apple Silicon Macs
- Follow similar setup principles but use UTM's interface instead of VirtualBox

## Prerequisites

- Computer with at least 4GB RAM (8GB recommended)
- At least 20GB free disk space
- 64-bit processor with virtualization support
- Administrative privileges on your system

## Step 1: Download VirtualBox

### For Windows/macOS/Linux:

1. Visit the official VirtualBox website: https://www.virtualbox.org/
2. Click on "Downloads" in the navigation menu
3. Select your operating system:
   - **Windows**: Download "Windows hosts"
   - **macOS**: Download "OS X hosts"
   - **Linux**: Choose your distribution (Ubuntu, Debian, etc.)
4. Download the latest version (currently VirtualBox 7.x)

### Installation:

**Windows:**
1. Run the downloaded `.exe` file as administrator
2. Follow the installation wizard
3. Accept the license agreement
4. Choose installation directory (default is recommended)
5. Select components to install (keep all selected)
6. Click "Install" and wait for completion
7. Restart your computer if prompted

**macOS:**
1. Open the downloaded `.dmg` file
2. Double-click the VirtualBox installer package
3. Follow the installation prompts
4. You may need to allow the installation in System Preferences > Security & Privacy
5. Restart if required

**Note:** If VirtualBox doesn't work on your Mac (especially Apple Silicon Macs), consider using UTM instead.

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install virtualbox virtualbox-ext-pack
```

## Step 2: Download Kali Linux ISO

1. Visit the official Kali Linux website: https://www.kali.org/
2. Navigate to "Get Kali" or "Downloads"
3. Choose the appropriate version:
   - **Recommended**: "Installer Images" > "64-bit"
   - Download the `.iso` file (approximately 3-4GB)
4. Verify the download integrity using the provided checksums (optional but recommended)

## Step 3: Create a New Virtual Machine

1. **Launch VirtualBox**
   - Open VirtualBox from your applications menu

2. **Create New VM**
   - Click "New" or press Ctrl+N
   - Name: Enter "Kali Linux" or any preferred name
   - Type: Select "Linux"
   - Version: Select "Debian (64-bit)"
   - Click "Next"

3. **Configure Memory (RAM)**
   - Allocate at least 2048 MB (2GB)
   - Recommended: 4096 MB (4GB) or more
   - Click "Next"

4. **Create Virtual Hard Disk**
   - Select "Create a virtual hard disk now"
   - Click "Create"
   - Choose "VDI (VirtualBox Disk Image)"
   - Click "Next"
   - Select "Dynamically allocated"
   - Click "Next"
   - Set disk size to at least 20GB (recommended: 40GB+)
   - Click "Create"

## Step 4: Configure Virtual Machine Settings

1. **Select your VM** and click "Settings"

2. **System Settings:**
   - Go to "System" > "Motherboard"
   - Ensure "Enable I/O APIC" is checked
   - Go to "System" > "Processor"
   - Allocate 2+ CPU cores if available
   - Enable "Enable PAE/NX"

3. **Display Settings:**
   - Go to "Display"
   - Increase "Video Memory" to 128 MB
   - Enable "3D Acceleration" (optional)

4. **Storage Settings:**
   - Go to "Storage"
   - Click on "Empty" under "Controller: IDE"
   - Click the CD icon next to "Optical Drive"
   - Select "Choose a disk file"
   - Browse and select your downloaded Kali Linux ISO file
   - Click "OK"

5. **Network Settings (Optional):**
   - Go to "Network"
   - Ensure "Enable Network Adapter" is checked
   - Set "Attached to: NAT" (default)

## Step 5: Install Kali Linux

1. **Start the Virtual Machine**
   - Select your Kali Linux VM
   - Click "Start"

2. **Boot from ISO**
   - The VM will boot from the Kali Linux ISO
   - Select "Graphical Install" or "Install" from the boot menu

3. **Installation Process:**
   - **Language**: Select your preferred language (English recommended)
   - **Location**: Choose your country/region
   - **Keyboard**: Select your keyboard layout
   - **Network**: Configure hostname (default: kali)
   - **Users**: 
     - Set root password (make it strong)
     - Create a regular user account (recommended)
   - **Partitioning**:
     - Select "Guided - use entire disk"
     - Choose the virtual disk
     - Select "All files in one partition"
     - Confirm partitioning changes

4. **Package Installation**
   - Choose software to install:
     - **Desktop Environment**: XFCE (lightweight, recommended for VMs)
     - **Tools**: Default selection includes essential penetration testing tools
   - Wait for installation to complete (15-30 minutes)

5. **Boot Loader**
   - Install GRUB boot loader: Yes
   - Select the virtual disk for boot loader installation

6. **Complete Installation**
   - Remove installation media (VirtualBox does this automatically)
   - Restart the virtual machine

## Step 6: Post-Installation Setup

1. **First Boot**
   - Boot into Kali Linux
   - Log in with the credentials you created

2. **Install VirtualBox Guest Additions**
   ```bash
   sudo apt update
   sudo apt install -y dkms linux-headers-$(uname -r)
   ```
   - In VirtualBox menu: Devices > Insert Guest Additions CD image
   - Run the installer from the mounted CD
   - Reboot the VM

3. **Update System**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

4. **Take a Snapshot (Recommended)**
   - In VirtualBox: Machine > Take Snapshot
   - Name it "Fresh Installation"
   - This allows you to restore to a clean state

## Troubleshooting

### Common Issues:

**VM won't start or crashes:**
- Enable virtualization in BIOS/UEFI
- Increase allocated RAM
- Disable Hyper-V on Windows (if applicable)
- **Mac Users**: If VirtualBox fails on Apple Silicon Macs, switch to UTM

**VirtualBox incompatibility on Mac:**
- Apple Silicon Macs (M1/M2/M3) have limited VirtualBox support
- **Solution**: Use UTM (https://mac.getutm.app/) as a VirtualBox alternative
- UTM provides native ARM64 support and better performance on Apple Silicon

**Slow performance:**
- Increase RAM allocation
- Allocate more CPU cores
- Install VirtualBox Guest Additions
- Enable hardware acceleration

**Installation fails:**
- Verify ISO integrity
- Increase disk space allocation
- Try different installation method (text-based vs graphical)

**Network issues:**
- Check network adapter settings
- Try different network modes (NAT, Bridged, Host-only)

## Security Notes

- Use Kali Linux responsibly and only on networks/systems you own or have permission to test
- Keep the system updated regularly
- Consider using snapshots before making significant changes
- Be aware that Kali Linux contains powerful security tools that should be used ethically

## Useful Commands

```bash
# Update package lists
sudo apt update

# Upgrade installed packages
sudo apt upgrade

# Install new tools
sudo apt install [package-name]

# Check system information
uname -a
whoami
ip addr show
```

## Conclusion

You now have a fully functional Kali Linux virtual machine running in VirtualBox. This setup provides a safe, isolated environment for learning cybersecurity tools and techniques. Remember to use these tools responsibly and only on systems you own or have explicit permission to test.

For more advanced configurations and tool usage, refer to the official Kali Linux documentation at https://www.kali.org/docs/
