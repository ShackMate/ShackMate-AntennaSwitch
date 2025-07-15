# ShackMate Antenna Switch

**Remote Control System for RCS-8 and RCS-10 Antenna Switches**  
_Version 2.1 - Enhanced UI/UX and Modern Web Interface_

## 🎯 Overview

ShackMate Antenna Switch is a comprehensive ESP32-based remote control system designed to modernize RCS-8 and RCS-10 antenna switches. It combines full CI-V protocol compatibility with an intuitive web interface, providing both automated and manual antenna switching capabilities for amateur radio operators.

Built on the M5Stack AtomS3 platform, the system offers real-time control, persistent configuration storage, and seamless integration with the ShackMate ecosystem for complete station automation.

## ✨ Key Features

### 🔄 **Dual Switch Support**

- **RCS-8 Mode**: Direct GPIO control for 5 antennas (1-5)
- **RCS-10 Mode**: BCD-encoded control for 8 antennas (1-8)
- **Runtime Switching**: Change between modes via web interface without rebooting
- **Smart Button Management**: Automatically shows/hides antenna buttons based on selected mode

### 📡 **Advanced CI-V Integration**

- **Full Icom Compatibility**: Complete CI-V protocol implementation
- **Automatic Switching**: Radio-driven antenna selection based on band/frequency
- **Configurable Addressing**: Device numbers 1-4 (CI-V addresses 0xB4-0xB7)
- **Bi-directional Communication**: Real-time status updates and command acknowledgment
- **Multiple Radio Support**: Connect multiple radios through CI-V daisy chain

### 🎨 **Modern Web Interface**

- **Clean Design**: Streamlined switch control page with professional appearance
- **Real-time Updates**: Live WebSocket communication for instant status changes
- **Responsive Layout**: Mobile-friendly design that works on phones, tablets, and desktop
- **Visual Indicators**: RGB LED status and GPIO output indicators
- **Intuitive Controls**: Touch/click interface with visual feedback

### 🔧 **Advanced Antenna Management**

- **Persistent Details**: Each antenna stores comprehensive configuration:
  - **Type**: None, Wire, Directional, Satellite
  - **Style**: Beam, Yagi, Log-Periodic, Dipole, Loop, End Fed, etc.
  - **Polarization**: Vertical, Horizontal, Circular, Linear
  - **Manufacturer**: Chameleon, Comet, Cushcraft, Diamond, MFJ, SteppIR, etc.
  - **Band Pattern**: Visual LED pattern for quick band identification
  - **Disable State**: Temporarily disable antennas for maintenance
- **Auto-Save**: All changes automatically saved to ESP32 NVS storage
- **Multi-Client Sync**: Changes synchronized across all connected web browsers

### 🌐 **Network & Connectivity**

- **WiFi Setup**: Easy configuration via captive portal (WiFiManager)
- **WebSocket Communication**: Real-time bidirectional communication on port 4000
- **UDP Discovery**: Automatic ShackMate ecosystem integration on port 4210
- **mDNS Support**: Access via `shackmate-switch.local`
- **OTA Updates**: Over-the-air firmware updates for easy maintenance
- **Cache-Busting**: Prevents browser caching issues with automatic file versioning

### 📊 **Live System Monitoring**

- **Real-time Status**: Uptime, memory usage, CPU frequency, temperature
- **Connection Monitoring**: WebSocket status, CI-V communication health
- **GPIO Indicators**: Live status of all 5 GPIO outputs (G5, G6, G7, G8, G39)
- **Performance Metrics**: Free heap, PSRAM usage, flash memory status
- **Network Stats**: IP address, WiFi signal strength, connected clients

### 💾 **Robust Data Persistence**

- **NVS Storage**: Non-volatile storage for all configuration and antenna details
- **Automatic Backup**: Configuration automatically saved on every change
- **Factory Reset**: Easy restoration to default settings
- **Import/Export**: Configuration backup and restore capabilities

### 🔄 **Dual Switch Support**

- **RCS-8 Mode**: Direct GPIO control for 5 antennas (1-5)
- **RCS-10 Mode**: BCD-encoded control for 8 antennas (1-8)
- Runtime switchable between modes via web interface

### 📡 **CI-V Integration**

- Full Icom CI-V protocol compatibility
- Automatic antenna switching based on radio commands
- Configurable CI-V addresses (device numbers 1-4)
- Real-time bi-directional communication with transceivers

### 🌐 **Web Interface**

