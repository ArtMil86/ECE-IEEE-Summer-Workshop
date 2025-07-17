# 📡 Lesson 3 — Ultrasonic Sensor (Keyestudio 4WD BT Car)

## 🎯 Objectives
- Understand how an **ultrasonic sensor** measures distance using sound waves.
- Control the **Trigger** and read from the **Echo** pin to calculate time-of-flight.
- Convert the pulse duration into **centimeters** and **inches**.
- Print the result to the **Serial Monitor**.

---

## 🧠 Concepts

- The **HC-SR04 ultrasonic sensor** sends a high-frequency sound pulse and listens for its echo.
- Time taken for the echo to return is used to calculate distance.
- The Arduino uses `pulseIn()` to measure the echo duration in microseconds.

---

## 🔌 Wiring Instructions

| Ultrasonic Sensor Pin | Arduino Pin |
|------------------------|-------------|
| VCC                   | 5V          |
| GND                   | GND         |
| TRIG                  | 12          |
| ECHO                  | 13          |

📌 **Tip**: Make sure echo pin is on a digital input pin that can use `pulseIn()`.

---

## ✅ Your challenge:
  - Set up the Trig and Echo pins in setup()
  - Write the trigger pulse code inside loop()
---

## 💾 Arduino Code (Student Challenge Template)

```cpp

👉 Hints are provided in comments.


int trigPin = 12;  // Trigger pin
int echoPin = 13;  // Echo pin

long duration;
float cm, inches;

void setup() {
  Serial.begin(9600);  // Start Serial Monitor

  // 👉 TODO: Setup the pin modes
  // Make trigPin an OUTPUT
  // Make echoPin an INPUT
}

void loop() {
  // 👉 TODO: Write the trigger pulse code!
  // 1) Set trigPin LOW for 2 microseconds
  // 2) Set trigPin HIGH for 10 microseconds
  // 3) Set trigPin LOW again

  // Measure echo time
  duration = pulseIn(echoPin, HIGH);

  // Calculate distance
  cm = (duration / 2.0) / 29.1;
  inches = (duration / 2.0) / 74;

  // Output to Serial Monitor
  Serial.print("Distance: ");
  Serial.print(cm);
  Serial.print(" cm\t");
  Serial.print(inches);
  Serial.println(" inches");

  delay(500);
}
