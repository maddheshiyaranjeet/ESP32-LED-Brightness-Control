# ESP32-LED-Brightness-Control
Control LED brightness using a potentiometer and ESP32 by reading analog input and generating PWM output.

 
# Project Title

A brief description of what this project does and who it's for

# ESP32 LED Brightness Control Using Potentiometer

Control the brightness of an LED using a potentiometer and an ESP32. The potentiometer value is read through the ESP32's ADC and mapped to a PWM signal that adjusts the LED brightness.

## 📌 Features

- Read analog input from a potentiometer
- Control LED brightness using PWM
- Display potentiometer and brightness values in the Serial Monitor
- Simple beginner-friendly ESP32 project

---

## 🛠️ Components Required

- ESP32 Development Board
- 10kΩ Potentiometer
- LED
- 220Ω Resistor (recommended for LED)
- Breadboard
- Jumper Wires
- USB Cable

---

## 🔌 Circuit Diagram

> Connect the components as shown below.

![Circuit Diagram](circuit.png)

### Connections

| Component | ESP32 Pin |
|-----------|------------|
| Potentiometer VCC | 3.3V |
| Potentiometer GND | GND |
| Potentiometer Signal | GPIO34 |
| LED Anode (+) | GPIO32 |
| LED Cathode (-) | GND (through 220Ω resistor) |

---

## 📂 Project Structure

```
ESP32-LED-Brightness-Control/
│── ESP32_LED_Brightness_Control.ino
│── circuit.png
└── README.md
```

---

## 💻 Code

```cpp
const int potPin = 34;
const int ledPin = 32;

void setup() {
  Serial.begin(115200);

  // Configure PWM
  ledcAttach(ledPin, 5000, 8);
}

void loop() {
  int potValue = analogRead(potPin);

  int brightness = map(potValue, 0, 4095, 0, 255);

  ledcWrite(ledPin, brightness);

  Serial.print("Potentiometer = ");
  Serial.print(potValue);
  Serial.print("  Brightness = ");
  Serial.println(brightness);

  delay(10);
}
```

---

## ▶️ How It Works

1. The ESP32 reads the potentiometer value using **GPIO34**.
2. The ADC converts the voltage into a value between **0 and 4095**.
3. The `map()` function converts this value into a PWM range of **0–255**.
4. PWM is generated on **GPIO32**, changing the LED brightness.
5. The current potentiometer value and brightness level are displayed in the Serial Monitor.

---

## 📊 Serial Monitor Output

```
Potentiometer = 0     Brightness = 0
Potentiometer = 1050  Brightness = 65
Potentiometer = 2100  Brightness = 130
Potentiometer = 3200  Brightness = 199
Potentiometer = 4095  Brightness = 255
```

---

## ⚙️ PWM Configuration

| Parameter | Value |
|-----------|-------|
| PWM Frequency | 5000 Hz |
| PWM Resolution | 8-bit |
| PWM Range | 0–255 |

---

## 🚀 Getting Started

1. Install the **Arduino IDE**.
2. Install the **ESP32 Board Package** from the Boards Manager.
3. Connect the ESP32 to your computer.
4. Open the `.ino` file.
5. Select your ESP32 board and COM port.
6. Upload the code.
7. Open the Serial Monitor at **115200 baud**.
8. Rotate the potentiometer to control the LED brightness.

---

## 📖 Explanation

- `analogRead()` reads the potentiometer voltage.
- `map()` converts ADC values to PWM values.
- `ledcAttach()` configures the ESP32 PWM output.
- `ledcWrite()` changes the LED brightness.

---

## 📝 Future Improvements

- Add OLED display to show brightness percentage.
- Control RGB LEDs.
- Create a web interface using ESP32 Wi-Fi.
- Add MQTT or Bluetooth control.
- Smooth brightness transitions using filtering.

---

## 📜 License

This project is open-source and available under the **MIT License**.

---

## 👨‍💻 Author

**Your Name**

If you found this project helpful, consider giving the repository a ⭐ on GitHub!
