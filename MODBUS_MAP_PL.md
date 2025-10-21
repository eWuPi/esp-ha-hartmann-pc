# Hartmann Heat Pump - Modbus Register Map / Mapa rejestrów Modbus

🇬🇧 **English** | 🇵🇱 **Polski**

## ✅ Real Addresses / Rzeczywiste adresy

**🇬🇧 ENGLISH**: This register map contains REAL addresses extracted from actual Hartmann heat pump Modbus documentation.

**🇵🇱 POLSKI**: Ta mapa rejestrów zawiera RZECZYWISTE adresy wyciągnięte z faktycznej dokumentacji Modbus pompy ciepła Hartmann.

---

## 🔧 Control Commands / Komendy sterujące (Coils - 10001 series)

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | R/W | Type<br/>Typ | Description (EN) / Opis (PL) |
|-------------------|--------------------------|-----|--------------|-------------------------------|
| 10001 | On/Off Control<br/>Sterowanie Wł/Wył | RW | BOOL | Unit main on/off control<br/>Główne sterowanie wł/wył jednostki |
| 10002 | Flow Switch Status<br/>Stan czujnika przepływu | R | BOOL | Water flow switch status<br/>Stan czujnika przepływu wody |
| 10003 | External Control Input<br/>Wejście sterowania zewnętrznego | R | BOOL | External linkage control switch<br/>Przełącznik sterowania zewnętrznego |
| 10004 | AC Linkage Control<br/>Sterowanie łączenia AC | R | BOOL | AC linkage control switch<br/>Przełącznik sterowania łączenia AC |
| 10005 | Phase Control Input<br/>Wejście kontroli faz | R | BOOL | Phase sequence control switch<br/>Przełącznik kontroli kolejności faz |
| 10006 | Fan High Speed Output<br/>Wyjście wysokiej prędkości wentylatora | O | BOOL | Fan high speed relay output<br/>Wyjście przekaźnika wysokiej prędkości wentylatora |
| 10007 | Fan Low Speed Output<br/>Wyjście niskiej prędkości wentylatora | O | BOOL | Fan low speed relay output<br/>Wyjście przekaźnika niskiej prędkości wentylatora |
| 10008 | 4-Way Valve Output<br/>Wyjście zaworu 4-drogowego | O | BOOL | 4-way valve control output<br/>Wyjście sterowania zaworu 4-drogowego |
| 10009 | Circulation Pump Output<br/>Wyjście pompy obiegowej | O | BOOL | Water circulation pump output<br/>Wyjście pompy obiegowej wody |
| 10010 | Chassis Heater Output<br/>Wyjście grzałki obudowy | O | BOOL | Chassis heater control output<br/>Wyjście sterowania grzałki obudowy |
| 10011 | Compressor Heater Output<br/>Wyjście grzałki sprężarki | O | BOOL | Compressor crankcase heater output<br/>Wyjście grzałki skrzyni korbowej sprężarki |
| 10012 | 3-Way Valve Output<br/>Wyjście zaworu 3-drogowego | O | BOOL | 3-way valve control output<br/>Wyjście sterowania zaworu 3-drogowego |
| 10013 | Auxiliary Heater Output<br/>Wyjście grzałki pomocniczej | O | BOOL | Auxiliary heater control output<br/>Wyjście sterowania grzałki pomocniczej |
| 10179 | Circulation Pump Status<br/>Status pompy obiegowej | R | BOOL | Circulation pump operation status<br/>Status pracy pompy obiegowej |
| 10180 | Compressor Status<br/>Status sprężarki | R | BOOL | Compressor operation status<br/>Status pracy sprężarki |
| 10181 | Fan Status<br/>Status wentylatora | R | BOOL | Fan operation status<br/>Status pracy wentylatora |
| 10182 | Cooling Control Input<br/>Wejście sterowania chłodzeniem | R | BOOL | Cooling linkage control input<br/>Wejście sterowania łączenia chłodzenia |
| 10183 | Heating Control Input<br/>Wejście sterowania ogrzewaniem | R | BOOL | Heating linkage control input<br/>Wejście sterowania łączenia ogrzewania |
| 10184 | Terminal Pump Output<br/>Wyjście pompy terminalowej | O | BOOL | Terminal pump control output<br/>Wyjście sterowania pompy terminalowej |