- Modern, responsive dashboard with live updates
- Real-time system monitoring (uptime, memory, connection status)
- Antenna configuration and naming
- Visual antenna switch control interface
- Mobile-friendly design

## �️ Web Interface

### 📊 **Dashboard** (`/`)

- **System Overview**: Complete device status at a glance
- **Network Information**: IP address, WebSocket connections, UDP discovery status
- **Hardware Metrics**: Chip ID, CPU frequency, flash memory, PSRAM usage
- **Live Performance**: Real-time uptime, free heap memory, temperature monitoring
- **CI-V Status**: Current baud rate, device address, communication health
- **Quick Configuration**: Switch model selection, device number, antenna naming
- **Auto-Refresh**: Live updates every minute via WebSocket

### 🎛️ **Switch Control** (`/switch`)

- **Visual Antenna Panel**: Interactive SVG-based antenna switch representation
- **Smart Button Layout**: Dynamic visibility based on RCS-8/RCS-10 mode selection
- **Real-time Selection**: Instant antenna switching with visual feedback
- **GPIO Status Panel**: Live indicators showing current output states (G5, G6, G7, G8, G39)
- **Antenna Details Panel**: Comprehensive antenna configuration interface:
  - **TYPE Button**: Short press cycles, long press opens dropdown menu
  - **STYLE Button**: Context-aware options based on selected type
  - **POL Button**: Polarization selection with type/style-specific options
  - **MFG Button**: Manufacturer selection from comprehensive database
  - **Band Pattern LEDs**: 16 clickable LEDs for custom band identification
  - **Disable Toggle**: Long-press antenna buttons to enable/disable
- **Selected Antenna Display**: Shows current antenna port and name
- **Touch/Mouse Support**: Optimized for both touch devices and desktop use

### ⚙️ **Configuration** (`/config`)

- **Advanced Settings**: Deep configuration options for power users
- **WiFi Management**: Network credential management and scanning
- **Factory Reset**: Complete restoration to default settings
- **Backup/Restore**: Configuration export and import capabilities

## 🔧 Hardware Requirements

### **Primary Platform**

- **M5Stack AtomS3** (ESP32-S3 based)
- **8MB Flash Memory** for firmware and web interface storage
- **Built-in RGB LED** for status indication
- **Physical Reset Button** for factory reset and WiFi clearing
- **USB-C Programming Port** for development and initial setup

### **GPIO Pin Assignments**

| GPIO Pin | RCS-8 Function | RCS-10 Function | Physical Location |
| -------- | -------------- | --------------- | ----------------- |
| **G5**   | Antenna 1      | BCD Bit A       | Grove Port        |
| **G6**   | Antenna 2      | BCD Bit B       | Grove Port        |
| **G7**   | Antenna 3      | BCD Bit C       | Grove Port        |
| **G8**   | Antenna 4      | _Unused_        | Grove Port        |
| **G39**  | Antenna 5      | _Unused_        | Grove Port        |

### **RGB LED Status Indicators**

- 🟢 **Green**: Normal operation, antenna control active
- 🔵 **Blue**: Connected to ShackMate server/dashboard
- 🟣 **Purple**: WiFi configuration mode (captive portal active)
- ⚪ **White (blinking)**: OTA firmware update in progress
- 🔴 **Red**: Error state or CI-V communication failure

### **Compatible Antenna Switches**

- **West Mountain Radio RCS-8**: 8 antennas with direct GPIO control
- **West Mountain Radio RCS-10**: 10 antennas with BCD-encoded control
- **Custom Switches**: Any switch accepting 5V logic levels on control inputs

## 🏗️ Software Architecture

### **Core Components**

#### **1. SMCIV Library** (`lib/SMCIV/`)

- Complete CI-V protocol implementation with error handling
- WebSocket client management for ShackMate dashboard integration
- Thread-safe antenna state management with callbacks
- GPIO abstraction layer for hardware control
- Automatic retry and connection recovery

#### **2. Web Server Stack** (AsyncWebServer)

- **HTTP Server**: Port 80 for web interface and API endpoints
- **WebSocket Server**: Port 4000 for real-time bidirectional communication
- **Static File Serving**: LittleFS-based with cache-busting headers
- **Template Engine**: Dynamic content generation with live data injection
- **RESTful API**: JSON-based configuration and control endpoints

#### **3. Network Services**

