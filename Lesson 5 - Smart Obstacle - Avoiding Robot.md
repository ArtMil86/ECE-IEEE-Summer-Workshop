# 🤖 Lesson 5 — Smart Obstacle-Avoiding Robot (Keyestudio 4WD BT Car)

## 🎯 Objectives

* Combine **all previous skills**: motors, ultrasonic sensor, servo, and LED matrix.
* Build a robot that **drives forward** and **reacts** when it detects an obstacle.
* Display **animated warnings** using the LED matrix.
* Use `if` statements, `for` loops, sensor readings, and modular code effectively.

---

## 🧠 What You Should Know by Now

By this point, you've learned how to:

✅ Wire and control **DC motors** for movement
✅ Use a **servo** to rotate between angles
✅ Measure distance with an **ultrasonic sensor**
✅ Display images using an **LED matrix**
✅ Write and use `if`, `for`, `delay`, and functions

Now, it’s time to put it **all together** into one **autonomous robot**.

---

## 🧩 Suggested Features

Here are ideas for what your robot can do:

| Feature                  | What It Should Do                                     |
| ------------------------ | ----------------------------------------------------- |
| 🔄 Servo Sweep           | Move left and right to "look around"                  |
| 🧠 Distance Check        | Use `pulseIn()` to measure distance                   |
| ❌ Obstacle Detected      | Stop the motors, show warning on LED matrix           |
| ✅ Path is Clear          | Drive forward                                         |
| 💬 LED Display           | Use smile, arrow, or stop icons to communicate        |
| 🔄 Scan for Alternatives | After stopping, look left and right and choose a turn |
| 🔁 Smart Recovery        | If no path found, back up and try again               |

---

## 🛠️ Things to Remember

* The servo uses **pin 9** — you can `write(angle)` from 0 to 180°
* Use your **ultrasonic TRIG** (pin 12) and **ECHO** (pin 13) to measure distance
* Motors use **4, 5, 2, 6** (check your left/right wiring!)
* LED matrix uses **A4 (SDA)** and **A5 (SCL)**

---

## 💡 Design Tips

* Create your own functions: `driveForward()`, `stopMotors()`, `scanServo()`, `turnLeft()`, `turnRight()`, `reverse()`
* Add creative faces or icons to match robot behaviors:

  * 😀 Going Forward
  * 😮 Obstacle Detected
  * 🤔 Scanning
  * ⛔ Stop / Blocked
  * 🔄 Turning
* Use servo sweeps **after stopping** to scan side angles before deciding to reverse or turn
* Bonus: add sounds or blinking lights for even more personality!

---

## 🧪 Challenge Ideas

| Challenge                         | Description                                                |
| --------------------------------- | ---------------------------------------------------------- |
| 🚗 Smart Drive                    | Robot drives and stops automatically                       |
| 🎭 Show Emotions                  | Display different LED faces based on actions               |
| 🌀 Servo Scan + React             | Robot turns head (servo) and reacts when blocked           |
| 🧠 Obstacle Avoidance Logic       | If path is blocked, scan left/right and decide direction   |
| ↩️ Backup Mode                    | If no path found, reverse and turn to try new path         |
| ⛑️ Safety Mode                    | Add longer-range scanning before making big turns          |
| 💡 Light-Based Trigger (Advanced) | Combine with photoresistor or IR sensor for added behavior |

---

## 📓 Reflect and Plan

Ask yourself:

* What functions will you reuse from previous lessons?
* What logic will you need for directional decision-making?
* What matrix displays will help you express what the robot is "thinking"?
* How can you make your code modular and easy to read?

---

## 🎬 Final Project Prompt

> Create an obstacle-avoiding robot using **everything** you've learned:
>
> * When path is clear → drive forward with a smile face
> * When obstacle detected → stop and display warning face
> * Servo sweeps left and right → choose turn direction
> * If no clear path → reverse and try another way
>
> Bonus: use creative matrix icons for every phase!

💾 Name your file: `smart_robot.ino`

🔗 You can use animations from your **Lesson 4 LED Matrix**, distance functions from **Lesson 3**, and movement logic from **Lesson 1**.

---

🚀 Ready to test it? You're now building **adaptive behavior** — the heart of robotics!
