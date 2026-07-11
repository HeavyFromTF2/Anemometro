# Winduino: Ultrasonic IoT Anemometer

An open-source, low-cost ultrasonic anemometer built with an **Arduino Nano RP2040 Connect** to measure wind speed through Time-of-Flight (TOF) data. The system features real-time environmental compensation via a **BME280** sensor and connects seamlessly to the **Arduino IoT Cloud** for remote monitoring.

---

## 🚀 Features

* **Ultrasonic Wind Measurement:** Uses two HC-SR04 sensors facing each other to calculate wind speed based on sound wave propagation time differences.
* **Dynamic Environmental Compensation:** Real-time updates for temperature, relative humidity, and barometric pressure using a BME280 sensor.
* **Intelligent Noise Filtering:** Implements custom software thresholding to eliminate baseline sensor fluctuations and stabilize readings.
* **Beaufort Scale Classification:** Automatically translates wind velocities into intuitive categories (e.g., "Calm", "Moderate Breeze").
* **IoT Connected:** Publishes telemetry instantly to the Arduino IoT Cloud for live chart tracking and data historical logging.

---

## 📸 System Overview

### Physical Build
The prototype features a 30 cm rectangular wooden structure designed to guarantee exact alignment between the acoustic axes of the ultrasonic transducers.

<img width="2040" height="1536" alt="Project1" src="https://github.com/user-attachments/assets/5466ebc2-6357-4c71-9266-65e5067c9f28" />
<img width="2040" height="1536" alt="Project2" src="https://github.com/user-attachments/assets/2d5d0946-e11e-444d-809d-2ef41fde29bc" />

### IoT Cloud Dashboard
Telemetry data (Temperature, Humidity, Pressure, Wind Speed, and Beaufort Category) is visualized remotely via a customized web dashboard.

<img width="1389" height="760" alt="Dashboard" src="https://github.com/user-attachments/assets/94d8c4a0-b1c0-4e24-960e-a7041b5d3847" />

---

## ⚙️ Mathematical Model

Wind speed ($v$) is isolated and computed from the structural distance ($d = 0.3\text{ m}$) and the respective travel times using the following expression:

$$v = \frac{d}{2} \times \left( \frac{1}{t_{1\_2s}} - \frac{1}{t_{2\_1s}} \right)$$

Where:
* $d$ is the strict distance spacing between the sensors ($30\text{ cm}$).
* $t_{1\_2s}$ is the time-of-flight from Sensor 1 to Sensor 2.
* $t_{2\_1s}$ is the time-of-flight from Sensor 2 to Sensor 1.

The hardware additionally computes a reference thermodynamic speed of sound adjusted dynamically by temperature ($T$ in Kelvin):

$$c = \sqrt{\frac{\gamma \cdot R \cdot T}{M}}$$

---

## 🛠️ Hardware & Pin Configuration

### Components
* **Microcontroller:** Arduino Nano RP2040 Connect
* **Ultrasonic Sensors:** 2x HC-SR04
* **Environmental Sensor:** Bosch BME280 (I2C)

### Wiring Schematic
* **HC-SR04 Sensor 1:** Trig ➡️ Pin 9  | Echo ➡️ Pin 10
* **HC-SR04 Sensor 2:** Trig ➡️ Pin 11 | Echo ➡️ Pin 12
* **BME280 Sensor:** Connected via standard I2C (SDA/SCL)

---

## 📊 Evaluation & Limitations

* **Airflow Stability:** The system performs exceptionally well under uniform wind conditions. Testing under localized turbulent flows (e.g., utilizing a hair dryer) revealed a transient calculation noise floor variation of 1–2 m/s.
* **Sensor Range Constraints:** The standard HC-SR04 has an operational echo envelope between 2 cm and 400 cm, bounding maximum detectable high-speed boundaries.
* **Future Enhancements:** Next steps include introducing an automated hardware zero-calibration routine and moving to a 4-sensor multi-axial configuration for detailed 2D/3D wind vector modeling.

---

## 🎓 Acknowledgments

Special thanks to **Professor Nuno Pereira** for guidance throughout development, as well as the active community contributors on the **Arduino Forum**.
