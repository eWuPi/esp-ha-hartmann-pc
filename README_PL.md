# ESPHome Hartmann Heat Pump Integration

🌐 **Wielojęzyczna integracja** | **Multi-language integration** 🇵🇱🇬🇧

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
![Language](https://img.shields.io/badge/Languages-PL%20%7C%20EN-blue?style=for-the-badge)

## 🌍 Language Support / Obsługa języków

**🇬🇧 English**: This integration supports English interface - see `README_EN.md` for English documentation.

**🇵🇱 Polski**: Ta integracja obsługuje polski interfejs - niniejsza dokumentacja jest w języku polskim.

## 🎯 Szybki Start - Wybór Języka

Ta integracja oferuje **dwie opcje instalacji**:

### 📦 Opcja 1: Wielojęzyczna (DOMYŚLNA)
Użyj pliku `hartmann-heat-pump.yaml` aby wybrać język interfejsu:

```yaml
# Dla polskiego interfejsu:
language_pack: "PL"

# Dla angielskiego interfejsu:
# language_pack: "EN"
```

**Korzyści:**
- ✅ Łatwa zmiana języka bez edycji całej konfiguracji
- ✅ Wszystkie sensory z polskimi/angielskimi nazwami
- ✅ Przyszłe aktualizacje języków

### 📄 Opcja 2: Legacy (dla zaawansowanych)
Jeśli potrzebujesz specjalnych modyfikacji, możesz stworzyć własną konfigurację bazując na strukturze pakietów.

📖 **Szczegółowe instrukcje**: Zobacz `LANGUAGE_GUIDE_PL.md`

---

Integracja ESPHome dla pompy ciepła Hartmann opartej na protokole Modbus RTU. Projekt zapewnia kompleksową integrację z Home Assistant, umożliwiając monitorowanie i sterowanie systemem pompy ciepła w czasie rzeczywistym.

Projekt bazuje na integracji: [ESPHome PV Inverter](https://github.com/eWuPi/esphome-pv-inverter)

🇬🇧 **[English version available](README_EN.md)**

## 🚀 Funkcje

- **Monitorowanie w czasie rzeczywistym**: Monitoruj temperaturę, ciśnienie, przepływ i inne parametry pompy ciepła
- **Zdalne sterowanie**: Kontrola trybów pracy, temperatur zadanych i innych parametrów
- **Integracja z Home Assistant**: Bezproblemowa integracja poprzez API ESPHome
- **Funkcje bezpieczeństwa**: Automatyczne przejście do bezpiecznych parametrów przy utracie połączenia z Home Assistant
- **Modułowa konstrukcja**: Przejrzysta, łatwa w utrzymaniu struktura kodu

## 🛠️ Wymagania sprzętowe

- **Płytka ESP32** (np. ESP32-DevKit V1)
- **Konwerter RS485 na TTL**
- **Pompa ciepła Hartmann** z obsługą Modbus RTU
- **Kable połączeniowe** (do komunikacji RS485)

## 🔌 Okablowanie

Podłącz ESP32-DevKit V1 do portu Modbus pompy ciepła:

```
ESP32          Konwerter RS485    Pompa ciepła
GPIO17 (TX) -> DI/A+            -> A+ (Modbus)
GPIO16 (RX) -> RO/B-            -> B- (Modbus)
3.3V        -> VCC             
GND         -> GND             -> GND (Modbus)
```

**Uwaga**: Niektóre konwertery RS485 mogą wymagać pinu kontroli przepływu. Odkomentuj i skonfiguruj `flow_control_pin` w głównej konfiguracji jeśli to konieczne.

## ⚙️ Instalacja

### Metoda 1: Dodatek ESPHome w Home Assistant (Zalecane)

#### Wymagania wstępne
- [Home Assistant](https://www.home-assistant.io/) z dostępem do sklepu dodatków
- Płytka ESP32
- Konwerter RS485 na TTL

#### Krok 1: Instalacja dodatku ESPHome
1. W Home Assistant, przejdź do **Ustawienia** → **Dodatki** → **Sklep dodatków**
2. Wyszukaj **"ESPHome"** i kliknij **Instaluj**
3. Po instalacji kliknij **Uruchom** i opcjonalnie włącz **"Uruchom przy starcie"**
4. Kliknij **"Otwórz interfejs WWW"** aby uzyskać dostęp do panelu ESPHome

#### Krok 2: Dodawanie nowego urządzenia
1. W panelu ESPHome kliknij **"+ NOWE URZĄDZENIE"**
2. Kliknij **"KONTYNUUJ"** na ekranie powitalnym
3. Wprowadź nazwę urządzenia (np. "Hartmann Heat Pump")
4. Wybierz typ urządzenia **"ESP"**
5. Kliknij **"DALEJ"** i zapisz klucz szyfrowania (zachowaj go bezpiecznie)
6. Kliknij **"POMIŃ"** na razie - dodamy konfigurację ręcznie

#### Krok 3: Konfiguracja urządzenia
1. **Utwórz plik secrets**:
   Utwórz `secrets.yaml` w katalogu konfiguracji ESPHome:
   ```yaml
   wifi_ssid: "NazwaTwojejSieciWiFi"
   wifi_password: "HasloWiFi"
   hartmann_api_key: "twoj-32-znakowy-klucz-api"
   hartmann_ota_password: "haslo-ota"
   hartmann_fallback_password: "haslo-awaryjne"
   modbus_heat_pump_address: "1"  # Adres Modbus pompy ciepła
   baud_rate: "9600"              # Prędkość komunikacji Modbus
   safe_mode_delay: "30s"         # Opóźnienie trybu bezpiecznego
   default_target_temp_heating: "22"   # Domyślna temperatura ogrzewania
   default_target_temp_cooling: "24"   # Domyślna temperatura chłodzenia
   ```

2. **Wybierz plik konfiguracyjny**:
   
   **🌐 DOMYŚLNIE - Wersja wielojęzyczna:**
   - Pobierz i użyj pliku [`hartmann-heat-pump.yaml`](hartmann-heat-pump.yaml)
   - Ustaw `language_pack: "PL"` dla polskiego interfejsu
   - Lub ustaw `language_pack: "EN"` dla angielskiego interfejsu
   
   **📄 Alternatywnie - Własna konfiguracja:**
   - Stwórz własną konfigurację bazując na plikach w folderze `packages/`

3. Kliknij **"EDYTUJ"** na nowo utworzonym urządzeniu
4. **Zastąp całą zawartość** wybraną konfiguracją
5. **Edytuj sekcję wyboru języka** (tylko dla wersji wielojęzycznej):
   ```yaml
   # For Polish interface:
   language_pack: "PL"
   
   # For English interface:
   # language_pack: "EN"
   ```
6. Kliknij **"ZAPISZ"** a następnie **"INSTALUJ"**

#### Krok 4: Wgrywanie do ESP32
1. Podłącz ESP32 do komputera przez USB
2. Kliknij **"Podłącz do tego komputera"**
3. Wybierz odpowiedni port COM
4. Kliknij **"INSTALUJ"** i poczekaj na zakończenie procesu
5. Kliknij **"ZATRZYMAJ LOGI"** gdy instalacja się zakończy

#### Krok 5: Podłączenie sprzętu
1. Odłącz ESP32 od komputera
2. Podłącz konwerter RS485 zgodnie z powyższym schematem
3. Uruchom ESP32 (przez zasilacz USB lub zewnętrzne zasilanie)
4. Urządzenie powinno pojawić się automatycznie w Home Assistant pod **Ustawienia** → **Urządzenia i usługi** → **ESPHome**

## 🔧 Opcje konfiguracji

### Główna konfiguracja (`hartmann-heat-pump.yaml`)

| Parametr | Opis | Domyślna wartość | Wymagany |
|----------|------|------------------|----------|
| `name` | Nazwa urządzenia w ESPHome | `hartmann-heat-pump` | Nie |
| `friendly_name` | Przyjazna nazwa urządzenia | `Hartmann Heat Pump` | Nie |
| `device_description` | Opis urządzenia | `Hartmann Heat Pump Integration` | Nie |
| `modbus_controller_id` | ID kontrolera Modbus | `hartmann_modbus_controller` | Nie |
| `modbus_heat_pump_address` | Adres Modbus pompy ciepła | `0x01` | Nie |
| `baud_rate` | Prędkość transmisji Modbus | `9600` | Nie |
| `update_interval` | Częstotliwość odczytu danych | `5s` | Nie |

### Konfiguracja pompy ciepła

| Parametr | Opis | Domyślna wartość | Wymagany |
|----------|------|------------------|----------|
| `safe_mode_delay` | Opóźnienie przed aktywacją trybu bezpiecznego | `600s` | Nie |
| `default_target_temp_heating` | Domyślna temperatura grzania w trybie bezpiecznym | `21` | Nie |
| `default_target_temp_cooling` | Domyślna temperatura chłodzenia w trybie bezpiecznym | `24` | Nie |

### Domyślna konfiguracja sprzętowa

- **Piny UART**: GPIO17 (TX), GPIO16 (RX)  
- **Prędkość transmisji**: 9600
- **Płytka**: ESP32-DevKit v1 (konfigurowalne)
- **Kontrola przepływu**: Opcjonalny GPIO4 (odkomentuj jeśli potrzebny)

## 🏠 Integracja z Home Assistant

Ten projekt automatycznie integruje się z Home Assistant poprzez API ESPHome. Po wgraniu i podłączeniu będziesz mieć dostęp do:

### Sensory
- **Temperatury**: Temperatura wewnętrzna, zewnętrzna, wody, powrotu
- **Ciśnienia**: Ciśnienie w obiegach grzewczym i chłodniczym
- **Przepływy**: Przepływ wody i czynnika chłodniczego
- **Status pompy**: Stan pracy, kody błędów, tryb działania

### Sterowanie
- **Tryby pracy**: Grzanie, chłodzenie, automatyczny
- **Temperatury zadane**: Ustawienia temperatur dla różnych trybów
- **Harmonogramy**: Programowalne profile temperatur
- **Parametry zaawansowane**: Ustawienia krzywej grzewczej, histerez

### Funkcje bezpieczeństwa
- **Automatyczny tryb bezpieczny**: Przejście do bezpiecznych parametrów przy utracie połączenia z Home Assistant
- **Monitorowanie połączenia**: Status połączenia w czasie rzeczywistym
- **Walidacja parametrów**: Sprawdzanie czy wszystkie ustawienia mieszczą się w bezpiecznych zakresach
- **Dostęp awaryjny**: Awaryjny hotspot WiFi z konfigurowalnym hasłem

## 🔒 Funkcje bezpieczeństwa

System zawiera kompleksowe mechanizmy bezpieczeństwa:

1. **Monitorowanie połączenia**: Ciągłe monitorowanie połączenia z Home Assistant
2. **Przejście do trybu bezpiecznego**: Automatyczne stosowanie bezpiecznych parametrów przy rozłączeniu przez ponad 10 minut
3. **Walidacja parametrów**: Wszystkie ustawienia są sprawdzane pod kątem bezpiecznych zakresów
4. **Dostęp awaryjny**: Awaryjny hotspot WiFi z konfigurowalnym hasłem
5. **Ochrona sprzętowa**: Limity czasowe komunikacji Modbus i obsługa błędów

## 🐛 Rozwiązywanie problemów

### Typowe problemy

1. **Brak komunikacji z pompą ciepła**:
   - Sprawdź okablowanie RS485 (połączenia A+/B-)
   - Zweryfikuj czy adres Modbus pasuje do ustawień pompy
   - Upewnij się że prędkość transmisji jest prawidłowa (9600)
   - Sprawdź modbus_heat_pump_address w konfiguracji

2. **Problemy z połączeniem WiFi**:
   - Zweryfikuj SSID i hasło w konfiguracji
   - Sprawdź siłę sygnału WiFi w miejscu ESP32
   - Użyj awaryjnego hotspotu do dostępu awaryjnego
   - Sprawdź ustawienia firewall routera

3. **Problemy z integracją Home Assistant**:
   - Zweryfikuj czy klucz API pasuje między konfiguracją a Home Assistant
   - Sprawdź logi dodatku ESPHome pod kątem błędów połączenia
   - Upewnij się że dodatek ESPHome działa i jest dostępny
   - Zweryfikuj łączność sieciową między urządzeniami

### Tryb debugowania

Włącz szczegółowe logowanie odkomentowując w `hartmann-heat-pump.yaml`:
```yaml
logger:
  level: VERBOSE
```

Następnie sprawdź logi w panelu ESPHome lub integracji ESPHome w Home Assistant.

## 📄 Licencja

Ten projekt jest licencjonowany na licencji Apache License 2.0 - zobacz plik [LICENSE](LICENSE) po szczegóły.

## 🙏 Podziękowania

- [ESPHome PV Inverter by eWuPi](https://github.com/eWuPi/esphome-pv-inverter) za inspirację i strukturę projektu
- [Zespół ESPHome](https://esphome.io/) za doskonałą platformę automatyki domowej
- [Społeczność Home Assistant](https://community.home-assistant.io/) za ciągłe wsparcie i inspirację

## 📞 Wsparcie

- **GitHub Issues**: [Zgłaszaj błędy lub proś o nowe funkcje](https://github.com/user/esphome-hartmann-heat-pump/issues)
- **Dyskusje**: [GitHub Discussions](https://github.com/user/esphome-hartmann-heat-pump/discussions) dla pytań i wsparcia społeczności
- **Społeczność Home Assistant**: [Sekcja ESPHome](https://community.home-assistant.io/c/esphome/) dla ogólnej pomocy z ESPHome

---

**⚠️ Zastrzeżenie**: Ten projekt nie jest oficjalnie powiązany z marką Hartmann. Używaj na własne ryzyko i upewnij się o zgodności z lokalnymi przepisami i regulacjami. Zawsze skonsultuj się z wykwalifikowanym technikiem instalacji i weryfikacji bezpieczeństwa. Autorzy nie ponoszą odpowiedzialności za jakiekolwiek uszkodzenia sprzętu lub obrażenia wynikające z użycia tego oprogramowania.