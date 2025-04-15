# OpenBook – Proiect TSC 2025

## Descriere generală

**OpenBook** este un dispozitiv portabil de tip e-book reader, conceput ca soluție open-source, eficientă energetic și scalabilă. Acesta se bazează pe microcontrolerul **ESP32-C6-WROOM**, având ca funcții principale afișarea de conținut pe un ecran e-paper și monitorizarea parametrilor de mediu (temperatură, umiditate, CO2, particule).

Dispozitivul permite salvarea datelor colectate pe un card microSD și oferă control prin intermediul unor butoane fizice.

## Diagramă bloc
![Pollution Tracker](https://github.com/user-attachments/assets/ec750db2-4d4a-47b5-96d8-3d568c1b4d18)


## Funcționalitate hardware

Dispozitivul este structurat în jurul modulului **ESP32-C3-WROOM**, care gestionează toate interfețele de comunicare cu componentele externe.

### ESP32-C3-WROOM
- Microcontroler principal cu suport pentru **Wi-Fi** și **BLE**
- Interfețe: **SPI**, **I2C**, **UART**
- Alimentare: **3.3V** prin LDO

### Sistem de alimentare
- **USB-C** pentru alimentare externă și comunicare
- **MCP73832** pentru managementul încărcării bateriei Li-Po
- **LDO 3.3V** pentru alimentarea logicii
- **DC-DC 5V** pentru alimentarea senzorilor PM și CO2

### Senzori
- **BME680** (I2C, 3.3V) - temperatură, umiditate, gaze
- **MH-Z19B** (UART, 5V) - CO2
- **PMSA003** (UART, 5V) - particule fine (PM2.5)

### Ecran
- **E-paper monocrom 1.5''** cu rezoluție 200x200 px
- Interfață SPI comună cu cardul SD

### Card SD
- Slot microSD pentru stocarea de date/text
- Interfață SPI

### Butoane
- 3 butoane tactile conectate la pinii GPIO pentru interacțiune cu utilizatorul

## Bill of Materials (BOM)

| Part | Device | Datasheet |
|------|--------|-----------|
| CHG_LED | ADAFRUIT_LEDCHIP-LED0603 | [ADAFRUIT_LEDCHIP-LED0603](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) |
| SJ1 | SJ | [SJ](https://grabcad.com/library/solder-jumpers-1) |
| EPD_C5 | EAGLE-LTSPICE_CC0402 | [EAGLE-LTSPICE_CC0402](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| R3 | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | (https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| R1_PWRUSB | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | (https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL) |
| C4_USB | EAGLE-LTSPICE_CC0402 | [EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| C1, C2, C6, C8, C9, C10, C_DELAY | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| C3 | RCL_CPOL-EUCT3528 | [RCL_CPOL-EUCT3528](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| R1, R1_PINH, R1_PINH1, R2_PINH, R2_PINH1, R4, R5, R6, R7, R8, R9, R10, R_BOOT, R_CHANGE, R_CL1, R_RESET | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| C7 | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| J4 | 112A-TAAR-R03_ATTEND | [112A-TAAR-R03_ATTEND](https://store.comet.srl.ro/Catalogue/Product/43497/) |
| R_CAPACITOR | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| C5 | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| EPD_C6, EPD_C7, EPD_C8, EPD_C9, EPD_C10, EPD_C11, EPD_C12 | EAGLE-LTSPICE_CC0402 | [EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| EPD_C1, EPD_C2 | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| R2 | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| R1_BAT | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| Q1, Q2 | ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_PCH-DMG2305UX-7 | [ESP32_WROVER_SPARKFUN-DISCRETESEMI_MOSFET_PCH-DMG2305UX-7](https://componentsearchengine.com/part-view/DMG2305UX-7/Diodes%20Incorporated) |
| R2_BAT | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| C5_USB | EAGLE-LTSPICE_CC0402 | [EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| C1_BAT, C1_BAT1, C1_BAT2, C2_BAT | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| C4 | ESP32_WROVER_EAGLE-LTSPICE_CC0402 | [ESP32_WROVER_EAGLE-LTSPICE_CC0402](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |
| R2-USB, R2-USB1 | ESP32_WROVER_EAGLE-LTSPICE_RR0402 | [ESP32_WROVER_EAGLE-LTSPICE_RR0402](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| L1 | 744043680IND_4828-WE-TPC_WRE | [744043680IND_4828-WE-TPC_WRE](https://eu.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) |
| IC1 | BD5229G-TR | [BD5229G-TR](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) |
| SENSOR2 | ESP32_WROVER_BME680_BME680 | [ESP32_WROVER_BME680_BME680](https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home) |
| BUTTON_CUSYOMV1 |BUTTON_CUSYOMV1 | [BUTTON_CUSYOMV1](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) |
| C10_SUPERCAP | CPH3225A | [CPH3225A](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=snap) |
| U3 | DS3231SN# | [DS3231SN#](https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=snap) |
| U2 | ESP32-C6-WROOM-1-N8 | [ESP32-C6-WROOM-1-N8](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) |
| PFMF.050.1 | ESP32C6_VARISTORCN1812 | [ESP32C6_VARISTORCN1812](https://www.mouser.co.uk/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D) |
| D2, D7 | ESP32_WROVER_AVX---SD0805S020S1R0_AVX_SD0805S020S1R0_0_0AVX_SD0805S020S1R0_0_0 | [ESP32_WROVER_AVX---SD0805S020S1R0_AVX_SD0805S020S1R0_0_0AVX_SD0805S020S1R0_0_0](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) |
| U5 | ESP32_WROVER_SPARKFUN-IC-POWER_MCP73831 | [ESP32-C6-WROOM-1-N8](https://componentsearchengine.com/part-view/MCP73831T-2ATI%2FOT/Microchip) |
| J1 | FH34SRJ-24S-0.5SH_99_ | [FH34SRJ-24S-0.5SH_99_](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |
| U4 | MAX17048G+T10 | [MAX17048G+T10](https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=snap) |
| D3, D4, D5 | MBR0530 | [MBR0530](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=snap) |
| D6, D8, D9, D10, D11, D12 | PGB1010603MR | [PGB1010603MR](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=snap) |
| J3 | QWIIC_CONNECTORJS-1MM | [QWIIC_CONNECTORJS-1MM](https://www.snapeda.com/parts/PRT-14417/SparkFun%20Electronics/view-part/?ref=search&t=qwiic) |
| J2 | SAMACSYS_PARTS_USB4110-GF-A | (https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY) |
| Q3 | SI1308EDL-T1-GE3 | [SI1308EDL-T1-GE3](https://componentsearchengine.com/part-view/SI1308EDL-T1-GE3/Vishay) |
| TP1, TP2, TP3, TP4, TP5, TP6, TP7, TP8, TP9, TP10, TP11, TP12, TP13, TP14, TP15, TP16, TP17 | TPTP20R | [facute de mine] |
| D1 | USBLC6-2SC6Y | [USBLC6-2SC6Y](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=snap) |
| U1 | W25Q512JVEIQ | [W25Q512JVEIQ](https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=snap) |
| IC4 | XC6220A331MR-G | [XC6220A331MR-G](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) |

## Alocare pini ESP32-C3

| Pin ESP32-C3 | Componentă  | Funcție / Motiv                     |
|--------------|-------------|-------------------------------------|
| GPIO1        | BME680      | I2C - SDA                           |
| GPIO2        | BME680      | I2C - SCL                           |
| GPIO3        | PMSA003     | UART RX pentru senzor PM           |
| GPIO4        | SD Card     | SPI Chip Select (CS)               |
| GPIO5        | E-Ink       | Data/Command                       |
| GPIO6        | E-Ink & SD  | SPI Clock (SCK)                    |
| GPIO7        | E-Ink & SD  | SPI MOSI (date)                    |
| GPIO8        | Buton 1     | Control meniu / pagină             |
| GPIO9        | Buton 2     | Control meniu / pagină             |
| GPIO10       | E-Ink       | SPI Chip Select (CS)               |
| GPIO11       | Flash ext.  | CS rezervat, neutilizat momentan   |
| GPIO12       | USB         | USB D-                             |
| GPIO13       | USB         | USB D+                             |
| GPIO18       | MH-Z19B     | UART TX pentru senzor CO2          |
| GPIO19       | Buton 3     | Confirmare / acțiune suplimentară  |