- **UDP Discovery**: Port 4210 for ShackMate ecosystem auto-discovery
- **WiFiManager**: Captive portal for initial WiFi configuration
- **mDNS Responder**: `shackmate-switch.local` for easy device access
- **OTA Updates**: Secure over-the-air firmware updates
- **Network Diagnostics**: Connection monitoring and auto-recovery

#### **4. Data Management**

- **NVS Storage**: Non-volatile storage for all configuration data
- **Preferences Library**: Organized data storage with automatic backup
- **JSON Serialization**: Efficient data exchange format
- **State Synchronization**: Multi-client real-time updates

#### **5. GPIO Control System**

- **Hardware Abstraction**: Mode-independent control interface
- **Smart Switching**: Automatic RCS-8/RCS-10 mode detection and switching
- **Real-time Updates**: Immediate GPIO state changes with confirmation
- **Safety Interlocks**: Prevention of invalid antenna combinations

### 1. Development Environment

```bash
# Install PlatformIO Core
pip install platformio

# Clone the repository
git clone <repository-url>
cd ShackMate-AntennaSwitch

# Build and upload
pio run -t upload
```

### 2. Initial Configuration

1. Power on the AtomS3 - it will create a WiFi hotspot named "shackmate-switch"
2. Connect to the hotspot and configure your WiFi credentials
3. Select your switch model (RCS-8 or RCS-10) and device number (1-4)
4. The device will reboot and connect to your network

### 3. Web Access

- Direct IP: `http://<device-ip>`
- mDNS: `http://shackmate-switch.local`
- Default WebSocket port: 4000

## Configuration

### Switch Models

- **RCS-8**: Supports 5 antennas with direct GPIO control
- **RCS-10**: Supports 8 antennas with BCD-encoded control

### Device Numbers

- Range: 1-4
- Determines CI-V address: (0xB4 - 0xB7) by the device_number.
- Example: Device #1 = CI-V address 0xB4

### Antenna Names

- Customizable names for each antenna port
- Stored in non-volatile memory
- Auto-saved via web interface

## 📡 API Reference

### **WebSocket Messages** (Port 4000)

#### **📥 Incoming Messages (Client → Server)**

##### **Antenna Selection**

```json
{
  "type": "antennaChange",
  "currentAntennaIndex": 2
}
```

##### **Complete State Update**

```json
{
  "type": "stateUpdate",
  "currentAntennaIndex": 2,
  "antennaNames": [
    "20m Beam",
    "40m Dipole",
    "80m Loop",
    "Vertical",
    "Spare",
    "Spare",
    "Spare",
    "Spare"
  ],
  "antennaState": [
    {
      "typeIndex": 2,
      "styleIndex": 2,
      "polIndex": 1,
      "mfgIndex": 4,
      "bandPattern": 2046,
      "disabled": false
    }
  ],
  "rcsType": 1,
  "deviceNumber": 1
}
```

##### **Request Fresh State**

```json
{
  "type": "requestState"
}
```

#### **📤 Outgoing Messages (Server → Client)**

##### **State Broadcast**

```json
{
  "type": "stateUpdate",
  "currentAntennaIndex": 2,
  "antennaNames": [
    "20m Beam",
    "40m Dipole",
    "80m Loop",
    "Vertical",
    "Spare",
    "Spare",
    "Spare",
    "Spare"
  ],
  "antennaState": [
    {
      "typeIndex": 2,
      "styleIndex": 2,
      "polIndex": 1,
      "mfgIndex": 4,
      "bandPattern": 2046,
      "disabled": false
    }
  ],
  "rcsType": 1,
  "deviceNumber": 1,
  "gpioStatus": [true, false, false, false, false],
  "source": "web|ci-v"
}
```

##### **Dashboard Status Updates**

```json
{
  "type": "dashboardStatus",
  "wsServer": "192.168.1.100:4000",
  "wsStatus": "Connected",
  "civAddress": "0xB4"
}
```

##### **Live System Updates**

```json
{
  "type": "uptimeUpdate",
  "uptime": "2 Days 15 Hours 30 Minutes",
  "freeHeap": "245760"
}
```

### **HTTP API Endpoints**

#### **📄 Page Routes**

- `GET /` → Main dashboard with system overview
- `GET /switch` → Interactive antenna control interface
- `GET /config` → Advanced configuration page

#### **⚙️ Configuration API**

- `POST /saveConfig` → Save configuration changes
- `GET /scan` → WiFi network scanning
- `POST /restore` → Factory reset and restore defaults

