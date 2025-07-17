# 💡 Lesson 4 — 8x16 LED Matrix (Keyestudio 4WD BT Car)

## 🎯 Objectives
- Learn how to control a **dot matrix display** using I²C and bit-shifting
- Scroll a custom pattern across the screen from **left to right**
- Practice manipulating binary data with `<<`, `>>`, and custom shifting
- Create your own designs using **byte arrays**

---

## 🧠 Concepts

- Each column of an LED matrix is represented as **1 byte** (8 bits).
- You scroll by **bit-shifting** each byte and merging adjacent bytes.
- Custom characters or patterns can be encoded as arrays of bytes.

---

## 🔌 Wiring Instructions

| LED Matrix Pin | Arduino Pin |
|----------------|-------------|
| SCL            | A5          |
| SDA            | A4          |
| VCC            | 5V          |
| GND            | GND         |

📌 Make sure to power the matrix from 5V and confirm the **SCL** and **SDA** lines match the I²C configuration (A5 and A4 on most Arduino Uno boards).

---

## 💾 Arduino Code

```cpp
/*
Keyestudio 4WD BT Car V2.0
Lesson — LED Matrix LEFT to RIGHT SCROLL

✅ Scrolls a custom pattern left to right
✅ New bits appear on the right
✅ Uses simple bit-shifting
*/

// 👉 Example pattern — replace with your own 32 bytes
unsigned char pattern[] = {
  0x44, 0x00, 0x7C, 0x00, 0x44, 0x00, 0x00, 0x00,  // I
  0x7C, 0x00, 0x54, 0x00, 0x54, 0x00, 0x00, 0x00,  // E
  0x7C, 0x00, 0x54, 0x00, 0x54, 0x00, 0x00, 0x00,  // E
  0x7C, 0x00, 0x54, 0x00, 0x54, 0x00, 0x00, 0x00   // E
};

#define SCL_Pin A5
#define SDA_Pin A4

void setup() {
  pinMode(SCL_Pin, OUTPUT);
  pinMode(SDA_Pin, OUTPUT);
}

void loop() {
  int totalCols = sizeof(pattern);
  int displayCols = 16;

  while (true) {
    for (int shift = 0; shift < 8; shift++) {  // Bit shift
      for (int pos = 0; pos <= totalCols - displayCols; pos++) {
        IIC_start();
        IIC_send(0xC0);

        for (int i = 0; i < displayCols; i++) {
          unsigned char current = pattern[pos + i];
          unsigned char next = 0x00;
          if (pos + i + 1 < totalCols) {
            next = pattern[pos + i + 1];
          }

          // Shift left by 'shift' bits to push left
          // Bring in next byte bits on the right
          unsigned char col = (current << shift) | (next >> (8 - shift));

          // Flip bits vertically if needed
          col = flipByte(col);

          IIC_send(col);
        }

        IIC_end();
        IIC_start();
        IIC_send(0x8A);  // Refresh display
        IIC_end();

        delay(100);  // Scroll speed
      }
    }
  }
}

// === Flip bits vertically if needed ===
unsigned char flipByte(unsigned char b) {
  unsigned char rev = 0;
  for (int i = 0; i < 8; i++) {
    rev <<= 1;
    rev |= (b & 0x01);
    b >>= 1;
  }
  return rev;
}

// === IIC Protocol ===
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
    digitalWrite(SDA_Pin, (send_data & 0x01) ? HIGH : LOW);
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
