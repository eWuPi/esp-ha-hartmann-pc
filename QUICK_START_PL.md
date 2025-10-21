# Szybki start - Hartmann Heat Pump ESPHome Integration

🇬🇧 **[English version available](QUICK_START_EN.md)**

## Przygotowanie środowiska

### 1. Wymagania
- Home Assistant z dodatkiem ESPHome
- Płytka ESP32 (zalecane ESP32-DevKit V1)
- Konwerter RS485 na TTL
- Kable połączeniowe

### 2. Konfiguracja pliku secrets.yaml

Skopiuj plik `secrets.yaml.example` na `secrets.yaml` i uzupełnij:

```yaml
wifi_ssid: "TwojaNazwaSieci"
wifi_password: "TwojeHasloWiFi"
hartmann_api_key: "wygeneruj-32-znakowy-klucz-szyfrowania"
hartmann_ota_password: "haslo-do-ota"
hartmann_fallback_password: "haslo-hotspot-awaryjnego"
```

### 3. Generowanie klucza API

W ESPHome:
1. Utwórz nowe urządzenie
2. Skopiuj wygenerowany klucz API do `secrets.yaml`

### 4. Wgrywanie oprogramowania

1. Podłącz ESP32 przez USB
2. W ESPHome kliknij "INSTALL"
3. Wybierz "Plug into this computer"
4. Poczekaj na zakończenie instalacji

### 5. Podłączenie do pompy ciepła

```
ESP32 (GPIO)    RS485 Converter    Pompa Hartmann
GPIO17 (TX)  -> DI/A+           -> A+ (Modbus)
GPIO16 (RX)  -> RO/B-           -> B- (Modbus)
3.3V         -> VCC
GND          -> GND            -> GND (Modbus)
```

### 6. Konfiguracja pompy ciepła

Sprawdź w menu pompy:
- Adres Modbus (domyślnie 0x01)
- Prędkość transmisji (ustawić 9600)
- Włączona komunikacja Modbus

### 7. Pierwsza weryfikacja

Po podłączeniu sprawdź w Home Assistant:
1. **Settings** → **Devices & Services** → **ESPHome**
2. Urządzenie powinno być widoczne jako "Online"
3. Sprawdź logi pod kątem błędów komunikacji

### 8. Dostosowanie mapowania rejestrów

⚠️ **WAŻNE**: Przykładowe adresy w pliku YAML wymagają weryfikacji!

1. Sprawdź dokumentację pompy Hartmann
2. Przetestuj każdy rejestr osobno
3. Dostosuj adresy w pliku `hartmann-heat-pump.yaml`

### 9. Tryb testowy

Na początku zaleca się:
1. Odkomentować `level: VERBOSE` w sekcji `logger:`
2. Pozostawić tylko sensory odczytu (bez zapisów)
3. Stopniowo dodawać kolejne funkcje

### Typowe problemy

**Brak komunikacji z pompą:**
- Sprawdź okablowanie A+/B-
- Zweryfikuj adres Modbus
- Sprawdź prędkość transmisji

**Błędne wartości sensorów:**
- Sprawdź skalowanie (multiply/filters)
- Zweryfikuj typy danych (S_WORD/U_WORD)
- Sprawdź czy adresy są prawidłowe

**Problemy WiFi:**
- Sprawdź siłę sygnału
- Użyj hotspot awaryjnego (nazwa: "Hartmann Heat Pump Fallback Hotspot")

### Wsparcie

1. Sprawdź logi w ESPHome
2. Zobacz plik `MODBUS_MAP.md` dla mapowania rejestrów
3. Przeczytaj pełną dokumentację w `README.md`