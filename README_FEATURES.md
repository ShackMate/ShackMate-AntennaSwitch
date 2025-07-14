# ShackMate Antenna Switch: Features & Functions

## Features

- **Dual Antenna Switch Support**: RCS-8 (5 ports, direct GPIO) and RCS-10 (8 ports, BCD-encoded)
- **Dynamic Mode Switching**: Change between RCS-8 and RCS-10 at runtime via web UI
- **Web Interface**: Modern, mobile-friendly dashboard, live status, and visual antenna control
- **Real-Time Sync**: WebSocket-based updates for all clients and dashboard pages
- **Antenna Details Persistence**: Type, style, polarization, manufacturer, band pattern, and disabled state are stored in ESP32 NVS and synchronized across all clients
- **Custom Antenna Names**: Editable, persistent, and synchronized
- **OTA Updates**: Firmware and filesystem updates via web
- **WiFiManager**: Easy initial setup and recovery
- **mDNS & UDP Discovery**: Easy device finding and integration
- **RGB LED Status**: Visual feedback for operation, config, and OTA
- **CI-V Protocol Support**: Full Icom CI-V compatibility, including:
  - Address query (19 00)
  - IP query (19 01)
  - Antenna selection (31)
  - RCS type read/set (30)
  - Proper handling of broadcast and direct addressing
- **WebSocket CI-V Bridge**: For remote CI-V control and monitoring
- **Robust State Handling**: Handles browser reloads, tab focus, and network reconnects
- **Debug & Diagnostics**: Serial output, manual state refresh, and reset functions

## Functions

### Web UI Functions

- Visual antenna selection and status
- Antenna details editing (type, style, pol, mfg, band pattern)
- Model/device number selection (config page)
- Real-time dashboard and switch page sync
- Manual and automatic state refresh
- Factory reset and WiFi reconfiguration

### CI-V Protocol Functions

- Responds to 19 00 (address query) for both broadcast and direct
- Responds to 19 01 (IP query)
- Handles antenna selection (31) and RCS type (30) commands
- Broadcasts antenna state changes to all clients
- Device number sets CI-V address (0xB4-0xB7)

### Persistence & Sync

- All antenna and config data stored in ESP32 NVS
- No localStorage; all sync is server-based
- All changes are broadcast to all connected web clients

### Hardware Functions

- GPIO/BCD output for antenna switching
- Callback system for custom hardware integration
- RGB LED status indication

---

For more details, see the main README.md and the code documentation.
