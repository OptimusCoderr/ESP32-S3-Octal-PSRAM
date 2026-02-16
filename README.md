# ESP32-S3-Octal-PSRAM

![1](https://github.com/OptimusCoderr/ESP32-S3-Octal-PSRAM/blob/0104eaba3bb5c9bc84f64f7ac565f98f2a447b63/images/3d.png)
![2](https://github.com/OptimusCoderr/ESP32-S3-Octal-PSRAM/blob/0104eaba3bb5c9bc84f64f7ac565f98f2a447b63/images/layer1sig.png)
![3](https://github.com/OptimusCoderr/ESP32-S3-Octal-PSRAM/blob/0104eaba3bb5c9bc84f64f7ac565f98f2a447b63/images/layer2gnd.png)
![4](https://github.com/OptimusCoderr/ESP32-S3-Octal-PSRAM/blob/0104eaba3bb5c9bc84f64f7ac565f98f2a447b63/images/layer3pwr.png)
![5](https://github.com/OptimusCoderr/ESP32-S3-Octal-PSRAM/blob/0104eaba3bb5c9bc84f64f7ac565f98f2a447b63/images/layer4sig_gnd.png)

**ESP32-S3-Octal-PSRAM** is an advanced development board centered around the **ESP32-S3R16V**, designed specifically for high-bandwidth data processing and precision analog sensing. This project pushes the limits of the S3's **16MB Octal PSRAM** by implementing professional-grade layout techniques to ensure stability and low noise floors.

## 🚀 Key Hardware Features

* **MCU:** ESP32-S3R16V (Octal PSRAM @ 1.8V).
* **Precision ADC:** TI **ADS1232** 24-bit Bridge Sensor ADC for ultra-low-noise weight measurements.
* **Motion Tracking:** **LSM6DSR** High-performance 6-axis IMU.
* **External Display:** Dedicated UART interface for **Nextion HMI** integration.
* **External RF:** Removed PCB antenna in favor of a **controlled-impedance path** to a U.FL connector to minimize EMI near sensitive analog traces.

## 🛠 Advanced Engineering Highlights

### Power Integrity (PI) & Decoupling

To handle the high-speed switching transients of the 16MB Octal PSRAM, I implemented a **bottom-side decoupling strategy**:

* **Minimal Loop Inductance:** Capacitors are placed directly on the bottom layer, centered under the MCU power pads.
* **Hybrid Capacitor Array:** Utilizes 0201 capacitors for DC bias stability and 0201 high-frequency bypass caps to maintain a flat impedance profile across the MHz/GHz spectrum.

### Signal Integrity (SI) & Fan-out

* **QFN-56 Fan-out:** Engineered a custom fan-out strategy to isolate the **1.8V Octal PSRAM bus** from the **3.3V analog frontend**.
* **Clock Management:** Integrated a **4.9152 MHz crystal** with an optimized load capacitance circuit () to achieve 100dB rejection of 50Hz/60Hz noise for the ADC.
* **RF Optimization:** By removing the on-board antenna, I reduced the risk of RF interference leaking into the high-gain load cell signals.

## 📋 Pin Mapping Summary

| Peripheral | Function | GPIO | Notes |
| --- | --- | --- | --- |
| **ADS1232** | SCLK / DOUT | 12 / 10 | Shared SPI Clock |
| **LSM6DSR** | SCL / SDA / SDO | 12 / 13 / 14 | High-speed Motion Bus |
| **Nextion** | TX / RX | 43 / 44 | Primary UART |
| **Boot/Reset** | GPIO 0 / EN | 0 / EN | Dedicated HW Buttons |
| **PSRAM VDD** | VDD_SPI | 45 | **Hardwired High (1.8V Safety)** |


## 🤝 Contributing & Learning

This project is part of my journey into advanced PCB design. While I am still learning the nuances of high-speed hardware, I am documenting every step—from **BGA-style fan-outs** to **RC delay reset circuits**.

Feedback from the hardware community is always welcome!

---