#### **📁 Static Assets**

- `GET /antenna.css` → Stylesheets (with cache-busting)
- `GET /antenna.js` → JavaScript (with cache-busting)
- `GET /favicon.ico` → Site icon

### **Antenna Detail Configuration**

#### **Type Categories**

- **0 - None**: No antenna connected
- **1 - Wire**: Dipoles, End Fed, Random Wire, Quarter-Wave, Loop, Magnetic Loop
- **2 - Directional**: Beam, Yagi, Log-Periodic, Dish, Omni
- **3 - Satellite**: Beam, Yagi, Helical with circular/linear polarization

#### **Manufacturer Database**

Chameleon, Comet, Cushcraft, Diamond, GreyLine, HomeBrew, Hustler, M2, MFJ, SteppIR, SolarCON

#### **Band Pattern LEDs**

16-bit pattern for visual band identification:

- Bits 0-15: Individual band indicators
- Clickable in web interface for custom patterns
- Automatically saved to NVS storage

## 🚀 Installation & Setup

### **📋 Prerequisites**

- PlatformIO Core or PlatformIO IDE
- Git for repository cloning
- M5Stack AtomS3 hardware
- USB-C cable for initial programming

### **🔧 Development Environment Setup**

```bash
# Install PlatformIO Core (if not using IDE)
pip install platformio

# Clone the repository
git clone https://github.com/ShackMate/ShackMate-AntennaSwitch.git
cd ShackMate-AntennaSwitch

# Build the firmware
pio run

# Upload firmware and filesystem
pio run -t upload
pio run -t uploadfs
```

### **📶 Initial Device Configuration**

#### **Step 1: First Boot WiFi Setup**

1. Power on the AtomS3 → **Purple LED** indicates configuration mode
2. Connect to WiFi hotspot: `shackmate-switch-XXXXXX`
3. Captive portal opens automatically (or navigate to `192.168.4.1`)
4. Select your WiFi network and enter credentials
5. Device reboots and connects → **Green LED** indicates normal operation

#### **Step 2: Web Interface Access**

- **Direct IP**: `http://<device-ip>` (check router DHCP or serial monitor)
- **mDNS**: `http://shackmate-switch.local` (recommended)
- **WebSocket**: `ws://<device-ip>:4000/ws` for real-time communication

#### **Step 3: Basic Configuration**

1. Open the web interface and navigate to the **Dashboard**
2. Configure your **Switch Model** (RCS-8 or RCS-10)
3. Set your **Device Number** (1-4 for CI-V addressing)
4. Customize **Antenna Names** for each port
5. Settings auto-save to non-volatile storage

### **⚡ Over-The-Air (OTA) Updates**

#### **Setup OTA Environment**

```bash
# Configure OTA target in platformio.ini
# Update upload_port with your device IP
pio run -e m5stack-atoms3-ota -t upload
```

#### **OTA Update Process**

- **White blinking LED** during upload
- **Green LED** when complete
- **Red LED** if update fails
- Web interface temporarily unavailable during update

### **🔄 Factory Reset Options**

#### **Hardware Reset**

- Hold reset button for **5+ seconds** → Clears WiFi credentials only
- Hold reset button for **10+ seconds** → Complete factory reset

#### **Web Interface Reset**

- Navigate to `/config` page
- Click **"Factory Reset"** button
- Confirm reset action
- Device reboots to default configuration

## 📻 CI-V Protocol Integration

### **🔧 Configuration**

#### **Device Addressing**

- **Base Address**: `0xB3` (ShackMate family base)
- **Device-Specific**: `0xB3 + device_number`
- **Address Range**: `0xB4` - `0xB7` (devices 1-4)
- **Example**: Device #1 = CI-V address `0xB4`

#### **Communication Settings**

- **Default Baud Rate**: 19,200 bps
- **Data Format**: 8N1 (8 data bits, no parity, 1 stop bit)
- **Connection**: Daisy-chain compatible with other CI-V devices
- **Auto-Detection**: Automatically detects radio presence and capabilities

### **📡 Supported Commands**

#### **Antenna Selection Commands**

- **From Radio**: Automatic antenna switching based on band/frequency changes
- **To Radio**: Antenna status confirmation and acknowledgment
- **Manual Override**: Web interface commands override radio commands temporarily

#### **Status Queries**

- **Current Antenna**: Radio can query active antenna selection
- **Switch Capabilities**: Reports available antenna ports based on RCS mode
- **Health Check**: Periodic communication to verify connection integrity

