# 🧠 Day 3 — LED Patterns & Logic Control

---

## 1️⃣ Why multiple LEDs?

Working with multiple LEDs helps understand:

- Managing multiple outputs
- Code structure and organization
- Sequencing logic (very useful later for motors, LCDs, and IoT indicators)

---

## 2️⃣ LED Connection Rule

Every LED must be connected like this:

Arduino Pin → LED (anode) → 220Ω resistor → GND

Never connect LEDs directly to Arduino without a resistor — this protects the pin from excessive current.

---

## 3️⃣ Code Concepts Learned Today

| Concept | Use |
|--------|------|
| `digitalWrite()` | Turns LEDs ON/OFF |
| `delay()` | Timing control |
| `for` loops | Repeat actions without writing code 10 times |
| Arrays | Store multiple pin numbers & use them efficiently |

---

## 4️⃣ Pattern 1 — All LEDs Blink Together

```cpp
int led1 = 9;
int led2 = 8;
int led3 = 7;

void setup() {
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  delay(300);

  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  delay(300);
}

5️⃣ Pattern 2 — Ping-Pong / Knight Rider Effect

This introduces array + logic.

const int ledPin[] = {9, 8, 7};
int timer = 200;

void setup() {
  for(int i = 0; i < 3; i++) {
    pinMode(ledPin[i], OUTPUT);
  }
}

void loop() {

  // Forward → 1 → 2 → 3
  for(int i = 0; i < 3; i++) {
    digitalWrite(ledPin[i], HIGH);
    delay(timer);
    digitalWrite(ledPin[i], LOW);
  }

  // Backward → 2 → 1
  for(int i = 1; i >= 0; i--) {
    digitalWrite(ledPin[i], HIGH);
    delay(timer);
    digitalWrite(ledPin[i], LOW);
  }
}


This creates smooth movement:
LED1 → LED2 → LED3 → LED2 → LED1 → ...

6️⃣ Tinkercad Simulation Usage
Today, I also used Tinkercad Circuits to preview the wiring and code.
Why?

Avoid wiring mistakes
Test logic quickly
Confirm circuit before using real hardware
🤔 Reflection
Today’s exercise improved my logical thinking.
Using arrays and loops made the code scalable and professional.
Now I understand how embedded systems create meaningful output patterns instead of single-task blinking.