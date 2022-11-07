# Arduino-project-code
ECE Arduino project code

code starts from 6th line

/*Developer: Souparna Chowdhury~BongTechSolutions */

#define trigger 9  
#define echo 8
#define RED 2
#define YELLOW 3
#define GREEN 4
#define buzzer 5

float time=0,distance=0;    //Time and Distance variables initialized as 0.
void measure_distance();

void setup() {
 pinMode(trigger,OUTPUT);
 pinMode(echo,INPUT);
 pinMode(RED,OUTPUT);
 pinMode(YELLOW,OUTPUT);
 pinMode(GREEN,OUTPUT);
 pinMode(buzzer,OUTPUT);
 
 delay(2000);              //Delay provided to configure the i/o pins
}

void loop() {
  measure_distance();
 if(distance<10){
  digitalWrite(RED,HIGH);
  digitalWrite(YELLOW,LOW);
  digitalWrite(GREEN,LOW);
  digitalWrite(buzzer,HIGH);
 }
 else if((distance<30)&&(distance>10)){
  digitalWrite(RED,LOW);
  digitalWrite(YELLOW,HIGH);
  digitalWrite(GREEN,LOW);
  digitalWrite(buzzer,LOW);
 }
 else{
  digitalWrite(RED,LOW);
  digitalWrite(YELLOW,LOW);
  digitalWrite(GREEN,HIGH);
  digitalWrite(buzzer,LOW);
 }
}
 

void measure_distance()
{
 digitalWrite(trigger,LOW);
 delayMicroseconds(2);
 digitalWrite(trigger,HIGH);
 delayMicroseconds(10);
 digitalWrite(trigger,LOW);
 delayMicroseconds(2);
 time=pulseIn(echo,HIGH);
 
 distance=time*340/20000;
}
