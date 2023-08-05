
#define trig 12
#define echo 13
long duration,distance;
int sr=0;
void setup()
{for(int i=5;i<=6;i++){
  pinMode(i,OUTPUT);}
 for(int b=10;b<=11;b++){
  pinMode(b,OUTPUT);}
 pinMode(12,OUTPUT);
 pinMode(13,INPUT);
 Serial.begin(9600);}
  
void Ultrasonic(){
digitalWrite(trig, LOW);
delayMicroseconds(2); 
digitalWrite(trig, HIGH);
delayMicroseconds(10); 
digitalWrite(trig, LOW);
duration = pulseIn(echo, HIGH);
distance = (duration/2) * 0.0343; 
  
}
void loop()
{
Ultrasonic();
  if(distance>=50)digitalWrite(5,HIGH);
  if(distance>100&&distance<=355)
    analogWrite(6,distance-100);
    else
    analogWrite(6,0);
    if(distance>150&&distance<=336.5)
    analogWrite(10,(distance-150)*1.25);
    else
    analogWrite(10,0);
       if(distance>200&&distance<=336.5)
    analogWrite(11,(distance-200)*1.75);
    else
    analogWrite(11,0);
}