---

## 🌡️ Temperature Sensors / Sensory temperatury (Holding Registers - 40189-40197)

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | Unit<br/>Jednostka | Scale<br/>Skala | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|-------------------|-----------------|-------------------------------|
| 40189 | Inlet Water Temperature<br/>Temperatura wody powrotu | REAL | °C | 0.1 | Water return temperature (B1)<br/>Temperatura wody powrotnej (B1) |
| 40190 | Outlet Water Temperature<br/>Temperatura wody zasilania | REAL | °C | 0.1 | Water supply temperature (B2)<br/>Temperatura wody zasilającej (B2) |
| 40191 | Ambient Temperature<br/>Temperatura zewnętrzna | REAL | °C | 0.1 | External air temperature (B3)<br/>Temperatura powietrza zewnętrznego (B3) |
| 40192 | Discharge Gas Temperature<br/>Temperatura sprężania | REAL | °C | 0.1 | Compressor discharge temperature (B4)<br/>Temperatura tłoczna sprężarki (B4) |
| 40193 | Suction Gas Temperature<br/>Temperatura ssania | REAL | °C | 0.1 | Compressor suction temperature (B5)<br/>Temperatura ssąca sprężarki (B5) |
| 40196 | Hot Water Temperature<br/>Temperatura CWU | REAL | °C | 0.1 | Domestic hot water temperature (B8)<br/>Temperatura ciepłej wody użytkowej (B8) |
| 40197 | Coil Temperature<br/>Temperatura parownika | REAL | °C | 0.1 | Evaporator coil temperature (B9)<br/>Temperatura wymiennika parownika (B9) |

---

## 🔧 Pressure Sensors / Sensory ciśnienia (Holding Registers)

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | Unit<br/>Jednostka | Scale<br/>Skala | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|-------------------|-----------------|-------------------------------|
| 40194 | Discharge Pressure<br/>Ciśnienie sprężania | REAL | bar | 0.1 | High pressure sensor (B6)<br/>Czujnik wysokiego ciśnienia (B6) |
| 40195 | Suction Pressure<br/>Ciśnienie ssania | REAL | bar | 0.1 | Low pressure sensor (B7)<br/>Czujnik niskiego ciśnienia (B7) |

---

## ⚙️ Operation Mode & Setpoints / Tryb pracy i nastawy (Holding Registers - 40001-40004)

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | R/W | Unit<br/>Jednostka | Scale<br/>Skala | Range<br/>Zakres | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|-----|-------------------|-----------------|------------------|-------------------------------|
| 40001 | Work Mode Select<br/>Wybór trybu pracy | INT | RW | - | 1 | 0-4 | 0:Cooling/Chłodzenie, 1:Heating/Ogrzewanie, 2:DHW/CWU, 3:Cool+DHW/Chł+CWU, 4:Heat+DHW/Ogr+CWU |
| 40002 | Heating Setpoint<br/>Nastawa ogrzewania | REAL | RW | °C | 0.1 | 10-55 | Heating mode target temperature<br/>Docelowa temperatura w trybie ogrzewania |
| 40003 | Cooling Setpoint<br/>Nastawa chłodzenia | REAL | RW | °C | 0.1 | 1.2-25 | Cooling mode target temperature<br/>Docelowa temperatura w trybie chłodzenia |
| 40004 | Hot Water Setpoint<br/>Nastawa CWU | REAL | RW | °C | 0.1 | 10-80 | Hot water target temperature<br/>Docelowa temperatura ciepłej wody |

---