#### **Bidirectional Features**

- **Real-time Updates**: Immediate notification of antenna changes
- **Error Reporting**: Communication failures reported to web interface
- **Automatic Retry**: Failed commands automatically retried with backoff
- **Multi-Radio Support**: Handle multiple radios on same CI-V bus

### **🔗 Integration Examples**

#### **With Icom Radios**

```
Radio (0x94) ←→ ShackMate Switch (0xB4) ←→ Other CI-V Devices
```

#### **Multi-Device Chain**

```
Radio ←→ ShackMate #1 (0xB4) ←→ ShackMate #2 (0xB5) ←→ Amplifier
```

### **� CI-V Command Summary**

#### **Standard CI-V Message Format**

```
FE FE [TO] [FROM] [CMD] [SUB] [DATA...] FD
```

#### **ShackMate Switch Commands**

| Command    | Function               | Data Format | Example                            |
| ---------- | ---------------------- | ----------- | ---------------------------------- |
| **19 00**  | Request Device Address | None        | `FE FE B4 E0 19 00 FD`             |
| **19 01**  | Request IP Address     | None        | `FE FE B4 E0 19 01 FD`             |
| **30 00**  | Query Switch Model     | None        | `FE FE B4 E0 30 00 FD`             |
| **30 01**  | Set Switch Model       | `[MODE]`    | `FE FE B4 E0 30 01 00 FD` (RCS-8)  |
| **31 00**  | Query Current Antenna  | None        | `FE FE B4 E0 31 00 FD`             |
| **31 [N]** | Select Antenna         | `[ANTENNA]` | `FE FE B4 E0 31 03 FD` (Antenna 3) |

#### **Response Messages**

| Response   | Meaning           | Data Format            | Example                            |
| ---------- | ----------------- | ---------------------- | ---------------------------------- |
| **19 00**  | Device Address    | `[ADDRESS]`            | `FE FE E0 B4 19 00 B4 FD`          |
| **19 01**  | IP Address        | `[IP1][IP2][IP3][IP4]` | `FE FE E0 B4 19 01 C0 A8 01 64 FD` |
| **30 [M]** | Switch Model      | `[MODE]`               | `FE FE E0 B4 30 00 FD` (RCS-8)     |
| **31 [N]** | Antenna Selection | `[ANTENNA]`            | `FE FE E0 B4 31 03 FD` (Antenna 3) |

#### **Antenna Selection Values**

- **RCS-8 Mode**: `01`-`05` (Antennas 1-5)
- **RCS-10 Mode**: `01`-`08` (Antennas 1-8)
- **Invalid Selection**: No response (command ignored)

#### **Switch Mode Values**

- **00**: RCS-8 Mode (Direct GPIO, 5 antennas)
- **01**: RCS-10 Mode (BCD encoded, 8 antennas)

#### **Device Address Examples**

```
Device #1: 0xB4    FE FE B4 E0 31 03 FD
Device #2: 0xB5    FE FE B5 E0 31 03 FD
Device #3: 0xB6    FE FE B6 E0 31 03 FD
Device #4: 0xB7    FE FE B7 E0 31 03 FD
```

#### **Common CI-V Sequences**

##### **Device Discovery**

```
Radio → Switch:  FE FE B4 E0 19 00 FD     (Request Address)
Switch → Radio:  FE FE E0 B4 19 00 B4 FD  (Address 0xB4)
Radio → Switch:  FE FE B4 E0 19 01 FD     (Request IP)
Switch → Radio:  FE FE E0 B4 19 01 C0 A8 01 64 FD  (192.168.1.100)
```

##### **Antenna Selection**

```
Radio → Switch:  FE FE B4 E0 31 03 FD     (Select Antenna 3)
Switch → Radio:  FE FE E0 B4 31 03 FD     (Antenna 3 Selected)
```

##### **Query Current Antenna**

```
Radio → Switch:  FE FE B4 E0 31 00 FD     (Query Current)
Switch → Radio:  FE FE E0 B4 31 02 FD     (Antenna 2 Active)
```

##### **Switch Model Configuration**

```
Radio → Switch:  FE FE B4 E0 30 00 FD     (Query Model)
Switch → Radio:  FE FE E0 B4 30 00 FD     (RCS-8 Mode)
Radio → Switch:  FE FE B4 E0 30 01 01 FD  (Set RCS-10 Mode)
Switch → Radio:  FE FE E0 B4 30 01 FD     (RCS-10 Mode Set)
```

