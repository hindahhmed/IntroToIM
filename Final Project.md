# FINAL PROJECT #

#  Flashing Bugs!

## Inspiration and Game Concept

My partner Shamsa and I got inspired by a very addicting childhood game we both loved to play called "Hit the Beaver". In the game there were a bunch of beavers popping up in the screen where the player had to hit them to get a point. We thought that it would be really cool to try and re-create this but in real life format, which we got really excited about. We switched it up a bit by deciding to create insects using the LEDs instead of beavers and using force sensors to destroy these insects instead of hitting them, and of course getting a point when destroying the bugs/insects on time.

## How Arduino And P5 Are Connected

In the Arduino, we have set up the game on the board and this will include five LEDs and five force sensors, resistors, and a button to start the game. For the Arduino code, we coded that the game would start when the button gets pressed on, the duration and blinking of the LED lights, and the points dispalying 0 when teh force isn't touched, and displaying 1 when the force sesnor is touched while the LED light is on.

## Summary concept of the Game:

For the game, the player has to flip the switch for the game to begin. When the switch is flipped, the LED lights will turn on. The player would then have to touch the force sensors on time where the LED is turned off, and when the player has done so, they will have a point. However, if the player presses a sensor for an LED that is on, a point will be deducted. 


## Some important contributers we used in our Arduino board and both codes:

- LEDs
- Button/Switch 
- Force Sensors
- Resistors
- Wires.
- If Statements
- Loops

## Coding proccess:

Even though putting up the circuit in the Arduino board took a long while, the coding process we would say has been the hardest part in this project. The first part of the Arduino coding of making the LEDs flash, the button working, and the force having a response to its corresponding LED had its challenges but they were easy to overcome. However, as aforementioned, we faced difficulty when it came to the force sensors. In particular, when it came to coding how the player would get a point when pressing the force sensor when the LED was low. When we initially started coding this function, the values given out when the force sensor was pressed were very high, and did not correlate to a point. 
However, once we had our circuit working we started working with the rest of the Arduino code that we had to do to link it to P5, this was the most part we struggled with. The merging of sending Arduino to P5 has been a bit tricky for the both of us, but while researching, and testing the codes we mananged to make it work by also going through Github with the resources as well as going through old p5 and Arduino codes where we found bits and pieces of extra help from.

## Hardships during coding process:

We have faced many hardships during the coding process. The first issue was that we had countless errors that said that the port was not connected to the Arduino which we had to adjust multiple times, through finding the correct port and connecting it. Moreover, our sensors did not work, the hqrdwiring was correct, however, the code itself was not working. Through asking for help from the Professor, we were able to connect the sensors to the LED, and create a point system in which when the LED was low and the sensor was pressed, the player would get a point. We checked in the sensors were working through serial montering and checking the numbers. We utilized 0s and 1s to monitor this. If the sensor was pressed and a 1 was printed, we were able to see that it works. The code for the sensors is:

if (randomChoice == 1) {
        digitalWrite(ledPin4, LOW);
        if (analogRead(forcePin4) > 500) {
          isPressed = true;
        }
        
 ## Code explanation:
        
 In order to time when the LED would be low and the sensor must be pressed, we utilized millis, which was set up as the following: 
 
  startMillis = millis();  //initial start time
  currentMillis = startMillis;
  ranNum = currentMillis;
  
 Initially, the LEDs were not flashing randomly, however, we implemented the random code, and after a long process of trial and error, we were able to flas the LEDs randomly.  
 
 Last minute, we decided to add a 'You Win'/'You Lose' aspect to the P5 code. After the duration of the game has ended (30 seconds), if the player gets below 2 points, 'You Lose' is printed on the screen. 
 
  if (gameState == 2) {
    image(loseImg, 0, 0, 600, 600);
    textFont(font);
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
   
 

## Soldering Process: 

Initially, we wanted to solder the game for a cleaner final product. However, we faced many hardships during this process. When soldering, some wires were loose and because of this, a short circuit was created as the lose wires were touching other wires. This was brought to our attention as when we went to connect the arduino to the laptop and run the code, the arduino would not turn. We tried multipul techniques to fix this, such as restarting the laptop, however, it did not work. Moreover, we soon came to discover that the positive and negatives (ground and 5 volts) were connected together. We learned what connection it was utilizing a multimeter. After detecting this, we re-soldered the wires and there was no longer a short circuit. When when re-connected the laptop, the arduino turned on, however, only one LED (out of the 5) was high. This proved that the LED connections were not soldered properly w
and there was a mistake in the soldering. Due to lack of time, we decided not to present out soldered board in the final showcase and present our regular breadboard connection, which worked out in our favor, as the game was fully functioning with no errors. 

# Conclusion:

In conclusion, me and my partner would have never dreamed of creating something like this on our own. The building, the soldering, the coding, the entire process was a big challenge that we overcame. Although we experienced many errors and struggles, we managed to get beyond them all and create a beautiful output that was worked very hard on. There are many things we would have liked to change or implement if we had more time, such as fixing the soldering for the final design, or adding a sound effect when the ants are being squished. However, we are bith very proud for how far we've come since starting the final, and we've learned more than we could have anticipated through this journey. 

# Design: 

As the game concept was surrounded around a picnic, we decided to place the game on a picnic basket on fake grass, in order to mimic a picnic. As for the ants, I made them out of hot glue, and painted them with black acrylic paint, and stuck googly eyes on them. I also hot glued flowers and filled the basket with bubble wrap for a fuller effect. I then made a sign reading 'FLASHING BUGS' and glued it to a stick, which I placed in the basket. I also make a sign which reads "PRESS THE BUG SPRAY WHEN THE ANTS LIGHT UP!" and placed that in front of the breadboard. 

![design1](https://github.com/hindahhmed/IntroToIM/blob/main/images/IM%20FINAL/IMG_3708.HEIC)


# Final result output:

[CLICK ME TO SEE GAME DEMO](https://youtube.com/shorts/vgvi5tsESYs?feature=share)



# Final result Code:

![final code 1](not yet added)

# P5.js

let picnicImg;
let winImg;
let loseImg;
let font, music;
let force;
let timer = 30; // time limit for game
let score = 0;
let gameState = 0;
function keyPressed() {
  if (key == " ") {
    // important to have in order to start the serial connection!!
    setUpSerial();
  }
}

function doubleClicked() {
  if (gameState==2|| gameState==3) {
    gameState=1;
  }
}

function readSerial(data) {
  //READ FROM ARDUINO HERE
  if (data == "yes" || data == "no" || data == "start game" || data == "end game"){
    print(data)
  }
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
}

function preload() {
  picnicImg = loadImage("assets/picnic.jpeg");
  loseImg = loadImage("assets/lose.jpg");
  winImg = loadImage("assets/win.jpg");
  music = loadSound("assets/picnicmusic.mp3");
  font = loadFont("assets/BebasNeue-Regular.ttf");
}
function setup() {
  createCanvas(600, 600);
}
function draw() {
  if (gameState == 1 || gameState == 0) {
   
    background(220);
    image(picnicImg, 0, 0, 600, 600);
    if (!music.isPlaying()) {
      music.play();
    }
    textFont(font);
    fill(255, 255, 255);
    textSize(100);
    textFont(font); // text font and size display
    fill("white"); // time and color text white
    text("score :" + score, width / 47, height / 2); // points display
    textSize(25);
    text("timer :" + timer, 255, 380); // time display
  }
  if (gameState == 1) {
    if (frameCount % 60 == 0 && timer > 0) {
      timer--;
    } // timer set

    if (timer == 0) {
    if (score <= 0) {
      gameState = 2;
    }
      else {
        gameState = 3;
      }
      resetGame();
     

     
    } // if timer became 0 then game would reset
  }
 
  if (gameState == 2) {
    image(loseImg, 0, 0, 600, 600);
    textFont(font);
    fill(255, 255, 255);
    textSize(50);
    fill("white"); // time and color text white
    text("YOU LOSE! DOUBLECLICK TO RESTART :" + score, width / 47, height / 2);
   
  }
 
   if (gameState == 3) {
    image(winImg, 0, 0, 600, 600);
    textFont(font);
    fill(255, 255, 255);
    textSize(50);
    fill("white"); // time and color text white
    text("YOU WIN! DOUBLE CLICK TO RESTART :" + score, width / 47, height / 2);
   
  }
  // if (!serialActive) {
  //   text("", 20, 30);
  // }
}

function resetGame() {
  timer = 30; // when game resets time goes back to 5 seconds
  score = 0; // when game resets poiints goes back to 0
}

# ARDUINO 

const int buttonPin = 12;     // pushbutton pin number
const int ledPin1 =  5;      // LED pin number
const int ledPin2 =  6;      // LED pin number
const int ledPin3 =  7;      // LED pin number
const int ledPin4 =  8;      // LED pin number
const int ledPin5 =  9;      // LED pin number
const int forcePin1 = A3;
const int forcePin2 = A0;
const int forcePin3 = A2;
const int forcePin4 = A1;
const int forcePin5 = A4;
int  ranNum;
int  ranDel;
int startMillis;
int currentMillis;
int score = 0;
int timer = 0;


// variables declare:
int buttonState = 0;         // pushbutton state variable
int preButtonState;

void setup() {

  startMillis = millis();  //initial start time
  currentMillis = startMillis;
  ranNum = currentMillis;

  Serial.begin(9600);
  //  pinMode(2, OUTPUT);
  //  pinMode(5, OUTPUT);
  //  // start the handshake
  //  while (Serial.available() <= 0) {
  //    Serial.println("0,0"); // send a starting message
  //    delay(300);            // wait 1/3 second
  ////  }

  // LED pin output:
  pinMode(ledPin1, OUTPUT);
  // pushbutton pin input:
  pinMode(buttonPin, INPUT);

  pinMode(ledPin2, OUTPUT);
  // pushbutton pin input:
  pinMode(buttonPin, INPUT);

  pinMode(ledPin3, OUTPUT);
  // pushbutton pin input:
  pinMode(buttonPin, INPUT);

  pinMode(ledPin4, OUTPUT);
  // pushbutton pin input:
  pinMode(buttonPin, INPUT);

  pinMode(ledPin5, OUTPUT);
  // pushbutton pin input:
  pinMode(buttonPin, INPUT);
  preButtonState = digitalRead(buttonPin);
}

void loop() {

  // pushbutton value state
  buttonState = digitalRead(buttonPin);

  digitalWrite(ledPin1, HIGH);
  digitalWrite(ledPin2, HIGH);
  digitalWrite(ledPin3, HIGH);
  digitalWrite(ledPin4, HIGH);
  digitalWrite(ledPin5, HIGH);

  //  if pushbutton is pressed then thebuttonState is HIGH:
  if (buttonState == HIGH) {
    if (preButtonState == LOW) {
      Serial.println("start game");
      preButtonState = HIGH;
    }
    bool isPressed = false;
    bool wrongPress = false;
    startMillis = millis();
    currentMillis = startMillis;
    //  Serial.println(score);
    int randomChoice = random(1, 6);
    //  Serial.print("Choice : ");
    //  Serial.println(randomChoice);
    //
    //    Serial.print(analogRead(forcePin1));
    //    Serial.print(",");
    //    Serial.print(analogRead(forcePin2));
    //    Serial.print(",");
    //     Serial.print(analogRead(forcePin3));
    //    Serial.print(",");
    //     Serial.print(analogRead(forcePin4));
    //    Serial.print(",");
    //     Serial.println(analogRead(forcePin5));
    ////    Serial.print(",");

    while (currentMillis - startMillis < 2000) {

      // do this for each led
      if (randomChoice == 1) {
        digitalWrite(ledPin4, LOW);
        if (analogRead(forcePin4) > 500) {
          isPressed = true;
        }

      }
      if (randomChoice == 2) {
        digitalWrite(ledPin2, LOW);
        if (analogRead(forcePin2) > 500) {
          isPressed = true;
        }

      }
      if (randomChoice == 3) {
        digitalWrite(ledPin3, LOW);
        if (analogRead(forcePin3) > 500) {
          isPressed = true;
        }
      }
      if (randomChoice == 4) {
        digitalWrite(ledPin4, LOW);
        if (analogRead(forcePin4) > 500) {
          isPressed = true;
        }
      }

      if (randomChoice == 5) {
        digitalWrite(ledPin5, LOW);
        if (analogRead(forcePin5) > 500) {
          isPressed = true;
        }
      }

      currentMillis = millis();


      if (randomChoice == 2 && (analogRead(forcePin1) > 500 || analogRead(forcePin3) > 500) || analogRead(forcePin4) > 500 || analogRead(forcePin5) > 500) {
        wrongPress = true;
      }

      if (randomChoice == 1 && (analogRead(forcePin2) > 500 || analogRead(forcePin3) > 500) || analogRead(forcePin4) > 500 || analogRead(forcePin5) > 500) {
        wrongPress = true;
      }

      if (randomChoice == 3 && (analogRead(forcePin1) > 500 || analogRead(forcePin2) > 500) || analogRead(forcePin4) > 500 || analogRead(forcePin5) > 500) {
        wrongPress = true;
      }

      if (randomChoice == 4 && (analogRead(forcePin1) > 500 || analogRead(forcePin3) > 500) || analogRead(forcePin2) > 500 || analogRead(forcePin5) > 500) {
        wrongPress = true;
      }

      if (randomChoice == 5 && (analogRead(forcePin1) > 500 || analogRead(forcePin3) > 500) || analogRead(forcePin4) > 500 || analogRead(forcePin2) > 500) {
        wrongPress = true;
      }
    }

    if (isPressed == true) {
      Serial.println("yes");

    } else if (wrongPress == true) {
      Serial.println("no");
    }

  }
 
  else {
    if (preButtonState == HIGH) {
      Serial.println("end game");
      preButtonState = LOW;
    }
    // LED ON:
    digitalWrite(ledPin1, HIGH);
    digitalWrite(ledPin2, HIGH);
    digitalWrite(ledPin3, HIGH);
    digitalWrite(ledPin4, HIGH);
    digitalWrite(ledPin5, HIGH);
    score = 0;
  }



  //  // NEW ATTEMPT

  //
  //  if (randomChoice == 2) {
  //    digitalWrite(ledPin2, HIGH);
  //    if (analogRead(forcePin2) < 500) {
  //      score--;
  //    }
  //  }
  //  if (randomChoice == 3) {
  //    digitalWrite(ledPin1, HIGH);
  //    if (analogRead(forcePin1) < 500) {
  //      score--;
  //    }
  //  }
  //
  //  if (randomChoice == 4) {
  //    digitalWrite(ledPin4, HIGH);
  //    if (analogRead(forcePin4) < 500) {
  //      score--;
  //    }
  //  }
  //
  //  if (randomChoice == 5) {
  //    digitalWrite(ledPin5, HIGH);
  //    if (analogRead(forcePin5) < 500) {
  //      score--;
  //    }
  //  }

  //  digitalWrite(ledPin1, HIGH);
  //  digitalWrite(ledPin2, HIGH);
  //  digitalWrite(ledPin3, HIGH);
  //  digitalWrite(ledPin4, HIGH);
  //  digitalWrite(ledPin5, HIGH);

  //serial send to p5



}