## 📊 System Status & Performance / Status systemu i wydajność

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | Unit<br/>Jednostka | Scale<br/>Skala | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|-------------------|-----------------|-------------------------------|
| 40216 | Current Work Mode<br/>Aktualny tryb pracy | INT | - | 1 | Current operating mode readback<br/>Odczyt aktualnego trybu pracy |
| 40217 | System Temperature<br/>Temperatura systemu | REAL | °C | 0.1 | Current system temperature<br/>Aktualna temperatura systemu |
| 40218 | System Status<br/>Status systemu | INT | - | 1 | 0:Ready/Gotowość, 1:Run/Praca, 2:Alarm/Alarm, 3:Timer/Timer, etc. |
| 40198 | Fan Output Control<br/>Sterowanie wentylatora | REAL | % | 0.1 | Fan speed output percentage (Y1)<br/>Procent wyjścia prędkości wentylatora (Y1) |
| 40199 | Pump Output Control<br/>Sterowanie pompy | REAL | % | 0.1 | Pump PWM output percentage (Y3)<br/>Procent wyjścia PWM pompy (Y3) |
| 40200 | DC Fan 1 Output<br/>Wyjście wentylatora DC 1 | INT | rpm | 1 | DC Fan 1 speed control<br/>Sterowanie prędkości wentylatora DC 1 |
| 40201 | DC Fan 1 Feedback<br/>Sprzężenie wentylatora DC 1 | INT | rpm | 1 | DC Fan 1 actual speed<br/>Rzeczywista prędkość wentylatora DC 1 |
| 40202 | DC Fan 2 Output<br/>Wyjście wentylatora DC 2 | INT | rpm | 1 | DC Fan 2 speed control<br/>Sterowanie prędkości wentylatora DC 2 |
| 40203 | DC Fan 2 Feedback<br/>Sprzężenie wentylatora DC 2 | INT | rpm | 1 | DC Fan 2 actual speed<br/>Rzeczywista prędkość wentylatora DC 2 |
| 40204 | Required Capacity<br/>Wymagana wydajność | REAL | % | 0.1 | Compressor required capacity<br/>Wymagana wydajność sprężarki |
| 40205 | Actual Capacity<br/>Aktualna wydajność | REAL | % | 0.1 | Compressor actual capacity<br/>Aktualna wydajność sprężarki |
| 40206 | Compressor Speed<br/>Prędkość sprężarki | REAL | rps | 1 | Compressor actual speed<br/>Aktualna prędkość sprężarki |
| 40208 | EEV Opening<br/>Otwarcie zaworu EEV | INT | % | 1 | Electronic expansion valve opening<br/>Otwarcie elektronicznego zaworu rozprężnego |
| 40210 | EEV Status<br/>Status EEV | INT | - | 1 | 0:OK, 1:Control/Sterowanie, 2:Limited/Ograniczony |
| 40211 | EEV Protection<br/>Zabezpieczenie EEV | INT | - | 1 | Protection status code<br/>Kod statusu zabezpieczenia |
| 40212 | Suction Superheat<br/>Przegrzanie ssania | REAL | K | 0.1 | Suction gas superheat<br/>Przegrzanie gazu ssącego |

---

## 🚨 Alarm System / System alarmów (Discrete Inputs - 10014-10177)

### Critical Alarms / Alarmy krytyczne
| Address<br/>Adres | Alarm Code<br/>Kod alarmu | Description (EN) / Opis (PL) |
|-------------------|---------------------------|-------------------------------|
| 10016 | AL003 | Inlet probe error<br/>Błąd czujnika temperatury powrotu |
| 10017 | AL004 | Outlet probe error<br/>Błąd czujnika temperatury zasilania |
| 10018 | AL005 | Ambient probe error<br/>Błąd czujnika temperatury zewnętrznej |
| 10019 | AL006 | Condenser coil temperature error<br/>Błąd temperatury skraplacza |
| 10020 | AL007 | Water flow switch alarm<br/>Alarm czujnika przepływu wody |
| 10021 | AL008 | Phase sequence protection<br/>Alarm czujnika faz |

### Compressor Alarms / Alarmy sprężarki
| Address<br/>Adres | Alarm Code<br/>Kod alarmu | Description (EN) / Opis (PL) |
|-------------------|---------------------------|-------------------------------|
| 10048 | AL035 | BLDC: High startup pressure diff<br/>BLDC: Za wysoka różnica ciśnień przy starcie |
| 10049 | AL036 | BLDC: Compressor shut off<br/>BLDC: Wyłączenie sprężarki |
| 10050 | AL037 | BLDC: Out of envelope<br/>BLDC: Błąd transmisji |
| 10051 | AL038 | BLDC: Starting fail wait<br/>BLDC: Nieudane uruchomienie |
| 10052 | AL039 | BLDC: Starting fail exceeded<br/>BLDC: Błąd uruchamiania |

