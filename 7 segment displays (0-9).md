# ESP8266 Seven Segment Display Project

This project demonstrates how to control a seven-segment display using the ESP8266 microcontroller. The ESP8266 will display numbers from 0 to 9.

## Components Required

- **ESP8266 Development Board** (e.g., NodeMCU, Wemos D1 Mini)
- **Seven Segment Display** (Common Cathode recommended)
- **Resistors** (220-ohm or 100-ohm)
- **Breadboard**
- **Jumper Wires**

## Connect the ESP8266 to the seven-segment display as follows:

| ESP8266 Pin | Seven Segment Pin |
|-------------|--------------------|
| D0          | g                  |
| D1          | f                  |
| D2          | a                  |
| D3          | b                  |
| D4          | e                  |
| D5          | d                  |
| D6          | c                  |
| D7          | dp (dot point)     |
| GND         |Through a 220Ohm    |
|             |resistor and to COM |
|             |pin on 7 segment    |

## Code Example

Here’s a simple Arduino sketch to control the seven-segment display:

```cpp
#include <Arduino.h>

// Define segment pins
const int A_PIN = D2; // Segment A
const int B_PIN = D3; // Segment B
const int C_PIN = D6; // Segment C
const int D_PIN = D5; // Segment D
const int E_PIN = D4; // Segment E
const int F_PIN = D1; // Segment F
const int G_PIN = D0; // Segment G
const int DP_PIN = D7; // Decimal Point

// Array for digits 0-9
const byte digits[10][8] = {
    {HIGH, HIGH, HIGH, HIGH, HIGH, HIGH, LOW, LOW},   // 0
    {LOW, HIGH, HIGH, LOW, LOW, LOW, LOW, LOW},       // 1
    {HIGH, HIGH, LOW, HIGH, HIGH, LOW, HIGH, LOW},    // 2
    {HIGH, HIGH, HIGH, HIGH, LOW, LOW, HIGH, LOW},     // 3
    {LOW, HIGH, HIGH, LOW, LOW, HIGH, HIGH, LOW},      // 4
    {HIGH, LOW, HIGH, HIGH, LOW, HIGH, HIGH, LOW},     // 5
    {HIGH, LOW, HIGH, HIGH, HIGH, HIGH, HIGH, LOW},    // 6
    {HIGH, HIGH, HIGH, LOW, LOW, LOW, LOW ,LOW},       // 7
    {HIGH ,HIGH ,HIGH ,HIGH ,HIGH ,HIGH ,LOW ,LOW},   // 8
    {HIGH ,HIGH ,HIGH ,LOW ,LOW ,HIGH ,HIGH ,LOW}     // 9
};

void setup() {
    Serial.begin(115200);
    
    // Set all segment pins as OUTPUT
    pinMode(A_PIN, OUTPUT);
    pinMode(B_PIN, OUTPUT);
    pinMode(C_PIN, OUTPUT);
    pinMode(D_PIN, OUTPUT);
    pinMode(E_PIN, OUTPUT);
    pinMode(F_PIN, OUTPUT);
    pinMode(G_PIN, OUTPUT);
    pinMode(DP_PIN, OUTPUT);
}

void loop() {
    for (int i = 0; i < 10; i++) {
        displayDigit(i);   // Display digit from 0 to 9
        delay(1000);       // Wait for a second before next digit
    }
}

void displayDigit(int digit) {
    digitalWrite(A_PIN,digits[digit][0]);
    digitalWrite(B_PIN,digits[digit][1]);
    digitalWrite(C_PIN,digits[digit][2]);
    digitalWrite(D_PIN,digits[digit][3]);
    digitalWrite(E_PIN,digits[digit][4]);
    digitalWrite(F_PIN,digits[digit][5]);
    digitalWrite(G_PIN,digits[digit][6]);
}
```

## Conclusion

This project shows how to use a seven-segment display with the ESP8266. You can modify and extend it to display other characters or integrate it with Wi-Fi features. Enjoy experimenting!
