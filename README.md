# RC-Cara-Arduino-Control
This project uses an ultrasonic sensor that detects if the RC car will crash by checking the left and right, then choosing the direction that is more empty than the other.
## Features:
-Bluetooth control that sends the distance of the nearest possible crash to the mobile application that was created by MIT app inventor
-Obstacle detection using an ultrasonic sensor
-Simple, easy-to-use mobile app
## Hardware
1. Connect the Bluetooth module to the Arduino (TX, RX, and power connections).
2. Attach the ultrasonic sensor to the Arduino according to the wiring diagram.
3. Power up the system.
## Software
1. Clone or download this repository.
2. Open the Arduino code in the Arduino IDE and upload it to your board.
## Demo
Check out a demo of the project in action: [https://www.youtube.com/shorts/AeQrUgJGdnE]. Apologies for the sound.


## Here is the code for the RC car

#include <Servo.h>
#include <NewPing.h>

//L298N motor control pins

const int LMF = 13;
const int LMB = 12;
const int RMF = 11;
const int RMB = 10;

//sensor pins
#define trig_pin 4
#define echo_pin 5

#define maximum_distance 200
boolean goesForward = false;
int distance = 100;

NewPing sonar (trig_pin , echo_pin , maximum_distance);
Servo servo_motor 

Void setup () {

pinMode (RMF, OUTPUT);
pinMode (LMF, OUTPUT);
pinMode (LMB, OUTPUT);
pinMode (RMB, OUTPUT);

servo_motor.attach (9) ;

servo motor.write (115) ;
delay (2000) ;
distance = readPing ();
delay (100) ;
distance = readPing ():
deley (100) ;
distance = readPing ();
delay (100) ;
distance = readPing ();
delay(100);
}

void loop () {

int distanceRight = 0;
ine distanceleft - 0,
delay (50) ;

if (distance <= 40) {
moveStop () ;
delay (300) ;
morve Backward () ;
delay (400);
moveStop ();
delay (300) ;
distanceRight = LookRight ();
delay (300) ;
distanceLeft = lookLeft () ;
delay (300) ;

if (distance >= distanceLeft) {
turnRight ();
moveStop() ;
}
else{
turnLeft();
movestop();
}
}
else{
moveForward();
}
distance = readPing ();
}

int lookRight () {
servo_motor.write (60) ;
delay (500) ;
int distance = readPing () ;
delay (100) ;
servo_motor.write (115);
return distance;
}

int lookLeft () {
servo_motor.write (170) ;
delay (500) ;
int distance = readPing () ;
delay (100) ;
servo_motor.write(115);
return distance;
delay (100) ;
}

int readPing() {
delay(70);
int cm = sonar.ping_cm();
if (cm==0){
cm=250;
}
return cm;
}

void moveStop () {
digitalWrite (RMF, LOW);
digitalWrite (LMF, IOW) :
digitalWrite (RMB, IOW) :
digitalvirite (LMB, LOW);
}

void moveForward ( ) {
if ( !goesForward) {

goesForward=true;

digitalWrite (LMF,HIGH);
digitalWrite (RMF, HIGH);

digitalWrite (LMB, LOW);
digitalWrite (RMB, LOW);
}
}

void moveBackward () {

goesForward=false;

digitalWrite (LMB,HIGH);
digitalWrite (RMB,HIGH);

digitalWrite (LMF,LOW);
digitalWrite (RMF,LOW);

}

void turnRight () {

digitalWrite (LMF,HIGH);
digitalWrite (RMB,HIGH);


digitalWrite (LMB,LOW);
digitalWrite (RMF,LOW);

delay(500);

digitalWrite (LMF,HIGH); 
digitalWrite (RMF,HIGH);

digitalWrite (LMB,LOW);
digitalWrite (RMB,LOW);

}

void turnLeft () {

digitalWrite (LMB,HIGH);
digitalWrite (RMF,HIGH);


digitalWrite (LMF,LOW);
digitalWrite (RMB,LOW);

delay(500);

digitalWrite (LMF,HIGH); 
digitalWrite (RMF,HIGH);

digitalWrite (LMB,LOW);
digitalWrite (RMB,LOW);

}



