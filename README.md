# line-fallower-code-for-3-IR-sensors

const int rm1 = 7; // signal pin 1 for the right motor, connect to IN3               
const int rm2 = 6;  // signal pin 2 for the right motor, connect to IN4
const int re = 5; // enable pin for the right motor (PWM enabled)

const int lm1 = 8; // signal pin 1 for the left motor, connect to IN1           
const int lm2 = 9; // signal pin 2 for the left motor, connect to IN2
const int le = 10;// enable pin for the left motor (PWM enabled) 


int sensorleft = A1; // Assigning the analog pin 1 to left sensor
int sensorcenter = A3;// Assigning the analog pin 2 to center sensor
int sensorright = A5; // Assigning the analog pin 3 to right sensor


int left=1; // To store the left sensor data 
int center=1; // To store the center sensor data
int right=1; // To store the right sensor data


void setup()
{
Serial.begin(9600); // To start Serial communication to access sensor data
 pinMode(rm1,OUTPUT); // Assigning right motor's control signal as output
 pinMode(lm1,OUTPUT); // Assigning right motor's control signal as output
 pinMode(rm2,OUTPUT); // Assigning left motor's control signal as output
 pinMode(lm2,OUTPUT); // Assigning left motor's control signal as output

 pinMode(re,OUTPUT); // Assigning right motor's PWM control signal as output
 pinMode(le,OUTPUT); // Assigning left motor's PWM control signal as output


 pinMode(sensorleft,INPUT); // Assigning left Sensor output signal as input
 pinMode(sensorcenter,INPUT); // Assigning center Sensor output signal as input
 pinMode(sensorright,INPUT); // Assigning right Sensor output signal as input

}

void loop()
{
left=digitalRead(sensorleft); // Reading the digital data from the left sensor 
center=digitalRead(sensorcenter); // Reading the digital data from the center sensor
right=digitalRead(sensorright); // Reading the digital data from the right sensor
Serial.print(left); // Displaying the digital data from the left sensor
Serial.print("  "); // To provide space
Serial.print(center); // Displaying the digital data from the center sensor
Serial.print("  "); // To provide space
Serial.print(right); // Displaying the digital data from the right sensor
Serial.println("  "); // To provide space
  analogWrite(le,75);//To set the speed of left motor
  analogWrite(re,75);//To set the speed of right motor

if(left==1&&center==0&&right==0||left==1&&center==1&&right==0)   //left turn
{
  if(left==0&&center==0&&right==0)
  {
  Serial.println("Turning left");
  
  analogWrite(le,0);//To set the speed of left motor
  analogWrite(re,70);//To set the speed of right motor

  digitalWrite(rm1,1);
  digitalWrite(rm2,0);
  digitalWrite(lm1,0);
  digitalWrite(lm2,0);
}
analogWrite(le,0);//To set the speed of left motor
  analogWrite(re,70);//To set the speed of right motor

  digitalWrite(rm1,1);
  digitalWrite(rm2,0);
  digitalWrite(lm1,0);
  digitalWrite(lm2,0);
}
else
if(left==0&&center==0&&right==1||left==0&&center==1&&right==1)  //right turn
{
  if(left==0&&center==0&&right==0)
  {
   analogWrite(le,70);//To set the speed of left motor
  analogWrite(re,0);//To set the speed of right motor

  digitalWrite(rm1,0);
  digitalWrite(rm2,0);
  digitalWrite(lm1,1);
  digitalWrite(lm2,0); 
  }
  Serial.println("Turning right");

  analogWrite(le,70);//To set the speed of left motor
  analogWrite(re,0);//To set the speed of right motor

  digitalWrite(rm1,0);
  digitalWrite(rm2,1);
  digitalWrite(lm1,0);
  digitalWrite(lm2,0);
}
else
if(left==0&&center==1&&right==0)  //go forward straight

{
  Serial.println("Going straight");

  analogWrite(le,150);//To set the speed of left motor
  analogWrite(re,150);//To set the speed of right motor

  digitalWrite(rm1,1);
  digitalWrite(rm2,0);
  digitalWrite(lm1,1);
  digitalWrite(lm2,0);
}
else
if(left==1&&center==1&&right==1) //stop
{
  Serial.println("Stop");

  analogWrite(le,100);//To set the speed of left motor
  analogWrite(re,100);//To set the speed of right motor
  digitalWrite(rm1,0);
  digitalWrite(rm2,0);
  digitalWrite(lm1,0);
  digitalWrite(lm2,0);
}
//else
//if(left==0&&center==0&&right==0) // 180° turn
//{
//  analogWrite(le,100);//To set the speed of left motor
//  analogWrite(re,100);//To set the speed of right motor
//
//  digitalWrite(rm1,0);
//  digitalWrite(rm2,1);
//  digitalWrite(lm1,0);
//  digitalWrite(lm2,1);
//}
}
using arduino nano microcontroller