### EEV Alarms / Alarmy zaworu EEV
| Address<br/>Adres | Alarm Code<br/>Kod alarmu | Description (EN) / Opis (PL) |
|-------------------|---------------------------|-------------------------------|
| 10026 | AL013 | EEV A: Low superheat<br/>Zawór A: Niskie przegrzanie |
| 10027 | AL014 | EEV B: Low superheat<br/>Zawór B: Niskie przegrzanie |
| 10028 | AL015 | EEV A: Low pressure (LOP)<br/>Zawór A: Niskie ciśnienie |
| 10029 | AL016 | EEV B: Low pressure (LOP)<br/>Zawór B: Niskie ciśnienie |
| 10030 | AL017 | EEV A: High pressure (MOP)<br/>Zawór A: Wysokie ciśnienie |
| 10031 | AL018 | EEV B: High pressure (MOP)<br/>Zawór B: Wysokie ciśnienie |

---

## 🕒 Time Schedule / Harmonogram czasowy (Holding Registers - 40183-40187)

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | Range<br/>Zakres | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|------------------|-------------------------------|
| 40183 | Year<br/>Rok | UINT | 0-99 | System year<br/>Rok systemowy |
| 40184 | Month<br/>Miesiąc | UINT | 1-12 | System month<br/>Miesiąc systemowy |
| 40185 | Day<br/>Dzień | UINT | 1-31 | System day<br/>Dzień systemowy |
| 40186 | Hour<br/>Godzina | UINT | 0-23 | System hour<br/>Godzina systemowa |
| 40187 | Minute<br/>Minuta | UINT | 0-59 | System minute<br/>Minuta systemowa |
| 40188 | Day of Week<br/>Dzień tygodnia | UINT | 1-7 | Day of week (1=Monday)<br/>Dzień tygodnia (1=Poniedziałek) |

---

## ⚙️ Advanced Parameters / Parametry zaawansowane

| Address<br/>Adres | Name (EN)<br/>Nazwa (PL) | Type<br/>Typ | R/W | Unit<br/>Jednostka | Scale<br/>Skala | Description (EN) / Opis (PL) |
|-------------------|--------------------------|--------------|-----|-------------------|-----------------|-------------------------------|
| 40012 | Pump Work Mode<br/>Tryb pracy pompy | INT | RW | - | 1 | 0:Continuous/Ciągła, 1:External/Zewnętrzne, 2:Interval/Interwał |
| 40013 | Fan Mode<br/>Tryb wentylatora | INT | R | - | 1 | 0:Day/Dzień, 1:Night/Noc, 2:Curve/Krzywa, 3:Service/Serwis |
| 40075 | Modbus Address<br/>Adres Modbus | UDINT | RW | - | 1 | Unit Modbus slave address<br/>Adres slave urządzenia Modbus |
| 40324 | Heater Enable<br/>Włączenie grzałki | INT | RW | - | 1 | 0:Disable, 1:DHW only, 2:Heating only, 3:All |

---

## 📋 Notes / Uwagi

**🇬🇧 ENGLISH:**
- All temperature values use 0.1°C scaling (divide by 10)
- Pressure values use 0.1 bar scaling (divide by 10)  
- Percentage values use 0.1% scaling (divide by 10)
- Boolean values: 0 = False/Off, 1 = True/On
- Some registers may be manufacturer-specific variants

**🇵🇱 POLSKI:**
- Wszystkie wartości temperatury używają skali 0.1°C (dziel przez 10)
- Wartości ciśnienia używają skali 0.1 bar (dziel przez 10)
- Wartości procentowe używają skali 0.1% (dziel przez 10)  
- Wartości logiczne: 0 = Fałsz/Wył, 1 = Prawda/Wł
- Niektóre rejestry mogą być wariantami specyficznymi dla producenta