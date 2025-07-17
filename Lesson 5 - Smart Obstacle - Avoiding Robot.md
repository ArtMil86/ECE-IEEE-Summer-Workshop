# 🤖 Lesson 5 — Smart Obstacle-Avoiding Robot (Keyestudio 4WD BT Car)

## 🎯 Objectives
- Combine motors, ultrasonic sensor, servo, and LED matrix into one smart robot.
- Continuously **scan** ahead using a servo-mounted ultrasonic sensor.
- If an **obstacle is detected**, **stop** and **display a warning face**.
- Otherwise, **drive forward** automatically.

---

## 🧠 Concepts

- **Ultrasonic sensor** sweeps left to right using a servo.
- Distance is measured using `pulseIn()` and compared to a **safety threshold**.
- **If** the distance is too short: stop motors and show an LED warning.
- Use **modular code** with functions like `driveForward()` and `stopMotors()`.

---

## 🔌 Wiring Overview

| Component         | Arduino Pin   |
|------------------|---------------|
| Left Motor DIR    | 4             |
| Left Motor PWM    | 5             |
| Right Motor DIR   | 2             |
| Right Motor PWM   | 6             |
| Ultrasonic TRIG   | 12            |
| Ultrasonic ECHO   | 13            |
| Servo SIGNAL      | 9             |
| LED Matrix SCL    | A5            |
| LED Matrix SDA    | A4            |
---

## ✅ Goal:
  - Drive forward
  - Sweep ultrasonic sensor using servo
  - If obstacle close, STOP & show LED face
  - Servo scans left and right to look ahead
    
---
## 💡 YOU must:
  - Write your own driveForward(), stopMotors() functions
  - Write your servo sweep in loop()
  - Use if() to decide when to stop & display face
    
---
## 💾 Arduino Code (Student Starter Template)
```cpp
#include <Servo.h>

// === MOTOR PINS ===
// LEFT Motor
#define M1_DIR 4  // Direction pin
#define M1_PWM 5  // Speed PWM pin

// RIGHT Motor
#define M2_DIR 2  // Direction pin
#define M2_PWM 6  // Speed PWM pin

// === ULTRASONIC PINS ===
#define TRIG_PIN 12
#define ECHO_PIN 13

// === SERVO ===
Servo myServo;
#define SERVO_PIN 9  // Use pin 9

// === LED MATRIX PINS ===
#define SCL_Pin A5
#define SDA_Pin A4

// === LED MATRIX FACE ===
// 💡 TODO: Use dotmatrixtool.com and paste your hex array below:
// Example: unsigned char myFace[] = { ... };
unsigned char myFace[] = { 
  // 👉 Students paste their face hex here!
};

long duration;
float cm;

void setup() {
  // Motors
  pinMode(M1_DIR, OUTPUT);
  pinMode(M1_PWM, OUTPUT);
  pinMode(M2_DIR, OUTPUT);
  pinMode(M2_PWM, OUTPUT);

  // Ultrasonic
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);

  // Servo
  myServo.attach(SERVO_PIN);

  // LED Matrix
  pinMode(SCL_Pin, OUTPUT);
  pinMode(SDA_Pin, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  // === TODO: Sweep servo ===
  // 💡 Example: myServo.write(0); delay(200);
  // 💡 Then myServo.write(180); delay(200);
  // 💡 Or use for loop to sweep smoothly

  // === Measure distance ===
  measureDistance();

  Serial.print("Distance: ");
  Serial.print(cm);
  Serial.println(" cm");

  // === TODO: IF logic ===
  // if (cm < safe limit) {
  //   stopMotors();
  //   matrix_display(myFace);
  // } else {
  //   driveForward();
  // }
}

// === MEASURE DISTANCE ===
void measureDistance() {
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  duration = pulseIn(ECHO_PIN, HIGH, 25000);
  cm = (duration / 2.0) / 29.1;
}

// === LED MATRIX ===
void matrix_display(unsigned char matrix_value[]) {
  IIC_start();
  IIC_send(0xC0);

  for (int i = 0; i < 16; i++) {
    IIC_send(matrix_value[i]);
  }

  IIC_end();
  IIC_start();
  IIC_send(0x8A);
  IIC_end();
}

void IIC_start() {
  digitalWrite(SCL_Pin, HIGH);
  delayMicroseconds(3);
  digitalWrite(SDA_Pin, HIGH);
  delayMicroseconds(3);
  digitalWrite(SDA_Pin, LOW);
  delayMicroseconds(3);
}

void IIC_send(unsigned char send_data) {
  for (char i = 0; i < 8; i++) {
    digitalWrite(SCL_Pin, LOW);
    delayMicroseconds(3);
    if (send_data & 0x01) {
      digitalWrite(SDA_Pin, HIGH);
    } else {
      digitalWrite(SDA_Pin, LOW);
    }
    delayMicroseconds(3);
    digitalWrite(SCL_Pin, HIGH);
    delayMicroseconds(3);
    send_data >>= 1;
  }
}

void IIC_end() {
  digitalWrite(SCL_Pin, LOW);
  delayMicroseconds(3);
  digitalWrite(SDA_Pin, LOW);
  delayMicroseconds(3);
  digitalWrite(SCL_Pin, HIGH);
  delayMicroseconds(3);
  digitalWrite(SDA_Pin, HIGH);
  delayMicroseconds(3);
}

---
##Hint:
```cpp
// To move left motor forward:
//   digitalWrite(M1_DIR, LOW);
//   analogWrite(M1_PWM, 150);
// To move right motor forward:
//   digitalWrite(M2_DIR, HIGH);  // Direction for right side is usually REVERSED!
//   analogWrite(M2_PWM, 150);
