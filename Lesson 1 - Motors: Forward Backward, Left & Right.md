# 🚗 Lesson 1 — Motor Control (4WD Arduino Robot)

## 🎯 Objectives

* Understand what a motor is and how it moves the robot.
* Learn how 4 motors are driven using 2 control channels via a motor driver (L298P).
* Understand `digitalWrite()` for direction and `analogWrite()` for speed.
* Practice writing modular code to drive the robot forward.
* Complete a challenge to reverse, turn left, and turn right.

---

## 🧠 What Is a Motor?
<img width="631" height="480" alt="image" src="https://github.com/user-attachments/assets/d728225c-4062-40ec-b4a9-225bc5d6d70f" />

A motor converts electrical energy into **motion**.
Your robot has **4 wheels**, but only **2 motor channels** — one per side:

* **Left side (M1)** → controls both left wheels
* **Right side (M2)** → controls both right wheels

Each motor channel uses:

* A **Direction pin**: decides spin direction (clockwise or counterclockwise)
* A **Speed pin (PWM)**: controls how fast the motor spins (0 = off, 255 = max)

---

## 🧰 The Motor Driver (L298P)

The **motor driver** allows the Arduino to safely control high-power motors using low-power signals:

* `HIGH` = 5V (ON)
* `LOW` = 0V (OFF)

PWM = **Pulse Width Modulation**, a way of simulating variable power using fast ON/OFF pulses.

---

## 🔌 Pinout Table

| Channel | Controls          | Direction Pin | Speed Pin (PWM) |
| ------- | ----------------- | ------------- | --------------- |
| M1      | Left Wheels (x2)  | D4            | D5              |
| M2      | Right Wheels (x2) | D2            | D6              |

⚠️ Although you have 4 motors total, they are **grouped in pairs** (left and right) — so you only need 2 control channels.

---

## 🖼️ Embedding Robot Images

Place images like wiring diagrams into your `/images/` folder on GitHub and embed like this:

```markdown
![Motor Diagram](/images/motor_diagram_1.png)
![Wiring Diagram](/images/motor_driver_wiring.png)
![Pin Map](/images/pin_connection_labeled.png)
```

---

## 🧑‍💻 Basic Arduino Program Structure

Every Arduino sketch has two core functions:

```cpp
void setup() {
  // Runs once at the beginning
}

void loop() {
  // Repeats forever after setup runs
}
```

---

## 🔧 Step 1: Setup Motor Pins

Start by defining which pins control each motor side:

```cpp
#define M1_DIR 4  // Direction pin for Left motors
#define M1_SPD 5  // Speed (PWM) pin for Left motors

#define M2_DIR 2  // Direction pin for Right motors
#define M2_SPD 6  // Speed (PWM) pin for Right motors
```

Then, in `setup()`, configure them as OUTPUTs:

```cpp
void setup() {
  pinMode(M1_DIR, OUTPUT); pinMode(M1_SPD, OUTPUT);
  pinMode(M2_DIR, OUTPUT); pinMode(M2_SPD, OUTPUT);
  stopAll(); // Optional: stop everything at start
}
```

📤 Upload this code to your robot to test pin setup.

---

## ⚙️ Understanding the Code Functions

* **`pinMode(pin, OUTPUT)`** tells Arduino to send signals *out* on a pin. Needed for motor control.
* **`digitalWrite(pin, HIGH/LOW)`** sets the **direction** of the motor (forward or reverse).
* **`analogWrite(pin, value)`** sets the **speed** (0–255) using PWM (Pulse Width Modulation).

---

## 🚗 Step 2: Drive Forward (Example)

This makes both sides spin forward for 2 seconds:

```cpp
void loop() {
  digitalWrite(M1_DIR, HIGH);   // try HIGH or LOW depending on wiring
  analogWrite(M1_SPD, 200);     // speed (0–255)

  digitalWrite(M2_DIR, HIGH);   // try HIGH or LOW
  analogWrite(M2_SPD, 200);

  delay(2000);                  // move for 2 seconds

  stopAll();                    // then stop
  delay(1000);
}
```

🧪 Try changing HIGH and LOW for direction pins — your wiring may vary.

📤 Upload and run this code to see the robot move forward!

---

## 💻 Student Template Code

This is the starter code. Only `driveForward()` is included — others are up to you!

```cpp
#define M1_DIR 4
#define M1_SPD 5
#define M2_DIR 2
#define M2_SPD 6

void setup() {
  pinMode(M1_DIR, OUTPUT); pinMode(M1_SPD, OUTPUT);
  pinMode(M2_DIR, OUTPUT); pinMode(M2_SPD, OUTPUT);
  stopAll();
}

void loop() {
  driveForward();     // ✅ Try this first
  delay(2000);

  stopAll();          // Always stop after motion
  delay(2000);

  // 🧠 Challenge: Uncomment and complete these after testing forward
  // driveBackward();
  // turnLeft();
  // turnRight();
}

// === MOVEMENT FUNCTIONS ===

void driveForward() {
  // 💡 Hint: Set both motors to spin in same direction
  digitalWrite(M1_DIR, HIGH);
  analogWrite(M1_SPD, 200);

  digitalWrite(M2_DIR, HIGH);
  analogWrite(M2_SPD, 200);
}

// 🔧 Your Challenge: Write these yourself!

void driveBackward() {
  // 🔁 Hint: Flip direction pins
}

void turnLeft() {
  // ⬅️ Hint: Stop left, spin right
}

void turnRight() {
  // ➡️ Hint: Stop right, spin left
}

void stopAll() {
  analogWrite(M1_SPD, 0);
  analogWrite(M2_SPD, 0);
}
```

📤 Upload this code and test it after completing your custom functions!

---

## 🎯 Student Challenges

Once you've tested `driveForward()`, try these:

* 🔁 Make the robot reverse using `driveBackward()`
* ⬅️➡️ Make it turn left and right using just one side
* ⚡ Try speeds like 100, 150, and 255 to compare
* 🧠 Bonus: Turn right **backwards**, turn left **backwards**, then move on

⏳ Don't spend too long on this! Move on to Lesson 2 if you've mastered it.

---

## 📦 Quick Reference Table

| Concept    | Function              | Description                     |
| ---------- | --------------------- | ------------------------------- |
| Setup pin  | `pinMode()`           | Tells Arduino the pin is OUTPUT |
| Set spin   | `digitalWrite()`      | HIGH or LOW for direction       |
| Set speed  | `analogWrite()`       | PWM speed (0–255)               |
| Wait time  | `delay()`             | Pause program execution         |
| Stop motor | `analogWrite(..., 0)` | Sets speed to 0 (off)           |

---

👉 [Next: Lesson 2 - Servo Motor Basics](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%202%20-%20Servo%20Motor.md)
