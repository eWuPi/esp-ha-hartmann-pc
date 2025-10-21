# Quick Start - Hartmann Heat Pump ESPHome Integration

🇵🇱 **[Wersja polska dostępna](QUICK_START_PL.md)**

## Environment Setup

### 1. Requirements
- Home Assistant with ESPHome add-on
- ESP32 board (recommended ESP32-DevKit V1)
- RS485 to TTL converter
- Connection cables

### 2. Configure secrets.yaml file

Copy `secrets.yaml.example` to `secrets.yaml` and fill in:

```yaml
wifi_ssid: "YourNetworkName"
wifi_password: "YourWiFiPassword"
hartmann_api_key: "generate-32-character-encryption-key"
hartmann_ota_password: "ota-password"
hartmann_fallback_password: "emergency-hotspot-password"
```

### 3. Generate API Key

In ESPHome:
1. Create new device
2. Copy generated API key to `secrets.yaml`

### 4. Flash Firmware

1. Connect ESP32 via USB
2. In ESPHome click "INSTALL"
3. Select "Plug into this computer"
4. Wait for installation to complete

### 5. Connect to Heat Pump

```
ESP32 (GPIO)    RS485 Converter    Hartmann Heat Pump
GPIO17 (TX)  -> DI/A+           -> A+ (Modbus)
GPIO16 (RX)  -> RO/B-           -> B- (Modbus)
3.3V         -> VCC
GND          -> GND            -> GND (Modbus)
```

### 6. Heat Pump Configuration

Check in heat pump menu:
- Modbus address (default 0x01)
- Baud rate (set to 9600)
- Modbus communication enabled

### 7. First Verification

After connection, check in Home Assistant:
1. **Settings** → **Devices & Services** → **ESPHome**
2. Device should be visible as "Online"
3. Check logs for communication errors

### 8. Register Mapping Adjustment

⚠️ **IMPORTANT**: Example addresses in YAML file require verification!

1. Check Hartmann heat pump documentation
2. Test each register individually
3. Adjust addresses in `hartmann-heat-pump.yaml` file

### 9. Test Mode

Initially recommended:
1. Uncomment `level: VERBOSE` in `logger:` section
2. Keep only read-only sensors (no writes)
3. Gradually add more functions

### Common Issues

**No communication with heat pump:**
- Check A+/B- wiring
- Verify Modbus address
- Check baud rate

**Incorrect sensor values:**
- Check scaling (multiply/filters)
- Verify data types (S_WORD/U_WORD)
- Check if addresses are correct

**WiFi issues:**
- Check signal strength
- Use emergency hotspot (name: "Hartmann Heat Pump Fallback Hotspot")

### Support

1. Check ESPHome logs
2. See `MODBUS_MAP.md` for register mapping
3. Read full documentation in `README.md`