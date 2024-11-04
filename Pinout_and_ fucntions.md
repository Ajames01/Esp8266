# ESP8266 Pinout and Functions

This README provides a comprehensive overview of the pinout for the ESP8266 microcontroller, detailing the various pins available on common ESP8266 modules, such as the NodeMCU and ESP-01, along with their functions. Understanding these pins is crucial for effectively utilizing the ESP8266 in your projects.


## Pinout Diagram

ESP8266 Pinout
![WhatsApp Image 2024-11-04 at 09 44 12_2f7a3831](https://github.com/user-attachments/assets/18751f51-5404-4153-892b-e6f4851221a5)

## Pin Functions

The ESP8266 has multiple pins, each serving specific functions. Below is a table summarizing the key pins and their respective roles:

| Pin Number | Name       | Function Description                                   |
|------------|------------|-------------------------------------------------------|
| 1          | **VDDA**   | Analog power supply                                   |
| 2          | **LNA**    | RF antenna interface                                  |
| 3          | **VDD3P3** | Amplifier power supply                                |
| 4          | **VDD_RTC**| Real-time clock power supply (NC)                    |
| 5          | **TOUT**   | ADC pin (Analog to Digital Converter)                |
| 6          | **CHIP_EN**| Chip enable pin (active HIGH)                         |
| 7          | **XPD_DCDC**| Deep sleep wakeup pin                               |
| 8          | **GPIO0**  | General-purpose I/O, used to enter bootloader mode   |
| 9          | **GPIO2**  | General-purpose I/O                                   |
| 10         | **GPIO4**  | General-purpose I/O (often used for I2C SDA)        |
| 11         | **GPIO5**  | General-purpose I/O (often used for I2C SCL)        |
| 12         | **GPIO12** | General-purpose I/O (MISO for SPI)                   |
| 13         | **GPIO13** | General-purpose I/O (MOSI for SPI)                   |
| 14         | **GPIO14** | General-purpose I/O (SCLK for SPI)                   |
| 15         | **GPIO15** | General-purpose I/O (CS for SPI, pulled LOW at boot) |
| 16         | **GPIO16** | Used to wake up from deep sleep                       |
| 17         | **RST**    | Reset pin                                            |
| 18         | **ADC0**   | Analog input pin with a maximum voltage of 1V       |

## Detailed Functionality of Key Pins

### GPIO Pins
- The ESP8266 features a total of **17 GPIO pins**, which can be configured for various functions including digital input/output, PWM output, and more. Not all GPIOs are available on every module.

### ADC Pin
- The only analog input available is the **ADC0 pin**, which can read voltages from 0 to approximately 1V (or up to 3.3V on development boards like NodeMCU). This pin has a resolution of **10 bits**, providing values between 0 and 1023.

### UART Communication
- The ESP8266 supports two UART interfaces:
  - **UART0**: Used for serial communication and debugging.
  - **UART1**: Primarily used for logging output.

### SPI and I2C Interfaces
- The ESP8266 supports both SPI and I2C protocols:
  - **SPI Pins**:
    - MISO: GPIO12
    - MOSI: GPIO13
    - SCLK: GPIO14
    - CS: GPIO15
  - **I2C Pins**: Software-based, commonly using GPIO4 (SDA) and GPIO5 (SCL).

### Control Pins
- **CHIP_EN (Chip Enable)**: Activates the chip when pulled HIGH.
- **RST (Reset)**: Resets the module when pulled LOW.
- **FLASH Pin**: Used to enter bootloader mode when held LOW during startup.
- **WAKE Pin**: Wakes the chip from deep sleep.

## Usage Considerations

- Be cautious when using certain GPIOs during boot; specific states can prevent the ESP8266 from starting correctly:
  - GPIO0 should not be LOW during boot.
  - GPIO15 should not be HIGH during boot.
  
- Avoid using GPIOs connected to the flash chip (typically GPIO6 to GPIO11), as they are reserved for internal use.

