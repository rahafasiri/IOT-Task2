# IOT TASK 2
![1](https://github.com/rahafasiri/IOT-Task2/assets/139389205/33c4c419-fe65-4f7e-9275-fe69863c4d54)
![تنزيل](https://github.com/rahafasiri/IOT-Task2/assets/139389205/ffc94fd8-d96f-4169-b63f-1635cbcc912c)
# Arduino 1
#include <Wire.h>
int pushButton = A0;
int x = 0;
void setup()
{
  Wire.begin();
  pinMode(pushButton, INPUT);
}

void loop()
{
   Wire.beginTransmission(1);
   x = digitalRead(pushButton);
   Wire.write(x);
   Wire.endTransmission();
   delay(500);
}
# Arduino 2
#include <Wire.h>
int pinLed=13;
int x =0;

void setup()
{
  Wire.begin(1);
  Wire.onReceive(receiveEvent); 
  pinMode(pinLed, OUTPUT);
}

void loop()
{
  delay(100);
}

void receiveEvent(int howMany){

x = Wire.read();

  if (x == 1){

        digitalWrite(pinLed,HIGH);
  }
  else{
        digitalWrite(pinLed,LOW);
  }
}

