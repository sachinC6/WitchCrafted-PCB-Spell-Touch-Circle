# 🧙‍♀️ WitchCrafted PCB – Spell Touch Circle

---

## Project Introduction
**WitchCrafted PCB – Spell Touch Circle** is a **Halloween-themed interactive magic board** powered by **Arduino Uno**.  
Each button represents a magical rune — when pressed, it lights up an RGB LED in colorful patterns and plays a short sound effect, simulating a spell-casting experience.  

This project blends **electronics with art**, making it perfect for beginners, makers, and Halloween contest entries such as **JLCPCB’s “Colorful Silkscreen Magic”**.

---

## Project Function
- Uses **five buttons** to simulate “touch” magic symbols.  
- Each button triggers a **different RGB color pattern** and **buzzer tone**.  
- Demonstrates **PWM LED control**, **digital inputs**, and **tone generation**.  
- Works as a **Halloween prop**, **table decoration**, or **learning circuit**.  
- Designed to be simple enough to **simulate in Tinkercad** or **build physically**.  

---

## Project Parameters
- **Microcontroller:** Arduino Uno  
- **Inputs:** 5 push buttons (rune pads)  
- **Outputs:** 1 RGB LED (common cathode) + Piezo buzzer  
- **Resistors:** 220 Ω for each LED line  
- **Power:** USB or 9 V battery  
- **Simulation:** Fully supported in [Tinkercad Circuits](https://www.tinkercad.com/circuits) or [Wokwi](https://wokwi.com)  

---

## Principle Analysis (Hardware Description)
The project is divided into the following functional blocks:

1. **Main Control:**  
   - Arduino Uno processes input from buttons and drives the LED and buzzer.

2. **Input Section:**  
   - Five push buttons connected to digital pins (2, 4, 7, 8, 10) with internal pull-ups enabled.  
   - When pressed, the pin reads LOW, triggering a “spell.”

3. **Output Section:**  
   - RGB LED driven via PWM pins 3 (R), 5 (G), 6 (B).  
   - Piezo buzzer connected to pin 9 for tone output.  

4. **Power Supply:**  
   - Can be powered via USB or 9 V battery through the Arduino board.

---

## Software Code
```cpp
#define R 3
#define G 5
#define B 6
#define buzzer 9

int buttons[5] = {2, 4, 7, 8, 10};

void setup() {
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);
  pinMode(buzzer, OUTPUT);

  for (int i = 0; i < 5; i++) pinMode(buttons[i], INPUT_PULLUP);
}

void loop() {
  for (int i = 0; i < 5; i++) {
    if (digitalRead(buttons[i]) == LOW) {
      castSpell(i);
    }
  }
}

void castSpell(int spell) {
  switch (spell) {
    case 0: setColor(255, 0, 0); tone(buzzer, 400, 200); break;  // Red spell
    case 1: setColor(0, 255, 0); tone(buzzer, 600, 200); break;  // Green spell
    case 2: setColor(0, 0, 255); tone(buzzer, 800, 200); break;  // Blue spell
    case 3: setColor(255, 255, 0); tone(buzzer, 1000, 200); break; // Yellow spell
    case 4: rainbowEffect(); tone(buzzer, 1200, 200); break;  // Rainbow spell
  }
  delay(500);
  setColor(0, 0, 0);
}

void setColor(int red, int green, int blue) {
  analogWrite(R, red);
  analogWrite(G, green);
  analogWrite(B, blue);
}

void rainbowEffect() {
  for (int r = 0; r < 255; r++) {
    setColor(r, 255 - r, 128);
    delay(5);
  }
}
````

---

## Announcements

* Use **220 Ω resistors** for each RGB LED pin.
* Connect push buttons with **INPUT_PULLUP** enabled (no external resistors needed).
* Double-check LED polarity — common cathode connects to **GND**.
* If simulating, replace touch pads with standard buttons.
* For physical PCBs, a **purple or black board** with silkscreen runes gives the best aesthetic result.

---

## Assembling Process

1. Connect push buttons to pins 2, 4, 7, 8, 10 → GND.
2. Connect RGB LED pins to 3 (R), 5 (G), 6 (B) → each with 220 Ω resistor.
3. Connect buzzer to pin 9 → GND.
4. Power Arduino from USB or 9 V supply.
5. Upload the sketch and test.
6. Optionally, design a circular PCB with rune-style silkscreen art.

---

## Finished Product Display

When assembled, each button press activates a unique color glow and tone, creating a **magical spell effect**.
The board lights up beautifully in dark rooms — perfect for **Halloween displays**, **DIY electronics demos**, or **cosplay accessories**.

![Magic Circle Concept](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Pentacle.svg/512px-Pentacle.svg.png)

---

## Resources

* [Tinkercad Circuits – Free Simulator](https://www.tinkercad.com/circuits)
* [Arduino IDE Download](https://www.arduino.cc/en/software)
* [JLCPCB PCB Fabrication Service](https://jlcpcb.com)
* [Project Repository Template](https://github.com/)

---

### Author

**Prince K.**
*Electronics Engineering Student | Embedded Systems & Creative Circuits Enthusiast*

---

### License

This project is open-source under the **MIT License**.
Feel free to remix, modify, and share — just give proper credit.

---

*"When technology meets magic, circuits come alive."*

```

---

Would you like me to:  
1️⃣ Add a **schematic diagram image (Arduino + LED + buttons)** to insert into the repo automatically,  
or  
2️⃣ Create a **Tinkercad simulation link + screenshot** for your README “Demo” section?  

Both help your GitHub project look more professional and contest-ready.
```