#### **Error Conditions**

- **Invalid Antenna**: Command ignored (no response)
- **Invalid Mode**: Command ignored (no response)
- **Communication Timeout**: No response after 500ms
- **Address Conflict**: Multiple devices may respond

#### **Integration Notes**

- **Command Echo**: All valid commands echoed back as confirmation
- **Manual Override**: Web interface commands take precedence over CI-V
- **State Synchronization**: All antenna changes broadcast to web clients
- **IP Discovery**: Enables ShackMate dashboard auto-discovery via CI-V

### **�🛠️ Troubleshooting CI-V**

#### **Common Issues**

1. **No CI-V Communication**

   - Verify wiring (TIP/RING connections)
   - Check baud rate settings (default 19,200)
   - Ensure device address is unique on bus

2. **Intermittent Switching**

   - Check CI-V bus voltage levels
   - Verify proper termination
   - Monitor for electrical interference

3. **Address Conflicts**
   - Change device number in web interface
   - Verify no other devices using same address
   - Use CI-V bus scanner to detect conflicts

## 🔍 Troubleshooting

### **🌐 Network & Connectivity Issues**

#### **WiFi Connection Problems**

```bash
# Symptoms: Purple LED, can't access web interface
Solutions:
• Hold reset button 5+ seconds to clear WiFi credentials
• Device creates hotspot: "shackmate-switch-XXXXXX"
• Check router DHCP for assigned IP address
• Try mDNS: shackmate-switch.local
```

#### **Web Interface Not Loading**

```bash
# Symptoms: Browser timeout, connection refused
Diagnostic Steps:
1. Check device IP via serial monitor (115200 baud)
2. Verify device on same network subnet
3. Try direct IP instead of mDNS
4. Check browser cache - hard refresh (Ctrl+F5)
5. Verify WebSocket port 4000 not blocked by firewall
```

#### **WebSocket Connection Issues**

```bash
# Symptoms: Interface loads but no real-time updates
Solutions:
• Check browser developer console for errors
• Verify port 4000 accessibility
• Clear browser cache and reload
• Check network proxy/firewall settings
```

### **🔧 Hardware & GPIO Issues**

#### **Antenna Not Switching**

```bash
# Symptoms: Web interface works but no physical switching
Diagnostic Steps:
1. Verify GPIO connections to antenna switch
2. Check switch model configuration (RCS-8 vs RCS-10)
3. Monitor GPIO status indicators in web interface
4. Use multimeter to verify 5V output on control pins
5. Check antenna switch power supply
```

#### **Incorrect Antenna Selection**

```bash
# Symptoms: Wrong antenna activated
Solutions:
• Verify switch mode (RCS-8 vs RCS-10) matches hardware
• Check GPIO pin assignments in hardware section
• Test with known working antenna ports
• Verify BCD encoding for RCS-10 mode
```

#### **GPIO Status Indicators Not Working**

```bash
# Symptoms: No status LEDs in web interface
Solutions:
• Hard refresh browser (Ctrl+F5) to clear cache
• Check JavaScript console for errors
• Verify firmware version 2.1 or later
• Restart device to reload interface
```

### **📻 CI-V Communication Issues**

#### **No Radio Communication**

```bash
# Symptoms: Antenna switching works manually but not from radio
Diagnostic Steps:
1. Verify CI-V cable wiring (TIP/RING connections)
2. Check baud rate settings (default 19,200)
3. Ensure unique CI-V address (0xB4-0xB7)
4. Test with known working CI-V device
5. Monitor serial output for CI-V message traffic
```

#### **Intermittent CI-V Operation**

```bash
# Symptoms: Sometimes works, sometimes doesn't
Solutions:
• Check CI-V bus termination
• Verify power supply stability
• Look for electrical interference sources
• Ensure proper cable shielding
• Check for address conflicts on CI-V bus
```

### **💾 Configuration & Data Issues**

#### **Settings Not Saving**

```bash
# Symptoms: Configuration reverts after reboot
Solutions:
• Check NVS storage health via serial monitor
• Perform factory reset and reconfigure
• Verify sufficient flash memory available
• Update to latest firmware version
```

#### **Antenna Details Lost**

```bash
# Symptoms: TYPE/STYLE/POL/MFG settings reset
Solutions:
• Ensure firmware 2.1+ with enhanced persistence
• Check WebSocket connection during configuration
• Save settings incrementally, not all at once
• Monitor serial console for NVS write errors
```

