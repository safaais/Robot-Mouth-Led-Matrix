# Robot-Mouth-Led-Matrix

The project aims to simulate a robot mouth by controlling a 8x8 LED matrix. It uses an Arduino Uno board to send signals to the matrix, which then illuminates specific LEDs to create the appearance of a mouth opening and closing.

## Simulation:

![image alt]( https://github.com/safaais/Robot-Mouth-Led-Matrix/blob/75645d0e6323ed2bdd35e462351b3737b837696a/Screenshot%202024-08-14%20040021.png)

![image alt]( https://github.com/safaais/Robot-Mouth-Led-Matrix/blob/75645d0e6323ed2bdd35e462351b3737b837696a/Screenshot%202024-08-14%20040038.png)

## Code:

```
#include <LedControl.h>

// Initialize the LED Matrix
LedControl lc = LedControl(11, 13, 10, 1); // DIN, CLK, CS, # of Matrices

byte mouthClosed[8] = {
  B00000000,
  B00000000,
  B00000000,
  B01110000,
  B01110000,
  B00000000,
  B00000000,
  B00000000
};

byte mouthOpen[8] = {
  B00000000,
  B00010000,
  B00101000,
  B01000100,
  B01000100,
  B00101000,
  B00010000,
  B00000000
};

void setup() {
  lc.shutdown(0, false);
  lc.setIntensity(0, 8);
  lc.clearDisplay(0);
}

void loop() {
  // Mouth closed (line)
  displayMouth(mouthClosed);
  delay(1000);

  // Mouth open (circle)
  displayMouth(mouthOpen);
  delay(1000);

  // Mouth closed (line)
  displayMouth(mouthClosed);
  delay(1000);
}

void displayMouth(byte mouth[]) {
  for (int i = 0; i < 8; i++) {
    lc.setRow(0, i, mouth[i]);
  }
}
```
 



