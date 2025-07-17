# 📘 Lesson 1 - Motors: Forward, Backward, Left & Right

## 🎯 Objective
- Understand how to control motor **direction** using digital pins.
- Learn how to use **PWM (Pulse Width Modulation)** to control motor **speed**.
- Practice Arduino code that allows the robot to move **forward**, **backward**, and **turn left/right**.

---

## 🧠 Concepts

- Each motor has two direction pins (`motorA1`, `motorA2`).
- Speed is controlled via `analogWrite()` on a **PWM-enabled pin** (like `speedPinA`).
- Combining the correct logic levels allows us to control motion patterns.

---

## 🔌 Wiring

| Motor | Direction Pin 1 | Direction Pin 2 | PWM Speed Pin |
|-------|------------------|------------------|----------------|
| A     | Pin 2           | Pin 3           | Pin 5         |
| B     | Pin 4           | Pin 7           | Pin 6         |

Make sure to connect the motor driver to the appropriate pins and that the PWM pins support `analogWrite()`.

---

## 💾 Arduino Code

```cpp
/*
Keyestudio 4WD BT Car V2.0
Lesson 1 — Motors
STUDENT TEMPLATE

✅ This robot has 2 motor channels:
  M1 = Left side wheels
  M2 = Right side wheels

👉 Each side has:
   - 1 pin for direction (DIR)
   - 1 pin for speed (SPD)

👉 Students: test HIGH or LOW to figure out forward/backward.
👉 Use analogWrite() for speed control.
*/

// === MOTOR 1 (LEFT SIDE) ===
#define M1_DIR 4   // Direction pin for Left side
#define M1_SPD 5   // Speed pin (PWM) for Left side

// === MOTOR 2 (RIGHT SIDE) ===
#define M2_DIR 2   // Direction pin for Right side
#define M2_SPD 6   // Speed pin (PWM) for Right side

void setup() {
  pinMode(M1_DIR, OUTPUT); pinMode(M1_SPD, OUTPUT);
  pinMode(M2_DIR, OUTPUT); pinMode(M2_SPD, OUTPUT);

  stopAll();
}

void loop() {
  driveForward();
  delay(2000);

 /* driveBackward();
  delay(2000);

  turnLeft();
  delay(2000);

  turnRight();
  delay(2000);
*/
  stopAll();
  delay(2000); 
}

// === MOVEMENT FUNCTIONS ===

void driveForward() {
  // Left wheels: test DIR for CW forward
  digitalWrite(M1_DIR, /* HIGH or LOW*/);

  // Right wheels: test DIR for CW forward
  digitalWrite(M2_DIR, /*HIGH or LOW*/);

  analogWrite(M1_SPD, 150);
  analogWrite(M2_SPD, 150);
}

void driveBackward() {
  // Flip both
  digitalWrite(M1_DIR, /*HIGH or LOW*/);
  digitalWrite(M2_DIR, /*HIGH or LOW*/);

  analogWrite(M1_SPD, 150);
  analogWrite(M2_SPD, 150);
}

void turnLeft() {
  // Right wheels move forward, left wheels stop
  analogWrite(M1_SPD, 0);
  digitalWrite(M2_DIR, /*HIGH or LOW*/);
  analogWrite(M2_SPD, 150);
}

void turnRight() {
  // Left wheels move forward, right wheels stop
  analogWrite(M2_SPD, 0);
  digitalWrite(M1_DIR, /*HIGH or LOW*/);
  analogWrite(M1_SPD, 150);
}

void stopAll() {
  analogWrite(M1_SPD, 0);
  analogWrite(M2_SPD, 0);
}
