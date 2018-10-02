# Paper Puppets

*A lab report by Chris Brownell*

## In this Report

In this lab, I messed around with a DC motor, a servo motor, and the Stretch paper puppet. I also created an olympic torch puppet and I promise I adhered to all fire safety best practices!

## Part A. Actuating DC motors

**Link to a video of your virbation motor**

Vibrating DC motor [video]()

## Part B. Actuating Servo motors

### Part 1. Connect the Servo to your breadboard

**a. Which color wires correspond to power, ground and signal?**

Orange is signal, Red is power, Brown is ground.

### Part 2. Connect the Servo to your Arduino

**a. Which Arduino pin should the signal line of the servo be attached to?**

Pin 9 for PWM

**b. What aspects of the Servo code control angle or speed?**

Speed is controled by the delay() in the for loops in line 25 and line 29. Angle is simply measured as degrees from 
starting position. By default, sweep covers 180 degrees from starting position. Rather than keeping the raw 180 in the
code I just declared it as a variable. So I only have to change it once for the angle to change.

It seems 180 is the maximum allowed angle by the servo. Changing the angle to 90 has the intended effect but changing it 
to 270 produces the same behavior as 180.

```
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position
int angle = 90;

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 0; pos <= angle; pos += 1) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(20);                       // waits 15ms for the servo to reach the position
  }
  for (pos = angle; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(20);                       // waits 15ms for the servo to reach the position
  }
}
```

## Part C. Integrating input and output

**Include a photo/movie of your raw circuit in action.**

I used the FSR and the following code to make the servo respond to how hard I pressed down.

FSR controlling servo motor - [video]()

```
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position
int angle = 90;

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  myservo.write(map(analogRead(A0),0,1000,0,180));    // tell servo to go to position being read in on A0
  delay(20);                       // waits 20ms for the servo to reach the position
  
}

```

## Part D. Paper puppet

**a. Make a video of your proto puppet.**

Puppet in action! [video]()

## Part E. Make it your own

**a. Make a video of your final design.**

For my design, I was inspired by my multi colored craft paper and leftover birthday candles to make the last leg of 
the olympic torch relay, with a twist. In this futuristic olympic games, the robo-torch lights itself!

![flamestill]()

See video (with sound!) of the robo-torch lighting itself [video]()
 
