# Winduino: Ultrasonic IoT Anemometer

[cite_start]An open-source, low-cost ultrasonic anemometer built with an **Arduino Nano RP2040 Connect** to measure wind speed through Time-of-Flight (TOF) data[cite: 9, 10]. [cite_start]The system features real-time environmental compensation via a **BME280** sensor and connects seamlessly to the **Arduino IoT Cloud** for remote monitoring[cite: 9, 12].

---

## 🚀 Features

* [cite_start]**Ultrasonic Wind Measurement:** Uses two HC-SR04 sensors facing each other to calculate wind speed based on sound wave propagation time differences[cite: 9, 19].
* [cite_start]**Dynamic Environmental Compensation:** Real-time updates for temperature, relative humidity, and barometric pressure using a BME280 sensor[cite: 21, 30].
* [cite_start]**Intelligent Noise Filtering:** Implements custom software thresholding to eliminate baseline sensor fluctuations and stabilize readings[cite: 31, 32].
* [cite_start]**Beaufort Scale Classification:** Automatically translates wind velocities into intuitive categories (e.g., "Calm", "Moderate Breeze")[cite: 10, 22].
* [cite_start]**IoT Connected:** Publishes telemetry instantly to the Arduino IoT Cloud for live chart tracking and data historical logging[cite: 23, 24].

---

## 📸 System Overview

### Physical Build
[cite_start]The prototype features a 30 cm rectangular wooden structure designed to guarantee exact alignment between the acoustic axes of the ultrasonic transducers[cite: 29, 60].

![Project Structure]<img width="2040" height="1536" alt="Project1" src="https://github.com/user-attachments/assets/ce121ccc-3df4-4652-8c22-e3308e56d996" />

![Project Structure2]<img width="2040" height="1536" alt="Project2" src="https://github.com/user-attachments/assets/bad36758-7677-4d78-9316-b4fcf824ba5c" />

### IoT Cloud Dashboard
[cite_start]Telemetry data (Temperature, Humidity, Pressure, Wind Speed, and Beaufort Category) is visualized remotely via a customized web dashboard[cite: 39, 40].

![IoT Dashboard]<img width="1389" height="760" alt="Dashboard" src="https://github.com/user-attachments/assets/b524d141-e45c-4298-8006-42b33949dee1" />


---

## ⚙️ Mathematical Model

[cite_start]Wind speed ($v$) is isolated and computed from the structural distance ($d = 0.3\text{ m}$) and the respective travel times using the following expression[cite: 36, 37]:

$$v = \frac{d}{2} \times \left( \frac{1}{t_{1\_2s}} - \frac{1}{t_{2\_1s}} \right)$$

[cite_start]Where[cite: 37]:
* [cite_start]$d$ is the strict distance spacing between the sensors ($30\text{ cm}$)[cite: 37].
* [cite_start]$t_{1\_2s}$ is the time-of-flight from Sensor 1 to Sensor 2[cite: 37].
* [cite_start]$t_{2\_1s}$ is the time-of-flight from Sensor 2 to Sensor 1[cite: 37].

[cite_start]The hardware additionally computes a reference thermodynamic speed of sound adjusted dynamically by temperature ($T$ in Kelvin)[cite: 38]:

$$c = \sqrt{\frac{\gamma \cdot R \cdot T}{M}}$$

---

## 🛠️ Hardware & Pin Configuration

### Components
* [cite_start]**Microcontroller:** Arduino Nano RP2040 Connect [cite: 28]
* [cite_start]**Ultrasonic Sensors:** 2x HC-SR04 [cite: 28]
* [cite_start]**Environmental Sensor:** Bosch BME280 (I2C) [cite: 28, 30]

### Wiring Schematic
* **HC-SR04 Sensor 1:** Trig ➡️ Pin 9  | Echo ➡️ Pin 10
* **HC-SR04 Sensor 2:** Trig ➡️ Pin 11 | Echo ➡️ Pin 12
* [cite_start]**BME280 Sensor:** Connected via standard I2C (SDA/SCL) [cite: 30]

---

## 📊 Evaluation & Limitations

* [cite_start]**Airflow Stability:** The system performs exceptionally well under uniform wind conditions[cite: 45]. [cite_start]Testing under localized turbulent flows (e.g., utilizing a hair dryer) revealed a transient calculation noise floor variation of 1–2 m/s[cite: 43, 44].
* [cite_start]**Sensor Range Constraints:** The standard HC-SR04 has an operational echo envelope between 2 cm and 400 cm, bounding maximum detectable high-speed boundaries[cite: 53].
* [cite_start]**Future Enhancements:** Next steps include introducing an automated hardware zero-calibration routine and moving to a 4-sensor multi-axial configuration for detailed 2D/3D wind vector modeling[cite: 54, 61].

---

## 🎓 Acknowledgments

[cite_start]Special thanks to **Professor Nuno Pereira** for guidance throughout development, as well as the active community contributors on the **Arduino Forum**[cite: 63, 64].