### **⚡ Performance Issues**

#### **Slow Web Interface**

```bash
# Symptoms: Sluggish response, timeouts
Solutions:
• Check available heap memory in dashboard
• Restart device if memory low
• Reduce number of connected web clients
• Update firmware for performance improvements
```

#### **Frequent Disconnections**

```bash
# Symptoms: WebSocket keeps reconnecting
Solutions:
• Check WiFi signal strength
• Verify router stability and settings
• Reduce broadcast intervals in code
• Use 2.4GHz band if 5GHz unstable
```

### **🛠️ Diagnostic Tools**

#### **Serial Monitor Commands**

```bash
# Connect at 115200 baud to see:
• GPIO state changes
• WebSocket connection events
• CI-V message traffic
• Memory usage statistics
• Error messages and stack traces
```

#### **Browser Developer Tools**

```bash
# Press F12 and check:
• Console: JavaScript errors and WebSocket messages
• Network: Failed HTTP requests and file loading
• Application: Local storage and cached files
• Sources: Verify antenna.js version 2.1+
```

### **🔄 Recovery Procedures**

#### **Complete Reset**

```bash
1. Hold reset button 10+ seconds (complete factory reset)
2. Wait for purple LED (configuration mode)
3. Reconfigure WiFi via captive portal
4. Access web interface and reconfigure settings
```

#### **Firmware Recovery**

```bash
1. Connect via USB-C cable
2. Use PlatformIO to upload fresh firmware
3. Upload filesystem: pio run -t uploadfs
4. Perform factory reset via web interface
```

## 👨‍💻 Development

### **🏗️ Building from Source**

#### **Environment Setup**

```bash
# Install PlatformIO Core
pip install platformio

# Clone repository
git clone https://github.com/ShackMate/ShackMate-AntennaSwitch.git
cd ShackMate-AntennaSwitch

# Install dependencies (automatic)
pio lib install
```

#### **Build Targets**

```bash
# Debug build (USB upload)
pio run -e m5stack-atoms3

# Release build with OTA
pio run -e m5stack-atoms3-ota

# Upload firmware
pio run -t upload

# Upload filesystem (web interface files)
pio run -t uploadfs

# Monitor serial output
pio device monitor
```

### **📚 Dependencies**

#### **Core Libraries**

- **ESP32 Arduino Framework**: Base platform framework
- **WiFiManager**: Captive portal for WiFi configuration
- **AsyncTCP/ESPAsyncWebServer**: High-performance web server
- **ArduinoJson**: JSON serialization and parsing
- **WebSockets**: Real-time bidirectional communication
- **Adafruit NeoPixel**: RGB LED control
- **Preferences**: NVS storage abstraction

#### **Custom Libraries**

- **SMCIV** (`lib/SMCIV/`): CI-V protocol implementation and WebSocket management

### **📁 Project Structure**

```
ShackMate-AntennaSwitch/
├── src/
│   └── main.cpp                 # Main application code (1600+ lines)
├── lib/
│   └── SMCIV/                  # CI-V protocol library
│       ├── SMCIV.cpp           # Implementation
│       └── SMCIV.h             # Header definitions
├── data/                       # Web interface files (LittleFS)
│   ├── index.html              # Dashboard page
│   ├── switch.html             # Antenna control interface
│   ├── config.html             # Configuration page
│   ├── antenna.css             # Styling and responsive design
│   ├── antenna.js              # Client-side JavaScript (v2.1)
│   └── favicon.ico             # Site icon
├── include/                    # Additional headers
├── platformio.ini              # Build configuration
├── GPIO_ANTENNA_CONTROL.md     # Hardware documentation
└── README.md                   # This file
```

### **🔧 Configuration Files**

#### **platformio.ini** - Build Configuration

```ini
[env:m5stack-atoms3]
platform = espressif32
board = m5stack-atoms3
framework = arduino
board_build.filesystem = littlefs
board_build.partitions = default_8MB.csv
build_flags = -DARDUINO_USB_CDC_ON_BOOT=1

[env:m5stack-atoms3-ota]
upload_protocol = espota
upload_port = <device-ip>
```

### **🧪 Testing**

#### **Manual Testing Checklist**

