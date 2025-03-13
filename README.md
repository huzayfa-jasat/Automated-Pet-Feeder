# Automated-Pet-Feeder
The Automated Pet Feeder is a LEGO EV3-based system designed to dispense food for cats and dogs based on sound detection. It uses various sensors to identify which pet is present, ensure proper feeding times, and notify the owner when food is low.

## Features:<br/>
* **Pet Detection:** Uses an ultrasonic sensor to detect nearby pets and a sound sensor to differentiate between a cat (quiet meow) and a dog (loud bark).<br/>
* **Automated Food Dispensing:** A motorized hopper system opens and closes to dispense food for the detected pet.<br/>
* **Turntable Mechanism:** The feeder rotates 180 degrees to align with the correct bowl before dispensing food.<br/>
* **Feeding Interval Control:** Prevents overfeeding by tracking feeding times using a built-in timer.<br/>
* **Low Food Alerts:** A color sensor detects when the hopper is empty and alerts the user through sound and a display message.<br/>
* **User Input for Feeding Time:** Allows users to set custom feeding durations using EV3 buttons.<br/>
* **Manual Shutdown:** Pressing a button will shut down the feeder safely, displaying feeding statistics before turning off.<br/>

## Hardware Components:<br/>
* EV3 Brick for processing and control<br/>
* Ultrasonic Sensor (S1) for pet proximity detection<br/>
* Sound Sensor (S4) for animal recognition<br/>
* Color Sensors (S2, S3) for food level detection<br/>
* 3 Motors:<br/>
  * Turntable Motor (C) – Rotates between bowls<br/>
  * Cat Hopper Motor (A) – Opens/closes the cat food hopper<br/>
  * Dog Hopper Motor (B) – Opens/closes the dog food hopper<br/>
  
## Software Logic<br/>
### Startup Configuration:<br/>
* All sensors are initialized and calibrated.<br/>
* Motor encoders are reset.<br/>
* Turntable rotates to default position (180°).<br/>

### Main Logic Flow<br/>
#### 1. Pet Detection:<br/>
* Ultrasonic sensor checks for a pet in range.<br/>
* If a pet is detected, the sound sensor listens for a meow or bark.<br/>
* Based on the noise level, the system determines whether it's a cat or dog.<br/>

#### 2. Feeding Decision:<br/>
* If the detected pet has not been fed recently, the system proceeds to dispense food.<br/>
* Time intervals between feedings are enforced using a timer.<br/>

#### 3. Food Dispensing:<br/>
* The turntable rotates to the correct bowl.<br/>
* The hopper opens for a set time, dispensing food.<br/>
* The hopper closes, and the turntable returns to the default position.<br/>

#### 4. Food Level Check:<br/>
* The color sensor checks if food is running low.<br/>
* If empty, the system alerts the owner through a sound and display message.<br/>

#### 5. Shutdown Process:<br/>
* The user can press a button to shut down.<br/>
* The feeder displays feeding statistics before turning off.<br/>

## Code Structure:<br/>
| Function | Description |
| :---           |          ---: |
| startFeeder()|	Initializes all sensors and motors, sets default states
|turnTable(int deg)|	Rotates the turntable to a specified angle
dispenseFood(char animal)	|Opens and closes the hopper to dispense food
getFood(char animal)	|Rotates the turntable, dispenses food, and returns to default position
checkAnimal()|	Detects if a pet is present and determines if it’s a cat or dog
checkHopperEmpty(char animal)|	Checks if the food hopper is empty and alerts the owner
alert(char animal)	|Displays a warning and plays a sound when food runs out
setFeedTime()	|Allows the user to set custom feeding intervals
runChecks()	|Main loop that continuously monitors pet presence and feeding logic
shutDown()	|Handles system shutdown and displays feeding statistics
task main()	|Runs the feeder logic from startup to shutdown| <br/>

## Future Improvements:<br/>
* Add a database or SD card storage to track feeding history.<br/>
* Integrate WiFi or Bluetooth for remote monitoring via a mobile app.<br/>
* Improve accuracy of pet recognition using machine learning models.<br/>
