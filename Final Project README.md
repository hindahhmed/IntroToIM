# FINAL PROJECT #

#  Flashing Bugs!

## Inspiration and Game Concept

My partner Shamsa and I got inspired by a very addicting childhood game we both loved to play called "Hit the Beaver". In the game there were a bunch of beavers popping up in the screen where the player had to hit them to get a point. We thought that it would be really cool to try and re-create this but in real life format, which we got really excited about. We switched it up a bit by deciding to create insects using the LEDs instead of beavers and using force sensors to spray the bugs instead of hitting them, and of course getting a point when destroying the bugs on time. Finding an idea that interests the both of us took a while but once we came across this game idea we thought that was the one, and even though we knew that creating this complex idea would be challenging, we decided to accept whatever difficulty we would face. We started without  any second thoughts, we believed that we could do it.

## How Arduino And P5 Are Connected

For this game, we decided to only send information from Arduino to P5 and not the other way around so we did not have to use Handshake since information was only passing from one side not both. In the Arduino, we first set up the board with the things that we needed for the game, this included five LEDs and five force sensors, resistors, wires, and a switch to start and end the game. For the Arduino code, we coded a lot of logic that included when the game would start which would happen if the switch is moved from LOW to HIGH. We also coded the blinking of the lights in the LED, and how the score would decrease and increase depending on when the player presses on the force sensor (but the increasing and decreasing of score in coded in P5).

In P5, we first coded the basics which included the sound, three image backgrounds that included the first image that would be displayed when the game starts, the second image which would display if the player loset (point 0 or less), and finally the third image which would display if the player won (point 1 or higher). We also put  the display of points (force code for when it pressed on or not is on arduino), the timer (we coded that the timer would start in P5 only if the switch in arduino is turned on).

## Summary concept of the Game:

We called our game 'flashing bugs' because we wanted it to be short, fun, and unique. In the game, the player would first see that the LEDs (bugs) would all be turned on. When the player os ready to play the game, he or she has to flip the switch to the other side for the game to begin. When the switch is flipped, the game will start by starting the timer in P5 which is the duration of 30 seconds. The the LEDs will also start turning OFF one at a time. When the light of one LED (bug) is turned off, the player must quickly try to press on the force sensor to kill the bug, and get a point. However, if the player presses on a sensor when an LED is turned on, a point will be deducted. The player has to get as much points as possibl in 30 seconds. When the time is up the player would get 'YOU WIN! DOUBLE CLICK TO RESTART" or "YOU LOSE! DOUBLECLICK TO RESTART" based on the number of points they get (if it was 0 or below they lose, and 1 or above they win). The player has to then double click to restart the game to try and get a higher score.

## Some important contributors we used in our Arduino board and both codes:

- LEDs - This consisted of three red LEDs and two yellow Leds
- Switch - This consisted of a black switch
- Force Sensors - This consisted of five force sensors correspondent to each LED.
- Resistors - This consisted of
- Wires - This consisted of Red, Black, and colored wires to connect 5V, GND, for other elements.
- If Statements and loops - This was consisted both in Arduino and P5

## Hardships and Coding process:

Even though putting up the circuit in the Arduino board took a long while, the coding process we would say has been the hardest part in this project. The first part of the Arduino coding of making the LEDs flash, the button working, and the force having a response to its corresponding LED had its challenges but they were easy to overcome. However, we faced difficulty when it came to the force sensors. In particular, when it came to coding how the player would get a point when pressing the force sensor when the LED was LOW. When we initially started coding this function, the values given out when the force sensor was pressed were very high, and did not correlate to a point.

Once we had our circuit working, we started working with the rest of the Arduino code that we had to do to link it to P5, this was the most part we struggled with. The merging of sending Arduino to P5 has been a bit tricky for the both of us, but while researching, and testing the codes we managed to make it work by also going through Github with the resources as well as going through old p5 and Arduino codes where we found bits and pieces of extra help from.

We have faced many hardships during the coding process. The first issue was that we had countless errors that said that the port was not connected to the Arduino which we had to adjust multiple times, through finding the correct port and connecting it. Moreover, our sensors did not work, the hardwiring was correct, however, the code itself was not working. Through asking for help from the Professor, we were able to connect the sensors to the LED, and create a point system in which when the LED was low and the sensor was pressed, the player would get a point. We checked if the sensors were working through serial monitoring and checking the numbers. We utilized 0s and 1s to monitor this. If the sensor was pressed and a 1 was printed, we were able to see that it works.
 
## Arduino Board Process