- [ ] WiFi configuration via captive portal
- [ ] Web interface loads on multiple browsers
- [ ] Real-time WebSocket communication
- [ ] Antenna switching (manual and CI-V)
- [ ] Configuration persistence across reboots
- [ ] OTA updates work correctly
- [ ] GPIO status indicators update in real-time
- [ ] Antenna details save/load correctly

#### **Browser Compatibility**

- ✅ Chrome/Chromium (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ✅ Mobile browsers (iOS/Android)

### **🐛 Contributing**

#### **Bug Reports**

Please include:

- Firmware version number
- Hardware model (M5Stack AtomS3)
- Browser type and version
- Network configuration details
- Serial monitor output (if applicable)
- Steps to reproduce the issue

#### **Feature Requests**

- Describe the use case and benefit
- Consider backward compatibility
- Provide implementation suggestions if possible

## 📋 Version History

### **Version 2.1** (Current)

- ✅ **Complete tuner button removal** - Eliminated all tuner-related code
- ✅ **Enhanced GPIO indicators** - Real-time status with comprehensive debugging
- ✅ **Improved antenna persistence** - Robust NVS storage with detailed logging
- ✅ **Cache-busting implementation** - Prevents browser caching issues
- ✅ **Advanced antenna details** - Full TYPE/STYLE/POL/MFG configuration
- ✅ **WebSocket enhancements** - Better error handling and state synchronization
- ✅ **UI/UX improvements** - Cleaner interface with better visual feedback

### **Version 2.0.1**

- ✅ **Dual switch support** - RCS-8 and RCS-10 compatibility
- ✅ **CI-V integration** - Full Icom protocol compatibility
- ✅ **Modern web interface** - Responsive design with real-time updates
- ✅ **NVS persistence** - Reliable configuration storage
- ✅ **OTA updates** - Over-the-air firmware updates
- ✅ **UDP discovery** - ShackMate ecosystem integration

### **Planned Features**

- 🔄 **Advanced CI-V routing** - Multi-radio support with routing tables
- 🔄 **Band-based switching** - Automatic antenna selection by frequency
- 🔄 **Remote logging** - Cloud-based operation logging
- 🔄 **Mobile app** - Native iOS/Android companion app
- 🔄 **Voice control** - Integration with voice assistants

## 📄 License

This project is developed by **Half Baked Circuits** and is part of the **ShackMate Ecosystem** for comprehensive amateur radio station automation.

### Usage Terms

- ✅ **Amateur Radio Use**: Free for all amateur radio operators and enthusiasts
- ✅ **Educational Use**: Encouraged for learning and experimentation
- ✅ **Modification**: Source code available for customization and improvement
- ✅ **Redistribution**: Share with proper attribution to original authors

## 🤝 Support & Community

### **📞 Technical Support**

- **GitHub Issues**: Report bugs and request features
- **Documentation**: Comprehensive guides and API reference
- **Serial Debugging**: Detailed diagnostic information available
- **Community Forum**: Connect with other ShackMate users

### **🔗 Related Projects**

- **ShackMate Dashboard**: Central control for multiple devices
- **ShackMate Rotator Control**: Antenna rotator automation
- **ShackMate Power Management**: Station power sequencing and control

### **📈 Roadmap**

- **Q3 2025**: Band-based automatic switching
- **Q4 2025**: Mobile companion app
- **Q1 2026**: Voice control integration
- **Q2 2026**: Multi-site remote operation

---

## 🎯 Quick Start Summary

1. **📦 Hardware**: M5Stack AtomS3 + GPIO connections to RCS-8/RCS-10
2. **⚡ Setup**: Upload firmware, configure WiFi via captive portal
3. **🌐 Access**: Open `http://shackmate-switch.local` in web browser
4. **⚙️ Configure**: Select switch model, set device number, name antennas
5. **📡 Connect**: Wire CI-V for radio integration (optional)
6. **🎛️ Control**: Use web interface or CI-V commands for antenna switching

**🎉 Result**: Professional antenna switching with modern web control, persistent configuration, and seamless CI-V integration!

---

<div align="center">

**ShackMate Antenna Switch v2.1**  
_Bringing Modern Connectivity to Classic Antenna Switching Systems_

🔗 **[GitHub Repository](https://github.com/ShackMate/ShackMate-AntennaSwitch)** | 📧 **[Support](mailto:support@shackmate.com)** | 🌐 **[ShackMate Ecosystem](https://shackmate.com)**

_Built with ❤️ by Amateur Radio Operators, for Amateur Radio Operators_

</div>
