##  ESP8266 LED Blink Project


### What You Need
- **ESP8266 Module** (like NodeMCU)
- **LED**
- **220-ohm Resistor**
- **Jumper Wires**
- **USB Cable** (for power and programming)
- **Computer with Arduino IDE**

### Step 1: Set Up Arduino IDE
1. **Install Arduino IDE**: Download from the [Arduino website](https://www.arduino.cc/en/software).
2. **Add ESP8266 Board**:
   - Go to `File` > `Preferences`.
   - In "Additional Board Manager URLs", add:
     ```
     http://arduino.esp8266.com/stable/package_esp8266com_index.json
     ```
   - Click OK.
3. **Install ESP8266 Board**:
   - Go to `Tools` > `Board` > `Boards Manager`.
   - Search for "ESP8266" and install it.

### Step 2: Connect the Hardware

![OIP (6)](https://github.com/user-attachments/assets/821000ff-be1c-4338-9c7b-e87e05fc9e89)

   - Connect the **long leg** (anode) of the LED to **D1** (GPIO5).
   - Connect the **short leg** (cathode) to one end of a **220-ohm resistor**.
   - Connect the other end of the resistor to **GND**.


### Step 3: Write the Code
Open Arduino IDE and enter this simple code:

```cpp
#define LED D1 // Use D1 for NodeMCU

void setup() {
    pinMode(LED, OUTPUT); // Set LED pin as output
}

void loop() {
    digitalWrite(LED, HIGH); // Turn LED on
    delay(1000);             // Wait 1 second
    digitalWrite(LED, LOW);  // Turn LED off
    delay(1000);             // Wait 1 second
}
```

### Step 4: Upload the Code
1. **Select Your Board**:
   - Go to `Tools` > `Board` and select "NodeMCU".
2. **Select Port**:
   - Go to `Tools` > `Port` and choose your device's COM port.
3. **Upload**:
   - Click the upload button (right arrow icon).

### Step 5: Watch It Blink!
Once uploaded, your LED should blink on and off every second!

### Quick Tips
- Ensure correct connections (LED polarity matters).
- If using ESP-01, make sure it's in programming mode.

This simplified guide should help you get started quickly with your ESP8266 LED blink project! Enjoy experimenting!
