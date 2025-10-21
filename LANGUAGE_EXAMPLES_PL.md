# Language Comparison / Porównanie języków

## 🔍 Interface Examples / Przykłady interfejsu

### 🇬🇧 English Interface (`language_pack: "EN"`)

**Temperature Sensors:**
```
- Ambient Temperature
- Inlet Water Temperature  
- Outlet Water Temperature
- Discharge Gas Temperature
- Suction Gas Temperature
- Hot Water Temperature
- Evaporator Coil Temperature
```

**Controls:**
```
- Heating Setpoint
- Cooling Setpoint
- Hot Water Setpoint
- Work Mode Select
  - Cooling
  - Heating  
  - DHW
  - Cooling + DHW
  - Heating + DHW
```

**Status:**
```
- Connection Status
- Flow Switch
- Circulation Pump Status
- Compressor Status
- System Status:
  - Ready
  - Running
  - Alarm Stop
  - Manual Mode
```

---

### 🇵🇱 Polish Interface (`language_pack: "PL"`)

**Sensory temperatury:**
```
- Temperatura zewnętrzna
- Temperatura wody powrotu
- Temperatura wody zasilania  
- Temperatura sprężania
- Temperatura ssania
- Temperatura CWU
- Temperatura parownika
```

**Sterowanie:**
```
- Nastawa ogrzewania
- Nastawa chłodzenia
- Nastawa CWU
- Wybór trybu pracy
  - Chłodzenie
  - Ogrzewanie
  - CWU
  - Chłodzenie + CWU
  - Ogrzewanie + CWU
```

**Status:**
```
- Status połączenia
- Czujnik przepływu
- Status pompy obiegowej
- Status sprężarki
- Status systemu:
  - Gotowość
  - Praca
  - Stop - Alarm
  - Tryb ręczny
```

---

## 🔄 Switching Languages / Zmiana języków

To change language, edit one line in `hartmann-heat-pump.yaml`:

Aby zmienić język, edytuj jedną linię w `hartmann-heat-pump.yaml`:

```yaml
# English:
language_pack: "EN"

# Polish: 
language_pack: "PL"
```

Then recompile and flash the ESP32.

Następnie przekompiluj i wgraj na ESP32.