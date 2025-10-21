# ESPHome Hartmann Heat Pump Integration

<!--
Copyright 2025 Hartmann Heat Pump Integration

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

![Maintenance](https://img.shields.io/maintenance/yes/2025?style=for-the-badge)
![GitHub License](https://img.shields.io/github/license/apache/apache?style=for-the-badge)

An ESPHome-based integration for Hartmann heat pumps using Modbus RTU protocol. This project provides comprehensive integration with Home Assistant, enabling real-time monitoring and control of heat pump systems.

Based on: [ESPHome PV Inverter](https://github.com/eWuPi/esphome-pv-inverter)

🇵🇱 **[Polish version available](README_PL.md)**

## 🚀 Features

- **Real-time Monitoring**: Monitor temperature, pressure, flow rate and other heat pump parameters
- **Remote Control**: Control operation modes, target temperatures and other settings
- **Home Assistant Integration**: Seamless integration via ESPHome API
- **Safety Features**: Automatic fallback to safe parameters when Home Assistant connection is lost
- **Modular Design**: Clean, maintainable code structure

## 🛠️ Hardware Requirements

- **ESP32 Development Board** (e.g., ESP32-DevKit V1)
- **RS485 to TTL Converter**
- **Hartmann Heat Pump** with Modbus RTU support
- **Connection Cables** (for RS485 communication)

## 🔌 Wiring

Connect your ESP32-DevKit V1 to the heat pump's Modbus port:

```
ESP32          RS485 Converter    Heat Pump
GPIO17 (TX) -> DI/A+            -> A+ (Modbus)
GPIO16 (RX) -> RO/B-            -> B- (Modbus)
3.3V        -> VCC             
GND         -> GND             -> GND (Modbus)
```

**Note**: Some RS485 converters may require a flow control pin. Uncomment and configure the `flow_control_pin` in the main configuration if needed.

## ⚙️ Installation

### Method 1: Home Assistant ESPHome Add-on (Recommended)

#### Prerequisites
- [Home Assistant](https://www.home-assistant.io/) with Add-on store access
- ESP32 development board
- RS485 to TTL converter

#### Step 1: Install ESPHome Add-on
1. In Home Assistant, go to **Settings** → **Add-ons** → **Add-on Store**
2. Search for **"ESPHome"** and click **Install**
3. After installation, click **Start** and optionally enable **"Start on boot"**
4. Click **"Open Web UI"** to access ESPHome dashboard

#### Step 2: Add New Device
1. In ESPHome dashboard, click **"+ NEW DEVICE"**
2. Click **"CONTINUE"** on the welcome screen
3. Enter a name for your device (e.g., "Hartmann Heat Pump")
4. Select your **"ESP"** device as device type
5. Click **"NEXT"** and note down the encryption key (save it safely)
6. Click **"SKIP"** for now - we'll add the configuration manually

#### Step 3: Configure Device
1. **Create secrets file**:
   Create `secrets.yaml` in your ESPHome configuration directory:
   ```yaml
   wifi_ssid: "YourWiFiSSID"
   wifi_password: "YourWiFiPassword"
   hartmann_api_key: "your-32-character-api-key"
   hartmann_ota_password: "your-ota-password"
   hartmann_fallback_password: "your-fallback-password"
   ```
2. Click **"EDIT"** on your newly created device
3. **Replace the entire content** with the configuration from [`hartmann-heat-pump.yaml`](hartmann-heat-pump.yaml)
4. Click **"SAVE"** and then **"INSTALL"**

#### Step 4: Flash to ESP32
1. Connect your ESP32 to your computer via USB
2. Click **"Plug into this computer"**
3. Select the correct COM port
4. Click **"INSTALL"** and wait for the process to complete
5. Click **"STOP LOGS"** when installation is finished

#### Step 5: Connect Hardware
1. Disconnect ESP32 from computer
2. Connect RS485 converter according to wiring diagram above
3. Power up the ESP32 (via USB power adapter or external power)
4. The device should appear in Home Assistant automatically under **Settings** → **Devices & Services** → **ESPHome**

## 🔧 Configuration Options

### Main Configuration (`hartmann-heat-pump.yaml`)

| Parameter | Description | Default Value | Required |
|-----------|-------------|---------------|----------|
| `name` | Device name in ESPHome | `hartmann-heat-pump` | No |
| `friendly_name` | Friendly device name | `Hartmann Heat Pump` | No |
| `device_description` | Device description | `Hartmann Heat Pump Integration` | No |
| `modbus_controller_id` | Modbus controller ID | `hartmann_modbus_controller` | No |
| `modbus_heat_pump_address` | Modbus address of heat pump | `0x01` | No |
| `baud_rate` | Baud rate for Modbus communication | `9600` | No |
| `update_interval` | Sensor update frequency | `5s` | No |

### Heat Pump Configuration

| Parameter | Description | Default Value | Required |
|-----------|-------------|---------------|----------|
| `safe_mode_delay` | Delay before activating safe mode | `600s` | No |
| `default_target_temp_heating` | Default heating target temperature in safe mode | `21` | No |
| `default_target_temp_cooling` | Default cooling target temperature in safe mode | `24` | No |

### Default Hardware Configuration

- **UART Pins**: GPIO17 (TX), GPIO16 (RX)
- **Baud Rate**: 9600
- **Board**: ESP32-DevKit v1 (configurable)
- **Flow Control**: Optional GPIO4 (uncomment if needed)

## 🏠 Home Assistant Integration

This project automatically integrates with Home Assistant through the ESPHome API. Once flashed and connected, you'll have access to:

### Sensors
- **Temperatures**: Indoor, outdoor, water, return temperatures
- **Pressures**: Heating and cooling circuit pressures
- **Flow Rates**: Water and refrigerant flow
- **Heat Pump Status**: Operating state, error codes, operating mode

### Controls
- **Operation Modes**: Heating, cooling, automatic
- **Target Temperatures**: Setpoints for different modes
- **Schedules**: Programmable temperature profiles
- **Advanced Parameters**: Heating curve settings, hysteresis

### Safety Features
- **Automatic Safe Mode**: Transition to safe parameters when Home Assistant connection is lost
- **Connection Monitoring**: Real-time connection status
- **Parameter Validation**: Ensures all settings remain within safe operating ranges
- **Emergency Access**: Fallback WiFi hotspot with configurable password

## 🔒 Safety Features

The system includes comprehensive safety mechanisms:

1. **Connection Monitoring**: Continuously monitors connection to Home Assistant
2. **Safe Mode Transition**: Automatically applies safe operating parameters when disconnected for more than 10 minutes
3. **Parameter Validation**: All settings are validated against safe operating ranges
4. **Fallback Access**: Emergency WiFi hotspot with configurable password
5. **Hardware Protection**: Modbus communication timeouts and error handling

## 🐛 Troubleshooting

### Common Issues

1. **No Communication with Heat Pump**:
   - Check RS485 wiring (A+/B- connections)
   - Verify Modbus address matches heat pump settings
   - Ensure correct baud rate (9600)
   - Check modbus_heat_pump_address in configuration

2. **WiFi Connection Issues**:
   - Verify SSID and password in configuration
   - Check WiFi signal strength at ESP32 location
   - Use fallback hotspot for emergency access
   - Check router firewall settings

3. **Home Assistant Integration Problems**:
   - Verify API key matches between configuration and Home Assistant
   - Check ESPHome add-on logs for connection errors
   - Ensure ESPHome add-on is running and accessible
   - Verify network connectivity between devices

### Debug Mode

Enable verbose logging by uncommenting in `hartmann-heat-pump.yaml`:
```yaml
logger:
  level: VERBOSE
```

Then check logs in ESPHome dashboard or Home Assistant ESPHome integration.

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [ESPHome PV Inverter by eWuPi](https://github.com/eWuPi/esphome-pv-inverter) for inspiration and project structure
- [ESPHome Team](https://esphome.io/) for the excellent home automation platform
- [Home Assistant Community](https://community.home-assistant.io/) for continuous support and inspiration

## 📞 Support

- **GitHub Issues**: [Report bugs or request features](https://github.com/user/esphome-hartmann-heat-pump/issues)
- **Discussions**: [GitHub Discussions](https://github.com/user/esphome-hartmann-heat-pump/discussions) for questions and community support
- **Home Assistant Community**: [ESPHome section](https://community.home-assistant.io/c/esphome/) for general ESPHome help

---

**⚠️ Disclaimer**: This project is not officially affiliated with the Hartmann brand. Use at your own risk and ensure compliance with local electrical codes and regulations. Always consult with a qualified technician for installation and safety verification. The authors are not responsible for any damage to equipment or injury resulting from the use of this software.