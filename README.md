# Environment-temperature-and-humidity-analysis
Monitored the daily room climate and further processed its data with the help of DHT-11 sensor, MCU and Arduino. Also performed graphical variance in predicting climate change

# About Project
This Arduino sketch is designed to read temperature and humidity data from a DHT11 sensor and display it on an LCD screen. Here's a breakdown of the main parts of the code:

1. **Include Libraries:** The code starts by including the LiquidCrystal library, which allows you to control LCD displays.

2. **LiquidCrystal Object:** An instance of the LiquidCrystal class is created with the pins connected to the LCD (4, 5, 6, 7, 8, 9).

3. **Custom Character:** A custom character (degree symbol) is defined using a byte array. This character will be used later to display the temperature unit (°C).

4. **Global Variables:** Several global variables are declared:
   - `gate`: The pin connected to the DHT11 sensor.
   - `duration`: Stores the duration of the sensor signal.
   - `i[5]`: An array to store the 5 bytes of data received from the sensor.
   - `j[40]`: An array to store individual bits of the data.
   - `value`: Temporary variable to store a single bit of data.
   - `answer`: Stores the sum of the first 4 bytes of data (used for data verification).
   - `z`, `b`: Counters and flags for data processing.

5. **Setup Function:** 
   - Initializes serial communication.
   - Initializes the LCD display.
   - Prints initial text on the LCD.

6. **Custom Functions (`function1`, `function2`, `function3`):** These functions are used to print temperature, humidity, or both to the serial monitor. They are not currently called in the loop, but can be used for debugging or additional functionality.

7. **Loop Function:**
   - Waits for 1 second.
   - Reads data from the DHT11 sensor:
     - Sets the sensor pin as output and sends a start signal.
     - Sets the sensor pin as input and waits for the sensor response.
     - Reads 40 bits of data (5 bytes) from the sensor, storing each bit in `i` and `j` arrays.
   - Verifies the data integrity by summing the first 4 bytes and comparing it to the 5th byte.
   - If the data is valid, displays the temperature and humidity on the LCD.
   - Calls `function1` to print the data to the serial monitor.
   - Resets counters and data arrays for the next reading.

This code demonstrates how to interface with a DHT11 sensor and display its data on an LCD. Note that the DHT11 sensor has limitations in terms of accuracy and update rate, so this code is suitable for basic temperature and humidity monitoring applications.
