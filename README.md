## Breadboard Diagram
![98173ghdu](https://github.com/user-attachments/assets/c7b9ef93-c15f-410e-b077-3d9df48f7108)

1. Setup Function
   -  `Serial.begin(9600)`: Initializes serial communication at a baud rate of 9600 for debugging and monitoring.
   -  `pinMode(buzzerPin, OUTPUT)`: Sets the buzzer pin as an output.
2. Read Sensor Values
   -  `potValue = analogRead(potPin)`: Reads the value from the potentiometer.
   -  `tempValue = analogRead(thermistorPin)`: Reads the value from the thermistor.
   -  `lightValue = analogRead(ldrPin)`: Reads the value from the LDR.
3. Map Potentiometer Value to Temperature Threshold
   -  `temperatureThreshold = map(potValue, 0, 1023, 0, 100)`: Maps the potentiometer value (0-1023) to a temperature threshold (0-100 degrees Celsius).
4. Calculate Temperature
   -  `int temperature = map(tempValue, 0, 1023, -40, 125)`: Maps the thermistor value to a temperature range of -40 to 125 degrees Celsius.
5. Control Buzzer Based on Temperature and Light Level
   - `if (temperature >= temperatureThreshold)`: Checks if the measured temperature exceeds the threshold set by the potentiometer.
     -  If true, it calculates the buzzer frequency based on the light level: `int buzzerFrequency = map(lightValue, 0, 1023, 100, 2000)`. This maps the light level to a frequency range of 100 Hz to 2000 Hz.
     -  `tone(buzzerPin, buzzerFrequency)`: Activates the buzzer at the calculated frequency.
   -  If the temperature is below the threshold, `noTone(buzzerPin)` stops the buzzer.

This code effectively creates a simple temperature and light monitoring system. The user can set a temperature threshold using a potentiometer, and if the measured temperature exceeds this threshold, the buzzer will sound at a frequency that varies based on the light level detected by the LDR. The system also provides real-time feedback through the Serial Monitor.
