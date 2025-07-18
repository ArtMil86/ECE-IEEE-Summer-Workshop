# 🤖 ECE/IEEE Summer Workshop: An Intro to Robotics

Welcome to the self-paced robotics workshop using the 4WD Arduino-powered robot platform.
This site will guide you step-by-step through building and programming your own smart robot!

---

## 🌟 Introduction to Robotics

Robotics combines engineering, electronics, and programming to bring machines to life. Robots are all around us — in manufacturing, healthcare, delivery systems, and even space! In this workshop, you’ll learn **how to build and control your very own robot** using simple, powerful tools.

You’ll be working with a **4-wheel drive robot** powered by **Arduino**. Arduino is a beginner-friendly microcontroller that lets you write code to control hardware — motors, sensors, lights, and more. The goal is to make your robot drive, sense the environment, react, and display information — just like a real smart machine.

This hands-on learning experience will introduce you to key robotics concepts and core programming skills, even if you’ve never coded before.

---

## 🚗 About the Robot

Your robot uses:

* **Two DC motors** to drive the left and right sides
* An **L298P motor driver** to control motor speed and direction
* A **servo motor** to rotate sensors or displays
* An **ultrasonic sensor** to detect objects in front of it
* A **LED matrix** to show faces or messages

All of this is controlled by an **Arduino board** running your code.

> 💡 Throughout the workshop, you’ll learn how each component works, how to wire it up, and how to write programs that bring your robot to life!

---

## 🚀 Workshop Overview

This workshop includes:

* 🔧 Motor Control (Forward, Backward, Turning)
* 🔁 Servo Motor Movement (For Loops, Angles)
* 📡 Ultrasonic Sensor (Distance Detection)
* 🔲 LED Matrix Display (Faces & Messages)
* 🧠 Final Smart Robot Challenge

All lessons include:

* Clear objectives ✅
* Sample Arduino code 💻
* Diagrams and images 🖼️
* Beginner programming tips (e.g., if, for, libraries)

---

## 📚 Workshop Lessons

| Lesson | Title                                    | Link                                                                                                                                                        |
| ------ | ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | Motors: Forward, Backward, Turning       | [Go to Lesson 1](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%201%20-%20Motors%3A%20Forward%20Backward%2C%20Left%20%26%20Right.md) |
| 2      | Servo Motor Basics                       | [Go to Lesson 2](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%202%20-%20Servo%20Motor.md)                                          |
| 3      | Ultrasonic Sensor                        | [Go to Lesson 3](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%203%20Ultrasonic%20Sensor.md)                                        |
| 4      | LED Matrix Display                       | [Go to Lesson 4](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%204%20-%208x16%20LED%20Matrix.md)                                    |
| 5      | Final Challenge: Obstacle-Avoiding Robot | [Go to Lesson 5](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop/blob/main/Lesson%205%20-%20Smart%20Obstacle%20-%20Avoiding%20Robot.md)                |
| 🚧     | Programming Tips (if, for, libraries)    | [Go to Programming Basics](https://docs.arduino.cc/learn/programming/reference/)                                                                                                         |

---

## 🛠️ How to Use This Site

* Click on any lesson link above to start learning.
* Each lesson contains instructions, example code, and challenge tasks.
* This site is self-paced — go at your own speed!

---

## 🔗 Resources

* [Dot Matrix Designer Tool]((http://dotmatrixtool.com/#))
* [Arduino IDE Download](https://www.arduino.cc/en/software)
* [GitHub Repository for Code Files](https://github.com/ArtMil86/ECE-IEEE-Summer-Workshop)

---

## 📸 About This Project

Made with ❤️ by IEEE at UMD
View the full GitHub Page here: ***your-pages-link-here***

---

## 💡 Arduino Coding & Uploading Tips

### 🧠 Understanding Arduino Code Structure

Every Arduino program (called a sketch) is made up of a few key parts:

```cpp
// 1. Global Declarations
// This is where you include libraries and define constants/pins

void setup() {
  // 2. Setup Code — runs ONCE when the robot starts or resets
  // You set pin modes, initialize motors/serial/LEDs, etc.
}

void loop() {
  // 3. Loop Code — runs FOREVER after setup()
  // This is your robot's "brain" running repeatedly
}

// 4. Custom Functions — You can add your own below
void driveForward() {
  // motor logic here
}
```

📌 **Tip**: Define your own functions like `driveForward()` or `measureDistance()` below `loop()` and call them inside the loop when needed.

Many students get confused where code should go — follow the structure above!

---

### 🔌 Power Management When Uploading Code

💻 When uploading new code from your computer:

* **Turn OFF the robot's top switch** before clicking Upload.
* This prevents motor power from interfering with USB communication.

🔋 After the upload is complete:

* **Turn ON the top switch** so that the motors and sensors receive power from the battery pack.

> ⚠️ Reminder: USB alone can’t power the robot's motors — it only powers the Arduino board.

🧠 Many problems happen when students forget to flip the power switch ON!

---

### ✅ Good Practices While Programming

* Always click **✔ Verify** before uploading — it checks for errors.
* Use `Serial.print()` to help troubleshoot your code.
* Never change wiring while the car is powered on — **turn the switch OFF first**.
* Use modular code with functions to isolate each component.
* If something breaks, go back to your individual test sketches for that part.

---