![process](https://github.com/shamsasaeed/ssa8778/blob/main/process%20board.jpg)

![process2](https://github.com/shamsasaeed/ssa8778/blob/main/process%20board%202.jpg)


## Code explanation:ARDUINO
 
In the beginning of the code we first created variables for the button pin (the switch on the board), the five LEDs (LEDs on the board), the five sensors (sensors on the board), the score (will be shown in P5), the timer (will be shown in P5), millis (used for when the force sensors are pressed), random number (used for making random number equal to millis) , button state (to identify the starting of the game) , and pre button state (to identify what would happen before the button is switched). After that in th set-up, in order to time when the LED would be LOW and the sensor must be pressed, we utilized millis, which was set up as the following:
 
  startMillis = millis();  //initial start time
  currentMillis = startMillis;
  ranNum = currentMillis;
 
 Initially, the LEDs were not flashing randomly, however, we implemented the random code, and after a long process of trial and error, we were able to flash the LEDs randomly. After that we began the serial, and started to set up each LED as the output, and the buttonPin to be the input. In the loop we stated that the LED would be HIGH in the begininng, then if the switch is turned on (HIGH) the reading of the force sensors will start, and for this we also used the variable bool:
 
    bool isPressed = false;
    bool wrongPress = false;
   
In the loop, we coded for each LEDPins from 1-5 with the randomChoice 1-5 which meant that we had to repeat the code for each force sensor. We stated that if the randomChoice of 1 was pressed for example, and the LED 1 was low and the force sensor is greater than 500 which indicates that it is being pressed, then isPressed would be = true which meant that they would get a point:

     // Do this for each LED
      if (randomChoice == 1) {
        digitalWrite(ledPin1, LOW);
        if (analogRead(forcePin4) > 500) {
          isPressed = true;
        }

Then we coded a code that was similar for when a point would get deducted. We stated that for example if randomChoice 2 was pressed and any of the force sensor were greater than 500 then wrongPress would be = true. Here, we used wrongPress instead of isPressed, and we did not state that the LED would be turned off so if they clicked any LED while on then they would lose a point. Before we came to the wrong press we made sure to also re-write that currentMillis was equal to millis.
 
       if (randomChoice == 2 && (analogRead(forcePin1) > 500 || analogRead(forcePin3) > 500) || analogRead(forcePin4) > 500 || analogRead(forcePin5) > 500) {
        wrongPress = true;
      }
 
We then created a print.ln for both of them by stating that is isPressed is true then serial will print yes and if wrongPressed is true then serial will print no. The season we did that was for then to use this for writing out the code for the points in P5. Finally we created the else if statement which says that if the button is turned off then the game would restart (part of this code is also written in p5) and that if it's turned off then the LEDs will be back to HIGH (turned on).

# Coding process of testing force sensor:

![testing](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%20code.jpg)
 
# Final Code for P5:

[Final Code](https://editor.p5js.org/shamsasaeed/sketches/VDBsDVftM)

## Code explanation: P5.js
 
 For P5, we first added the p5.web-serial.js folder and added <script src="p5.web-serial.js"></script> in the html before starting the code. We then added the assets we wanted to use which included three images for background, sound, and a font. In the sketch.js we started by declaring variables that included the three images picnicImg (game background), winImg (win background), loseImg (lose background), font (for text) , music (background sound for game), timer (timer for game 30seconds), score (score display for game), gameState (used for declaring gameStae 1-3). Then we set up serial in keyPressed function, and created a doubleClicked function saying that if game state 2 or 3 (win or lose screens) came up then the player would have to double click to restart the game. We didn't know how to set this up, but once we got it we were glad.
 
The most important next step was the readSerial(data) which made P5 read data from arduino that included "yes" and "no" which we explained in the arduino code that "yes" would give a point since it indicated that the force was pressed when the LED was LOW. The "no" would deduct a point since it indicated that force was pressed when the LED is on. I also used "start game" and "end game"  in arduino where start game is for when the switch is turned on (HIGH) and end game is for when the switch is off (LOW). Ite 1 put an else if statement in P5 which said that if the P5 reads "yes" from arduino then the score would increase if P5 read "no" from arduino then score would decrease. Also that if the data reads "start game" then the game state will be 1 which means that game will start, if the data reads "end game" then game state will be 0 where the game isn't started but the background and text is displayed.

   if (data == "yes" && gameState == 1) {
    score++;
  } else if (data == "no" && gameState == 1) {
    score--;
  } else if (data == "start game") {
    gameState = 1;
  } else if (data == "end game") {
    resetGame();
    gameState = 0;
  }
 
The 'You Win'/'You Lose' aspect to the P5 code would work after the duration of the game has ended (30 seconds), if the player gets below 2 points, 'You Lose' is printed on the screen.
 
  if (gameState == 2) {
    image(loseImg, 0, 0, 600, 600);
    textFont(fon
    fill(255, 255, 255);
    textSize(50);
    fill("white"); // time and color text white
    text("YOU LOSE! DOUBLECLICK TO RESTART :" + score, width / 47, height / 2);
 
 However, if a player gets above 2 points 'you win' is printed on the screen. The code is as follows:
 
   if (gameState == 3) {
    image(winImg, 0, 0, 600, 600);
    textFont(font);
    fill(255, 255, 255);
    textSize(50);
    fill("white"); // time and color text white
    text("YOU WIN! DOUBLE CLICK TO RESTART :" + score, width / 47, height / 2);
   
For the function draw, we just wrote what we wanted to display, this part wasnt hard since we already inserted the assets, data, and score. Finally for the reset at the end we made sure to reset the score and timer after the game ended.
   
## Soldering Process:

Initially, we wanted to solder the game for a cleaner final product. However, we faced many hardships during this process. When soldering, some wires were loose and because of this, a short circuit was created as the loose wires were touching other wires. This was brought to our attention as when we went to connect the arduino to the laptop and run the code, the light on the arduino would not turn on. We tried multiple techniques to fix this, such as restarting the laptop, however, it did not work. Moreover, we soon came to discover that the positive and negatives (Ground and 5V) were connected together. We learned what connection it was using a multimeter from professor Aaron's advice. After detecting this, we tried to fix the issue by re-soldered the wires until there was no longer a short circuit. When re-connected the laptop, the arduino turned on, however, only one LED (out of the 5) was HIGH. This proved that the LED connections were not soldered properly, and there was a mistake in the soldering. We tried to fix most of the LEDs but because they weren't soldered very precisely they did not respond to the code very well. We were very annoyed because we have worked on the soldering for two days and it took a lot of time and effort. But we at least, had a chance to practice soldering and knowing how to use it properly since our soldering at the bottom of the solering was pretty good. Due to lack of time, we decided not to present out the soldered board in the final showcase and present our regular breadboard connection, which worked out in our favor, as the game was fully functioning with no errors.

![solder](https://github.com/shamsasaeed/ssa8778/blob/main/solder.jpg)
![solder2](https://github.com/shamsasaeed/ssa8778/blob/main/solder%202.jpg)
![solder2](https://github.com/shamsasaeed/ssa8778/blob/main/solder%203.jpg)

# Design:

As the game concept was surrounded around a picnic, we decided to place the game on a picnic basket on fake grass, in order to mimic a picnic. As for the ants, we made them out of hot glue, and painted them with black acrylic paint, and stuck googly eyes on them. We also hot-glued flowers and filled the basket with bubble wrap for a fuller effect. On top of the bubble wrap, we round placed white design papers and then placed the Arduino board on top, and placed the Arduino on the grass and tried to hide it. We also used long wires to cover up teh wires which looked nice. We then made and printed out a green sign that said 'FLASHING BUGS' and glued it to a stick, which was placed in the basket. We also made a sign which reads "PRESS THE BUG SPRAY WHEN THE ANTS LIGHT UP!" and placed that in front of the breadboard. We really liked the design and got many compliments on it which made us proud.

![design1](https://github.com/shamsasaeed/ssa8778/blob/main/design.jpg)
![design2](https://github.com/shamsasaeed/ssa8778/blob/main/design%202.jpg)
![design3](https://github.com/shamsasaeed/ssa8778/blob/main/design%203.jpg)

# Conclusion:

In conclusion, me and my partner would have never dreamed of creating something like this on our own. The building, the soldering, the coding, the entire process was a big challenge that we overcame. Although we experienced many errors and struggles, we managed to get beyond them all and create a beautiful output that was worked very hard on. There are many things we would have liked to change or implement if we had more time, such as fixing the soldering for the final design, or adding a sound effect when the ants are being squished. However, we are bith very proud for how far we've come since starting the final, and we've learned more than we could have anticipated through this journey.

![conclusion1](https://github.com/shamsasaeed/ssa8778/blob/main/conclusion.jpg)
![conclusion2](https://github.com/shamsasaeed/ssa8778/blob/main/conclusion%202.jpg)
![conclusion3](https://github.com/shamsasaeed/ssa8778/blob/main/conclusion%203.jpg)
![conclusion4](https://github.com/shamsasaeed/ssa8778/blob/main/conclusion%204.jpg)
![conclusion5](https://github.com/shamsasaeed/ssa8778/blob/main/conclusion%205.jpg)

# Final Result Game DEMO:

[CLICK ME TO SEE GAME DEMO IN CLASS SHOW](https://youtube.com/shorts/vgvi5tsESYs?feature=share)

# CODE: P5.js

![P51](https://github.com/shamsasaeed/ssa8778/blob/main/p5%201.png)
![P52](https://github.com/shamsasaeed/ssa8778/blob/main/p5%202.png)
![P53](https://github.com/shamsasaeed/ssa8778/blob/main/p5%203.png)
![P54](https://github.com/shamsasaeed/ssa8778/blob/main/p5%204.png)

# CODE: Arduino

![Arduino1](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%201.png)
![Arduino2](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%202.png)
![Arduino3](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%203.png)
![Arduino4](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%204.png)
![Arduino5](https://github.com/shamsasaeed/ssa8778/blob/main/arduino%205.png)

# Refrences
[Bool](https://www.arduino.cc/reference/en/language/variables/constants/constants/g)
[ArduinoXP5](https://medium.com/@yyyyyyyuan/tutorial-serial-communication-with-arduino-and-p5-js-cd39b3ac10ce)
[Random](https://forum.arduino.cc/t/random-led-blink-code-check/106834)
[Millis](https://forum.arduino.cc/t/using-millis-for-timing-a-beginners-guide/483573)
[Aaron](https://editor.p5js.org/aaronsherwood/sketches/q2Pl77SWl) 
