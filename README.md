# InkTime - SmartWatch Project
InkTime este un concept de ceas inteligent axat pe eficienta energetica, utilizand un display e-Paper.

## Diagrama Bloc
```
┌─────────────────────────────────────────────────────────────┐
│                   SUBSISTEM ALIMENTARE                      │
│                                                             │
│  Port USB-C ─────► USBLC6-2SC6 (Protecție ESD)              │
│                          │                                  │
│                          ▼                                  │
│  Baterie Li-Po ◄────► BQ25180 (Încărcător IC)               │
│  (Test Pads)             │                                  │
│                          ▼                                  │
│                   RT6160AWSC (Buck-Boost) ──► VCC (3.3V)    │
│                          │                      (Sistem)    │
│                          ▼                                  │
│  MAX17048 (Fuel Gauge) ──► Monitorizare prin I2C            │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                  UNITATE DE PROCESARE                       │
│                                                             │
│              nRF52840 (MCU + Bluetooth LE)                  │
│        ┌─────────────┬─────────────┬─────────────┐          │
│        │             │             │             │          │
│     Bus SPI       Bus I2C       GPIOs        Antenă RF      │
│        │             │             │             │          │
│        ▼             │             ▼             ▼          │
│  Display e-Paper     │       3x Butoane      Johanson       │
│   (J1 - 24 pin)      │      (UP, DN, ENT)    2.45GHz        │
│                      │                                      │
│        ┌─────────────┴─────────────┐                        │
│        │                           │                        │
│        ▼                           ▼                        │
│  BMA423 (Accel.)          DRV2605L (Haptic)                 │
│  (Senzor mișcare)         (Motor Vibrații)                  │
└─────────────────────────────────────────────────────────────┘
```

## Bill of Materials

