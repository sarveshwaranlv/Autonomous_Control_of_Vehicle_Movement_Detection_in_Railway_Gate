# Autonomous_Control_of_Vehicle_Movement_Detection_in_Railway_Gate

  #include <Servo.h>

  #define IR01 2

  #define IR02 3

  #define US01T 5

  #define US01E 6

  #define US02T 7

  #define US02E 8

  #define US03T 9

  #define US03E 10

  #define US04T 11

  #define US04E 12

  #define RED A4

  #define GREEN A5

  #define BUZZ 13

  Servo SM01;

  Servo SM02;

  Servo SM03;

  Servo SM04;

  int OPEN = 90;

  int CLOSE1 = 0;

  int CLOSE2 = 180;

  long TIME01, DIST01, TIME02, DIST02, TIME03, DIST03, TIME04, DIST04;

  int motionDetected = 0;

void setup() 

{

  SM01.attach(A0);
  
  SM02.attach(A1);
  
  SM03.attach(A2);
  
  SM04.attach(A3);
  
  pinMode(IR01, INPUT);
  
  pinMode(IR02, INPUT);
  
  pinMode(US01T, OUTPUT);
  
  pinMode(US01E, INPUT);
  
  pinMode(US02T, OUTPUT);
  
  pinMode(US02E, INPUT);
  
  pinMode(US03T, OUTPUT);
  
  pinMode(US03E, INPUT);
  
  pinMode(US04T, OUTPUT);
  
  pinMode(US04E, INPUT);
  
  
  pinMode(RED, OUTPUT);
  
  pinMode(GREEN, OUTPUT);
  
  pinMode(BUZZ, OUTPUT);
  
  
  SM01.write(OPEN);
  
  SM02.write(OPEN);
  
  SM03.write(OPEN);
  
  SM04.write(OPEN);
  
  
  Serial.begin(9600);
  
}

void loop() 

{

  digitalWrite(US01T, LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(US01T, HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(US01T, LOW);
  
  TIME01 = pulseIn(US01E, HIGH);
  
  DIST01 = (TIME01 / 2) * 0.0344;

  digitalWrite(US02T, LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(US02T, HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(US02T, LOW);
  
  TIME02 = pulseIn(US02E, HIGH);
  
  DIST02 = (TIME02 / 2) * 0.0344;

  digitalWrite(US03T, LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(US03T, HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(US03T, LOW);
  
  TIME03 = pulseIn(US03E, HIGH);
  
  DIST03 = (TIME03 / 2) * 0.0344;

  digitalWrite(US04T, LOW);
  
  delayMicroseconds(2);
  
  digitalWrite(US04T, HIGH);
  
  delayMicroseconds(10);
  
  digitalWrite(US04T, LOW);
  
  TIME04 = pulseIn(US04E, HIGH);
  
  DIST04 = (TIME04 / 2) * 0.0344;
  
  Serial.print("DIST01: ");
  
  Serial.print(DIST01);
  
  Serial.println(" cm");
  
  Serial.print("DIST02: ");
  
  Serial.print(DIST02);
  
  Serial.println(" cm");

  Serial.print("DIST03: ");
  
  Serial.print(DIST03);
  
  Serial.println(" cm");
  
  Serial.print("DIST04: ");
  
  Serial.print(DIST04);
  
  Serial.println(" cm");

  if (digitalRead(IR01) == LOW) 
  
  {
  
  Serial.println("Train detected. Closing the gate.");
  
  SM01.write(CLOSE1);
  
  SM02.write(CLOSE2);
  
  SM03.write(CLOSE1);
  
  SM04.write(CLOSE2);
  
  }

   if (digitalRead(IR02) == LOW) 
   
   {
   
   Serial.println("Train approaching. Opening the gate.");
   
   SM01.write(OPEN);
   
   SM02.write(OPEN);
   
   SM03.write(OPEN);
   
   SM04.write(OPEN);
   
   }
 
   if (DIST01 <= 3 || DIST04 <= 3) 
   
   {
   
   Serial.println("Move Away from the gate");
   
   alarm1();
   
   } 
  
   else if (DIST02 <= 3 || DIST03 <= 3) 
   
   {
   
   Serial.println("Move Away from the gate");
   
   alarm2();
   
   }  

   else if ((DIST02 <= 3 || DIST03 <= 3) && (DIST01 <= 3 || DIST04 <= 3)) 
   
   {
   
   Serial.println("Move Away from the gate");
   
   alarm3();
   
   } 
  
   else
   {
   
   digitalWrite(RED, LOW);
   
   digitalWrite(GREEN, LOW);
   
   }
   
   }

   void alarm1()
   
   {
   
   if (digitalRead(IR01) == LOW)
   
   {
   
   tone(BUZZ, 500);delay(500);noTone(BUZZ);
   
   digitalWrite(RED, HIGH);
   
   digitalWrite(GREEN, LOW);
   
   SM01.write(OPEN);
   
   delay(5000);
   
   SM01.write(CLOSE1);
   
   }
   
   else
   
   {}
   
   }

  void alarm2()
    
   {
   
   if (digitalRead(IR01) == LOW)
   
   {
   
   tone(BUZZ, 500);delay(500);noTone(BUZZ);
   
   digitalWrite(RED, HIGH
   
   digitalWrite(GREEN, LOW);
   
   SM03.write(OPEN);
   
   delay(5000);
   
   SM03.write(CLOSE1);
   
   }
   
   else
   
   {}
   
   }

   void alarm3()
   
   {
   
   if (digitalRead(IR01) == LOW)
   
   {
   
    tone(BUZZ, 500);delay(500);noTone(BUZZ);
    
   digitalWrite(RED, HIGH);
   
   digitalWrite(GREEN, LOW);
   
   SM01.write(OPEN);
   
   SM03.write(OPEN);
   
   delay(5000);
   
   SM01.write(CLOSE1);
   
   SM03.write(CLOSE1);
   
   }
   else
   
   {}
   
   }
