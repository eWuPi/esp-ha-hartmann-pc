# ESPHome Hartmann Heat Pump Integration

🌐 **Multi-language support** | **Obsługa wielojęzyczna** 🇵🇱🇬🇧

![Maintenance](https://img.shields.io/maintenance/yes/2025?style=for-the-badge)
![GitHub License](https://img.shields.io/github/license/apache/apache?style=for-the-badge)
![Language](https://img.shields.io/badge/Languages-PL%20%7C%20EN-blue?style=for-the-badge)

## 🌍 Choose Your Language / Wybierz język

**🇬🇧 ENGLISH**: For English documentation, see **[README_EN.md](README_EN.md)**

**🇵🇱 POLSKI**: Dla polskiej dokumentacji, zobacz **[README_PL.md](README_PL.md)**

---

## 📁 Project Structure / Struktura projektu

```
hartmann-heat-pump/
├── hartmann-heat-pump.yaml              # Main multilingual configuration
├── secrets.yaml.example                 # Configuration template
├── packages/
│   └── sensors/
│       ├── hartmann_sensors_EN.yaml     # English sensor definitions
│       └── hartmann_sensors_PL.yaml     # Polish sensor definitions
├── MODBUS_MAP_EN.md                     # Modbus documentation (English)
├── MODBUS_MAP_PL.md                     # Modbus documentation (Polish)
├── README_EN.md                         # English documentation
├── README_PL.md                         # Polish documentation
├── LANGUAGE_GUIDE_PL.md                 # Language setup guide
├── LANGUAGE_EXAMPLES_PL.md              # Language examples
├── QUICK_START_EN.md                    # Quick start (English)
└── QUICK_START_PL.md                    # Quick start (Polish)
```

---

## 🚀 Quick Setup / Szybka konfiguracja

### 1. Choose language in `hartmann-heat-pump.yaml`:

```yaml
# For English interface:
language_pack: "EN"

# For Polish interface:
language_pack: "PL"
```

### 2. Configure your `secrets.yaml`
### 3. Flash to ESP32
### 4. Add to Home Assistant

---

## 📖 Documentation / Dokumentacja

| Language | Documentation | Quick Start | Language Guide |
|----------|---------------|-------------|----------------|
| 🇬🇧 English | [README_EN.md](README_EN.md) | [QUICK_START_EN.md](QUICK_START_EN.md) | [LANGUAGE_GUIDE_PL.md](LANGUAGE_GUIDE_PL.md) |
| 🇵🇱 Polski | [README_PL.md](README_PL.md) | [QUICK_START_PL.md](QUICK_START_PL.md) | [LANGUAGE_GUIDE_PL.md](LANGUAGE_GUIDE_PL.md) |

---

## 🔧 Technical Details / Szczegóły techniczne

- **Platform**: ESPHome on ESP32
- **Communication**: Modbus RTU (RS485)
- **Heat Pump**: Hartmann models with Modbus support
- **Home Assistant**: Automatic integration via ESPHome API
- **Languages**: English (EN) / Polish (PL)

---

## 📄 License / Licencja

Licensed under the Apache License, Version 2.0 - see [LICENSE](LICENSE) for details.

Licencjonowane na licencji Apache License, Version 2.0 - szczegóły w pliku [LICENSE](LICENSE).