| Qty | Value | Device | Package | Parts | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | - | ESP32_C6_LIBRARY_JUMPER | JUMPER_SJ | SJ1 | SMD solder JUMPER |
| 3 | 0 | CPF0201D7K68C1 | 0201 | R2, R3, R4 | 7.68k 0201 Thin Film Resistor |
| 4 | 0.1uF | GRM011R60J152KE01L | CAPC0201 | C23, C27, C34, C42 | SMD Capacitor X5R 6.3V |
| 1 | 0.1uF/50V | NRF_3_CAPACITOR_0201 | RESC0201 | EPD_C5 | Generic chip capacitor |
| 7 | 0.1uF/50V | NRF_3_CAPACITOR_0402 | RESC0402 | EPD_C6, EPD_C7, EPD_C8, EPD_C9, EPD_C10, EPD_C11, EPD_C12 | Generic chip capacitor |
| 1 | 0.47 | CPF0201D7K68C1 | 0201 | R1_EP_DR | 7.68k 0201 Resistor |
| 1 | 1.0uF | PERFECT_0402_CAP | 0402 | C15 | 0402 (1005 Metric) |
| 5 | 100nF | NRF_3_CAPACITOR_0201 | RESC0201 | C5, C7, C8, C12, C19 | Generic chip capacitor |
| 1 | 100pF | NRF_3_CAPACITOR_0201 | RESC0201 | C11 | Generic chip capacitor |
| 3 | 10K | CPF0201D7K68C1 | 0201 | R2_EP_DR, R9, R_PWR_EPD | 7.68k 0201 Resistor |
| 3 | 10k | CPF0201D7K68C1 | 0201 | R5, R7, R8 | 7.68k 0201 Resistor |
| 1 | 10uF | NRF_3_CAPACITOR_0402 | RESC0402 | C1-EP-DR | Generic chip capacitor |
| 2 | 10uF | PERFECT_0402_CAP | 0402 | C24, C39 | 0402 (1005 Metric) |
| 1 | 10uH | NRF_2_INDUCTOR_0402 | RESC0402 | L2 | Generic chip inductor |
| 4 | 12pF | NRF_3_CAPACITOR_0201 | RESC0201 | C1, C2, C17, C18 | Generic chip capacitor |
| 1 | 15nH | NRF_2_INDUCTOR_0402 | RESC0402 | L3 | Generic chip inductor |
| 2 | 1pF | NRF_3_CAPACITOR_0201 | RESC0201 | C3, C4 | Generic chip capacitor |
| 6 | 1uF | GRM011R60J152KE01L | CAPC0201 | C29, C30, C31, C32, C37, C38 | SMD Capacitor X5R 6.3V |
| 2 | 1uF/50V | NRF_3_CAPACITOR_0402 | RESC0402 | EPD_C1, EPD_C2 | Generic chip capacitor |
| 1 | 2.2 | CPF0201D7K68C1 | 0201 | R_TYPE_SEL | 7.68k 0201 Resistor |
| 3 | - | EVP-AKE31ASW | SW_EVP-AKE31A | SW_DN, SW_ENT, SW_UP | Panasonic Tactile Switch |
| 1 | 20V/4.2A | MOSFET_PCH-DMG2305UX | SOT23-3 | Q1 | P-channel MOSFET |
| 2 | 22uF | PERFECT_0402_CAP | 0402 | C25, C33 | 0402 (1005 Metric) |
| 1 | 2450AT18B100E | 2450AT18B100E | ANTC3216 | ANT1 | Antennas 2.45GHz ANTENNA |
| 1 | 3.9nH | NRF_2_INDUCTOR_0402 | RESC0402 | L1 | Generic chip inductor |
| 1 | 32.768kHz | NRF_1_XTAL_32KHZ | XTAL_3215 | X2 | Crystal Oscillator |
| 1 | 32MHz | NRF_XTAL_32MHZ | BT-XTAL_2016 | X1 | Crystal Oscillator |
| 2 | 3K3 | CPF0201D7K68C1 | 0201 | R17, R18 | 7.68k 0201 Resistor |
| 2 | 4.7uF | NRF_3_CAPACITOR_0402 | RESC0402 | C14, C43 | Generic chip capacitor |
| 1 | 4.7uF/25V | NRF_3_CAPACITOR_0402 | RESC0402 | C2-EP-DR | Generic chip capacitor |
| 3 | 4.7µF | PERFECT_0402_CAP | 0402 | C6, C20, C21 | 0402 (1005 Metric) |
| 1 | 47nF | PERFECT_0402_CAP | 0402 | C16 | 0402 (1005 Metric) |
| 1 | 503480-2400 | 503480-2400 | 5034802400 | J1 | 0.5mm FPC RA SMT 24Ckt |
| 2 | 5K1 | CPF0201D7K68C1 | 0201 | R1_USB, R2_USB | 7.68k 0201 Resistor |
| 1 | 68uH | 744043680IND | IND_4828 | L5 | Wurth Electronics Inductor |
| 1 | 820pF | NRF_3_CAPACITOR_0201 | RESC0201 | C9 | Generic chip capacitor |
| 1 | BMA421 | BMA423 | BMA423 | IC3 | Accelerometer Triaxial |
| 1 | BQ25180YBGR | BQ25180YBGR | BGA8 | IC1 | Charger IC Li-Ion/Polymer |
| 1 | DRV2605YZFR | DRV2605YZFR | BGA9 | IC2 | Haptic Driver |
| 1 | FTC252012S | MLP2016SR47 | INDC2016 | L7 | SMD / SMT Inductor 0.47uH |
| 14 | - | HECTOR_WATCH_TP | TP20R | TP_3.3V ... TP_VREG | Test pads |
| 1 | KH-TYPE-C-16P | KH-TYPE-C-16P | SMT | J4 | USB Type-C Connector |
| 1 | MAX17048G+T | MAX17048G | SON50P200 | U3 | Fuel Gauge with ModelGauge |
| 3 | MBR0530 | MBR0530 | SOD3716 | D2, D4, D5 | Schottky Diode 0.5A 30V |
| 3 | N.C. | NRF_3_CAPACITOR_0201 | RESC0201 | C10, C13, C22 | Not Connected |
| 1 | NRF52840_QF | NRF52840_QF | AQFN-74 | U1 | nRF52840 SoC |
| 1 | RT6160AWSC | RT6160AWSC | BGA15 | IC9 | Buck-Boost Regulator |
| 1 | SI1308EDL | SI1308EDL | SOT65P210

