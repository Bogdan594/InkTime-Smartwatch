# InkTime - SmartWatch Project
InkTime este un concept de ceas inteligent axat pe eficiență energetica, utilizand un display e-Paper.

## Diagrama Bloc
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
