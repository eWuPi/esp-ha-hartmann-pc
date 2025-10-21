# Hartmann Heat Pump ESPHome Integration - Modbus Register Map

🇵🇱 **[Wersja polska dostępna](MODBUS_MAP_PL.md)**

## Notice: Example Modbus Address Map

**IMPORTANT**: The addresses below are examples based on typical heat pump register maps. 
Actual addresses for Hartmann heat pump must be verified in the technical documentation or through testing.

## Temperature Sensors (Holding Registers)

| Address | Name                    | Type   | Unit | Scale | Description |
|---------|-------------------------|--------|------|-------|-------------|
| 0x0001  | Outdoor Temperature     | S_WORD | °C   | 0.1   | Outdoor air temperature |
| 0x0002  | Indoor Temperature      | S_WORD | °C   | 0.1   | Indoor air temperature |
| 0x0003  | Water Temperature       | S_WORD | °C   | 0.1   | Water tank temperature |
| 0x0004  | Return Temperature      | S_WORD | °C   | 0.1   | Return water temperature |
| 0x0005  | Supply Temperature      | S_WORD | °C   | 0.1   | Supply water temperature |
| 0x0006  | Evaporator Temperature  | S_WORD | °C   | 0.1   | Evaporator temperature |
| 0x0007  | Condenser Temperature   | S_WORD | °C   | 0.1   | Condenser temperature |

## Pressure Sensors (Holding Registers)

| Address | Name                      | Type   | Unit | Scale | Description |
|---------|---------------------------|--------|------|-------|-------------|
| 0x0010  | Heating Circuit Pressure  | U_WORD | bar  | 0.01  | Heating circuit pressure |
| 0x0011  | Cooling Circuit Pressure  | U_WORD | bar  | 0.01  | Cooling circuit pressure |
| 0x0012  | High Pressure             | U_WORD | bar  | 0.01  | High pressure in system |
| 0x0013  | Low Pressure              | U_WORD | bar  | 0.01  | Low pressure in system |

## Flow Sensors (Holding Registers)

| Address | Name                    | Type   | Unit  | Scale | Description |
|---------|-------------------------|--------|-------|-------|-------------|
| 0x0020  | Water Flow              | U_WORD | l/min | 0.1   | Water flow in heating circuit |
| 0x0021  | Refrigerant Flow        | U_WORD | l/min | 0.1   | Refrigerant flow |

## Status and Operating Modes (Holding Registers)

| Address | Name                    | Type   | Values | Description |
|---------|-------------------------|--------|--------|-------------|
| 0x0100  | Operating Mode          | U_WORD | 0-4    | 0=Off, 1=Heating, 2=Cooling, 3=Auto, 4=Defrost |
| 0x0101  | Heat Pump Status        | U_WORD | 0-3    | 0=Stop, 1=Running, 2=Error, 3=Maintenance |
| 0x0102  | Error Code              | U_WORD | 0-999  | Active error code (0 = no errors) |

## Target Temperatures (Holding Registers - Read/Write)

| Address | Name                         | Type   | Unit | Range | Scale | Description |
|---------|------------------------------|--------|------|-------|-------|-------------|
| 0x0200  | Heating Target Temperature   | S_WORD | °C   | 15-30 | 0.1   | Target heating temperature |
| 0x0201  | Cooling Target Temperature   | S_WORD | °C   | 18-35 | 0.1   | Target cooling temperature |
| 0x0202  | DHW Target Temperature       | S_WORD | °C   | 35-65 | 0.1   | Target domestic hot water temperature |

## Control (Coil Registers)

| Address | Name                    | Type | Description |
|---------|-------------------------|------|-------------|
| 0x0001  | Main Power              | COIL | Heat pump main switch |
| 0x0002  | Heating Enable          | COIL | Enable heating mode |
| 0x0003  | Cooling Enable          | COIL | Enable cooling mode |
| 0x0004  | DHW Enable              | COIL | Enable domestic hot water heating |
| 0x0005  | Circulation Pump        | COIL | Circulation pump control |

## Commands (Holding Registers - Write Only)

| Address | Name                    | Type   | Value | Description |
|---------|-------------------------|--------|-------|-------------|
| 0x0500  | Defrost Command         | U_WORD | 1     | Start manual defrost |
| 0x0501  | Reset Errors            | U_WORD | 1     | Reset active errors |
| 0x0502  | System Restart          | U_WORD | 1     | Restart heat pump controller |

## Advanced Parameters (Holding Registers - Read/Write)

| Address | Name                         | Type   | Unit | Range | Description |
|---------|------------------------------|--------|------|-------|-------------|
| 0x0300  | Heating Curve               | U_WORD | -    | 0.5-4.0| Heating curve slope |
| 0x0301  | Temperature Hysteresis      | U_WORD | °C   | 0.5-3.0| Temperature control hysteresis |
| 0x0302  | Start Delay Time            | U_WORD | min  | 1-10   | Start delay after command |

---

**SAFETY WARNING**: 
- Verify all addresses with Hartmann heat pump technical documentation before use
- Test in read-only mode before enabling writes
- Keep backups of original heat pump settings
- Consult with manufacturer/service when in doubt

**How to obtain correct map**:
1. Check Hartmann heat pump technical documentation
2. Contact manufacturer/service
3. Use Modbus diagnostic tools to scan registers
4. Check if heat pump has debug mode displaying addresses