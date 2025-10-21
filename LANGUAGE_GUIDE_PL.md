# Multi-Language Installation Guide / Przewodnik Instalacji Wielojęzycznej

🇬🇧 **English** | 🇵🇱 **Polski**

## 🌐 Language Selection / Wybór języka

This Hartmann Heat Pump integration supports two languages for the user interface in Home Assistant.

Ta integracja pompy ciepła Hartmann obsługuje dwa języki dla interfejsu użytkownika w Home Assistant.

---

## 🇬🇧 English Installation

### Step 1: Choose Language
Open `hartmann-heat-pump.yaml` and edit the language selection section:

```yaml
# For English interface, uncomment this line:
language_pack: "EN"

# For Polish interface, comment out or remove this line:
# language_pack: "PL"
```

### Step 2: Flash to ESP32
1. Use ESPHome Dashboard or command line to compile and flash the configuration
2. The device will appear in Home Assistant with English entity names

### What you'll see in English:
- **Temperatures**: "Ambient Temperature", "Inlet Water Temperature", "Outlet Water Temperature", etc.
- **Controls**: "Heating Setpoint", "Cooling Setpoint", "Work Mode Select"
- **Status**: "Running", "Ready", "Alarm Stop", etc.
- **Modes**: "Heating", "Cooling", "DHW", "Cooling + DHW", "Heating + DHW"

---

## 🇵🇱 Instalacja w języku polskim

### Krok 1: Wybór języka
Otwórz plik `hartmann-heat-pump.yaml` i edytuj sekcję wyboru języka:

```yaml
# For English interface, comment out or remove this line:
# language_pack: "EN"

# For Polish interface, uncomment this line:
language_pack: "PL"
```

### Krok 2: Wgranie na ESP32
1. Użyj ESPHome Dashboard lub linii poleceń aby skompilować i wgrać konfigurację
2. Urządzenie pojawi się w Home Assistant z polskimi nazwami encji

### Co zobaczysz po polsku:
- **Temperatury**: "Temperatura zewnętrzna", "Temperatura wody powrotu", "Temperatura wody zasilania", itp.
- **Sterowanie**: "Nastawa ogrzewania", "Nastawa chłodzenia", "Wybór trybu pracy"
- **Status**: "Praca", "Gotowość", "Stop - Alarm", itp.
- **Tryby**: "Ogrzewanie", "Chłodzenie", "CWU", "Chłodzenie + CWU", "Ogrzewanie + CWU"

---

## 📁 File Structure / Struktura plików

```
hartmann-heat-pump/
├── hartmann-heat-pump.yaml              # Main multilingual configuration
├── secrets.yaml                         # Configuration secrets
├── packages/
│   └── sensors/
│       ├── hartmann_sensors_EN.yaml     # English sensor definitions
│       └── hartmann_sensors_PL.yaml     # Polish sensor definitions
├── MODBUS_MAP_PL.md                     # Modbus register documentation (Polish)
├── MODBUS_MAP_EN.md                     # Modbus register documentation (English)
├── README_PL.md                         # Polish documentation
├── README_EN.md                         # English documentation
└── QUICK_START_PL.md / QUICK_START_EN.md # Quick start guides
```

---

## 🔧 Technical Details / Szczegóły techniczne

### How it works / Jak to działa

The multi-language system uses ESPHome's `packages` feature to include different sensor definitions based on the selected language.

System wielojęzyczny używa funkcji `packages` ESPHome aby dołączać różne definicje sensorów w zależności od wybranego języka.

**English (en):**
```yaml
packages:
  sensor_package: !include packages/sensors/hartmann_sensors_EN.yaml
```

**Polish (pl):**
```yaml
packages:
  sensor_package: !include packages/sensors/hartmann_sensors_PL.yaml
```

### Changing Language / Zmiana języka

To change the language after installation:

Aby zmienić język po instalacji:

1. **Edit configuration / Edytuj konfigurację**: Change `language_pack` value in `hartmann-heat-pump.yaml`
2. **Recompile / Przekompiluj**: Use ESPHome to recompile the firmware
3. **Flash / Wgraj**: Upload the new firmware to ESP32
4. **Restart / Restartuj**: The device will restart with new language

---

## 🎯 Quick Start / Szybki start

### For English users:
1. Copy `hartmann-heat-pump.yaml` to your ESPHome config directory
2. Set `language_pack: "EN"` 
3. Configure your `secrets.yaml`
4. Flash to ESP32

### Dla polskich użytkowników:
1. Skopiuj `hartmann-heat-pump.yaml` do katalogu konfiguracji ESPHome
2. Ustaw `language_pack: "PL"`
3. Skonfiguruj swój `secrets.yaml`
4. Wgraj na ESP32

---

## 🛠️ Supported Languages / Obsługiwane języki

| Language / Język | Code / Kod | File / Plik | Status |
|------------------|------------|-------------|---------|
| English | `EN` | `hartmann_sensors_EN.yaml` | ✅ Available |
| Polski | `PL` | `hartmann_sensors_PL.yaml` | ✅ Dostępny |

---

## 📞 Support / Wsparcie

**🇬🇧 English**: If you need help with the English version, check the `README_EN.md` file.

**🇵🇱 Polski**: Jeśli potrzebujesz pomocy z polską wersją, sprawdź plik `README_PL.md`.

---

## 🔄 Migration from Single Language / Migracja z wersji jednojęzycznej

If you're upgrading from the original `hartmann-heat-pump.yaml`:

Jeśli aktualizujesz z oryginalnego `hartmann-heat-pump.yaml`:

1. **Backup your secrets / Zrób kopię secrets**: Keep your current `secrets.yaml`
2. **Choose language / Wybierz język**: Decide between English or Polish
3. **Use new file / Użyj nowego pliku**: Switch to the updated `hartmann-heat-pump.yaml`
4. **Set language / Ustaw język**: Configure `language_pack` parameter
5. **Flash / Wgraj**: Upload the new configuration

The entity IDs remain the same, so your Home Assistant automations will continue to work.

ID encji pozostają takie same, więc Twoje automatyzacje w Home Assistant będą nadal działać.