## Functionalitati Hardware

- Unitate Centrala: nRF52840 gestioneaza logica sistemului si conexiunea Bluetooth 5.4 prin arhitectura ARM Cortex-M4F.
- Afisaj: Ecranul e-Paper de 1.54" utilizeaza interfata SPI pentru a mentine imaginea afisata cu consum zero de energie.
- Senzori Miscare: Accelerometrul BMA423 comunica prin I2C pentru a detecta pasii si gesturile de activare a ecranului.
- Feedback Haptic: Driverul DRV2605L utilizeaza magistrala I2C pentru a genera efecte de vibratie precise prin motorul intern.
- Gestiune Energie: Integratul BQ25180 controleaza incarcarea bateriei prin USB-C, asigurand protectia si longevitatea celulei Li-Po.
- Stabilizare Tensiune: Regulatorul Buck-Boost RT6160A mentine un prag constant de 3.3V necesar functionarii stabile a componentelor.
- Monitorizare Baterie: Cipul MAX17048 raporteaza prin I2C nivelul de incarcare (SOC%) folosind algoritmi de masurare fara rezistor de sunt.
- Eficienta: Combinatia dintre MCU-ul ultra-low-power si display-ul e-Paper permite o autonomie estimata de peste 60 de zile.

## Configuratia pinilor nRF52840

- Bus SPI (P0.11-P0.15): Folosit pentru Display-ul e-Paper deoarece asigura latimea de banda mare necesara pentru transferul rapid al bufferului de imagine.
- Bus I2C (P0.26, P0.27): Conecteaza senzorii (BMA423, MAX17048) si driverele (DRV2605, BQ25180) pe aceleasi doua fire pentru a minimiza numarul de trasee pe PCB.
- Pini Butoane (P0.02, P0.03, P0.28): Alocati ca intrari digitale cu intreruperi (GPIOTE) pentru a permite trezirea instanta a ceasului din modul de consum redus (Deep Sleep).
- Pin Busy Display (P0.16): Intrare digitala care permite MCU-ului sa astepte pana cand ecranul termina procesul fizic de refresh inainte de a trimite noi date.
- Pin Interrupt BMA423 (P0.19): Conectat la MCU pentru a semnaliza detectia miscarii (wrist-tilt) fara ca procesorul sa interogheze constant senzorul, economisind energie.
- Pin Enable Haptic (P0.20): Pin de control rapid pentru driverul DRV2605L, utilizat pentru a declansa secventele de vibratii sincronizate cu notificarile.
- Pini Cristal 32MHz (XC1, XC2): Pini dedicati pentru oscilatorul extern de mare precizie, critic pentru functionarea corecta a radioului Bluetooth Low Energy.
- Pini Cristal 32.768kHz (P0.00, P0.01): Folositi pentru ceasul de timp real (RTC) care asigura masurarea precisa a orei cu un consum de curent de ordinul microamperilor.
- Pini SWD (SWDIO, SWDCLK): Interfata dedicata de programare si debug, absolut necesara pentru incarcarea firmware-ului si monitorizarea variabilelor in timp real.
- Pin Reset (P0.18): Configurat ca intrare de reset hardware pentru a permite repornirea sigura a sistemului in cazul unui blocaj software (Watchdog/Manual).

## Decizii luate
- Am acceptat erorile de overlap pe pinii procesorului cauzate de via-uri deoarece nu am gasit o alta metoda de a trage cablu pana acolo.
- Am acceptat erorile de copper clearence pentru ca orice alta solutie ar fi ingreunat si mai tare asezarea cablurilor.
- Am acceptat erorile de airwire intrucat gasirea unui traseu intre 2 acei pini ar fi provocat mai multe erori de alte tipuri
