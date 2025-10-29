# ProxyCloud GUI

[![GitHub issues](https://img.shields.io/github/issues/code3-dev/ProxyCloud-GUI)](https://github.com/code3-dev/ProxyCloud-GUI/issues)
[![License](https://img.shields.io/github/license/code3-dev/ProxyCloud-GUI)](LICENSE)

[فارسی (Persian)](FA.md) | [Русский (Russian)](RU.md)

![ProxyCloud GUI Home Screen](config/screenshots/home.jpg)

ProxyCloud GUI is a free, fast, and user-friendly desktop application for managing proxy connections across multiple platforms. With its sleek, modern interface and powerful features, it provides a seamless experience for users who need reliable and secure proxy connections.

## Features

### Core Features
- Cross-platform support (Windows, macOS, Linux)
- Beautiful, intuitive graphical interface with multiple theme options
- Multiple proxy protocol support (VLESS, VMess, SS (Shadowsocks), Trojan, Warp, WARP-Plus, WireGuard)
- Country-based proxy selection with flag icons
- System tray integration for quick access
- Auto-connect option on startup

### Advanced Features
- **TUN Mode**: Full VPN tunneling for system-wide proxy routing
- **DNS Settings**: Configurable remote and direct DNS options
- **Bypass Options**: LAN bypass and selective routing capabilities
- **Fragment Technology**: TLS fragmentation with customizable size and timing
- **Mux (Multiplexing)**: Connection multiplexing with padding and protocol options
- **ISP-Specific Optimizations**: Tailored settings for different internet service providers
- **Multiple Themes**: Choose from various visual themes including Dark, Light, Zen, Ahura, Warp, NeoFlux, Neon, and more

## Installation

### Windows

- Download the latest Windows installer or portable version from the [Releases](https://github.com/code3-dev/ProxyCloud-GUI/releases) page
- Run the installer or run the portable version
- If Windows shows "Windows protected your PC" message when installing:
  1. Click on "More info"
  
  ![More info button](config/screenshots/more.png)
  
  2. Then click on "Run anyway"
  
  ![Run anyway button](config/screenshots/run-anyway.png)
- Launch the application
- The application will automatically configure necessary components including TUN drivers

#### Important Notes for Windows Portable Version

- Always run as Administrator
- The Portable version doesn't require installation
- The Portable file works on all Windows versions
- If Windows shows "Windows protected your PC" message when installing or running the application:
  1. Click on "More info"
  
  ![More info button](config/screenshots/more.png)
  
  2. Then click on "Run anyway"
  
  ![Run anyway button](config/screenshots/run-anyway.png)

### macOS

- Download the latest macOS DMG or ZIP from the [Releases](https://github.com/code3-dev/ProxyCloud-GUI/releases) page
- Open the DMG and drag the application to your Applications folder or extract the ZIP
- Launch the application
- You may need to grant additional permissions for TUN mode functionality

> **Note for macOS Users**: Apple could not verify "ProxyCloud GUI" is free of malware that may harm your Mac or compromise your privacy. You can also use these commands to make it open:
> ```
> sudo spctl --master-disable
> xattr -cr /Applications/ProxyCloud\ GUI.app
> ```

This error usually happens when macOS blocks osascript or when the app does not have the required permissions to control System Proxy or Network settings.

Below are the steps you can follow to fix the issue:

**1. Grant Automation Permissions**
- Open System Settings (or System Preferences on older macOS)
- Go to Privacy & Security → Automation
- Look for ProxyCloud GUI in the list
- Enable permissions for System Events or osascript

**2. Grant Full Disk & Accessibility Access**
- Open System Settings → Privacy & Security
- Select Accessibility → click + → add ProxyCloud GUI
- Go back and open Full Disk Access → add ProxyCloud GUI
- This ensures the app can run scripts and manage proxy settings

**3. Reset Automation Permissions (if needed)**
If permissions are broken, you can reset them manually.

Run this command in Terminal:

```bash
tccutil reset AppleEvents
```

Then restart ProxyCloud GUI and macOS will ask again for permissions.

**4. Manual Proxy / TUN Mode Setup**
If the automatic setup does not work, you can configure manually:

**Proxy Mode**
```bash
networksetup -setwebproxy "Wi-Fi" 127.0.0.1 8086
networksetup -setsecurewebproxy "Wi-Fi" 127.0.0.1 8086
```

To turn off:
```bash
networksetup -setwebproxystate "Wi-Fi" off
networksetup -setsecurewebproxystate "Wi-Fi" off
```

**TUN Mode**
Make sure you grant System Extension / VPN permission to the app. If blocked, open:

System Settings → Privacy & Security → Allow system extension for ProxyCloud GUI.

**5. Restart & Test**
- Close ProxyCloud GUI completely
- Reopen the app
- Select System Proxy or TUN Mode
- Test your connection

If the problem continues, please send us logs or screenshots so we can help further.

### Linux

- Download the latest Linux package (DEB, RPM, AppImage, or tar.gz) from the [Releases](https://github.com/code3-dev/ProxyCloud-GUI/releases) page
- Install the package using your package manager or extract the archive
- Launch the application
- For TUN mode, you may need to run with elevated privileges or configure the necessary permissions

#### Running in TUN Mode (Linux)

To enable TUN mode in Linux, you need to provide root access to ProxyCloud. Execute the following commands one by one:

**First Command:**
```bash
xhost +SI:localuser:root
```
This command allows the root user to access your display, enabling it to run the graphical interface of the application.

**Second Command:**
```bash
sudo -E proxycloud-gui --no-sandbox
```
This command runs ProxyCloud with root privileges. The `-E` parameter preserves environment variables, and the `--no-sandbox` parameter disables the sandbox, which is necessary for full system access in TUN mode.

**Third Command:**
```bash
xhost -SI:localuser:root
```
After you finish using the application, run this command to revoke root access to your display. This step is essential for maintaining your system's security.

#### Arch Linux

ProxyCloud is now on the [AUR](https://aur.archlinux.org/packages/proxycloud-gui-bin), therefore you can install it using your preferred AUR helper.

```bash
paru -S proxycloud-gui-bin

# or if you are using yay

yay -S proxycloud-gui-bin
```

## User Interface

ProxyCloud GUI features a stunning, modern interface with multiple theme options to suit your preferences:

- **Dark Mode**: Sleek dark theme for reduced eye strain
- **Light Mode**: Clean, bright interface
- **Zen Mode**: Minimalist design for distraction-free usage
- **Ahura Mode**: Elegant theme with distinctive styling
- **Warp Mode**: Inspired by Cloudflare Warp's design language
- **NeoFlux Mode**: Modern, futuristic interface
- **Neon Mode**: Vibrant, high-contrast theme
- **CIA Mode**: Professional, security-focused design
- **Ocean Deep**: Calming blue tones
- **Forest Green**: Nature-inspired green theme
- **Sunset Glow**: Warm, sunset-colored interface
- **Midnight Silver**: Sophisticated dark theme with silver accents
- **Cosmic Dust**: Space-inspired design
- **Volcanic Ash**: Dark theme with fiery accents

## Usage Guide

### Quick Start

1. Launch ProxyCloud GUI
2. Import your proxy configuration or add a WARP configuration
3. Select your preferred server from the country list
4. Click the power button to connect
5. Monitor your connection status in the main interface

### Advanced Usage

- **TUN Mode**: Enable VPN mode in settings for system-wide proxy routing
- **Fragment Settings**: Configure TLS fragmentation for improved connection reliability
- **Mux Configuration**: Optimize connection multiplexing for better performance
- **Regional Optimization**: Select your region and ISP for tailored connection settings

## Development

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or later recommended)
- npm or yarn
- Electron knowledge for UI modifications

### Setup

```bash
# Clone the repository
git clone https://github.com/code3-dev/ProxyCloud-GUI.git
cd ProxyCloud-GUI

# Install dependencies
npm install

# Start the application
npm start
```

### Building

```bash
# Build for Windows
npm run build:win

# Build for Linux
npm run build:linux

# Build for macOS
npm run build:mac

# Build for all platforms
npm run build
```

### UI Customization

The application's UI is built with HTML, CSS, and JavaScript. To customize the UI:

1. Modify files in the `src/main` directory for the main interface
2. Edit theme files in the appropriate CSS files
3. Update component behavior in the JavaScript files

## Configuration

### Basic Configuration

Configuration files are stored in the `config/` directory. You can modify these files to customize your proxy settings or use the intuitive GUI interface to configure all options.

### Advanced Configuration Options

#### VPN Settings

- **VPN Core**: Choose between ProxyCloud or Warp cores based on your needs
- **VPN Type**: Select between System Proxy or TUN mode (full VPN tunneling)
- **Bind Address**: Configure the local address for the proxy service

#### DNS Configuration

- **Remote DNS**: Set custom DNS servers for encrypted remote connections
- **Direct DNS**: Configure DNS servers for direct connections

#### Security Features

- **Bypass LAN**: Allow local network traffic to bypass the proxy
- **Block Ads**: Enable built-in ad blocking functionality
- **TLS Fragment**: Configure fragmentation to bypass deep packet inspection
  - Fragment Size: Customize the size of TLS fragments
  - Fragment Sleep: Set timing between fragments
  - Mixed SNI Case: Enable SNI case randomization
  - TLS Padding: Add padding to TLS packets

#### Connection Optimization

- **Mux (Multiplexing)**: Optimize connection handling
  - Enable/disable multiplexing
  - Configure padding for additional obfuscation
  - Set maximum streams and protocol

#### Regional Settings

- **Region Selection**: Optimize for specific regions (Iran, China, Russia, etc.)
- **ISP-Specific Settings**: Tailored configurations for different ISPs

## License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.

## Bug Reports and Feature Requests

Please use the [GitHub issue tracker](https://github.com/code3-dev/ProxyCloud-GUI/issues) to report bugs or request features.

## Community and Support

- Join our community discussions
- Get help with configuration and troubleshooting
- Share your experience and contribute to the project's development

## Security and Privacy

ProxyCloud GUI is designed with security and privacy in mind:

- No logging of user activity
- Open-source code for transparency
- Regular security updates
- Advanced obfuscation techniques (TLS fragmentation, multiplexing)