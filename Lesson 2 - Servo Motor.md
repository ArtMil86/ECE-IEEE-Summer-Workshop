# 🧭 Lesson 2 — Servo Motor (Keyestudio 4WD BT Car)

## 🎯 Objectives
- Use the `Servo` library to control a standard hobby servo motor.
- Connect the servo to pin `9` and control its angle with `write()`.
- Learn how `delay()` affects movement speed.
- Practice **for-loop** logic for sweeping behavior.

---

## 🧠 Concepts

- Servos rotate to a **specific angle** between 0° and 180°.
- The angle is set using `myServo.write(angle)`.
- You can use `for` loops to **sweep** the servo gradually.
- Changing the `delay()` affects **speed of rotation**.

---

## 🔌 Wiring Instructions

| Servo Wire     | Connect To  |
|----------------|-------------|
| Orange/White   | **Pin 9**   |
| Red (VCC)      | **5V**      |
| Brown/Black    | **GND**     |

📌 **Important**: Always power the servo from 5V and make sure GND is shared with the Arduino.

---
## Goal: 

✅ Uses Servo library.

✅ Pin 9 = Servo signal.

✅ Sweeps servo back and forth.

✅ Students: change delay() to see how speed changes.

---
## 💾 Arduino Code
```cpp
#include <Servo.h>

Servo myServo;  // Create Servo object

void setup() {
  myServo.attach(9);  // Attach servo signal wire to pin 9
}

void loop() {
  // Sweep from 0 to 180 degrees
  for (int angle = 0; angle <= 180; angle++) {
    myServo.write(angle);   // Set servo to angle
    delay(40);              // Smaller delay = faster sweep
  }

  // Challenge: How would you continue this to rotate back to 0
  // without "jumping" suddenly? Try adding another for-loop.
}
