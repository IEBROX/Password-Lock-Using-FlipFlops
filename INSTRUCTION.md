# Hardware Implementation Guide  
## Password Lock System Using D Flip-Flops (74LS74)

This document explains how to implement the Logisim password lock circuit on a breadboard using standard 74xx TTL ICs.

---

## 1. Required Components

- 74LS74 (Dual D Flip-Flop) – 2 ICs  
- 74LS32 (OR Gate) – 1 IC  
- 74LS04 (NOT Gate) – 1 IC  
- Push Buttons – 5 (4 password inputs + 1 reset)  
- 10kΩ resistors – 5  
- 220Ω resistor – 1 (LED current limiting)  
- LED – 1 (Unlock indicator)  
- 5V regulated power supply  
- Breadboard  
- Jumper wires  
- 0.1µF decoupling capacitors (1 per IC, recommended)

---

## 2. IC Power Connections (IMPORTANT)

For all 74LS ICs:

- Pin 14 → +5V  
- Pin 7 → GND  

Place a 0.1µF capacitor between VCC and GND for each IC.

⚠ Do NOT exceed 5V.

---

## 3. 74LS74 Flip-Flop Pin Configuration

Each 74LS74 contains 2 D flip-flops.

| Function | 1st FF Pin | 2nd FF Pin |
|----------|------------|------------|
| CLR      | 1          | 13         |
| D        | 2          | 12         |
| CLK      | 3          | 11         |
| Q        | 5          | 9          |
| PRE      | 4          | 10         |

---

## 4. Reset / Clear Setup

- Connect all CLR pins together.
- Use a push button to pull CLR LOW.
- Add 10kΩ pull-up resistor to +5V.
- Normally CLR should remain HIGH.
- When pressed (LOW), system resets.

PRE pins must be tied HIGH (+5V).

---

## 5. Password Input Setup

For each password bit (p1, p2, p3, p4):

1. Connect push button to D input.
2. Add 10kΩ pull-down resistor to GND.
3. Other side of push button connects to +5V.

This prevents floating inputs.

---

## 6. Clock Setup

- Connect all CLK pins together.
- Use one push button as clock.
- Add 10kΩ pull-down resistor to GND.
- Pressing clock stores input bits into flip-flops.

Optional: Add debounce circuit for stable operation.

---

## 7. Combinational Logic Wiring

- Connect Q outputs to 74LS32 OR gates as per Logisim design.
- Combine intermediate outputs exactly like the simulation.
- Final logic output represents "Password Correct".

If required:
- Pass final output through 74LS04 NOT gate.

Follow your simulation wiring carefully.

---

## 8. Unlock Indicator

Final logic output → 220Ω resistor → LED → GND  

LED ON  = Password Correct  
LED OFF = Password Incorrect  

---

## 9. Operating Procedure

1. Apply 5V power.
2. Press RESET.
3. Set password bits.
4. Press CLOCK.
5. If correct, LED turns ON.
6. Press RESET to restart.

---

## 10. Safety Notes

- Never exceed 5V.
- Avoid floating inputs.
- Double-check VCC and GND.
- Keep wiring short.

---

## 11. Possible Improvements

- Add buzzer for wrong attempt
- Add attempt counter
- Add auto lock after 3 failures
- Implement using JK flip-flops
- Replace with microcontroller-based system
