#define trigPin 3
#define echoPin 4
#define ledr 8
#define ledy 9
#define ledg 10
long duration;
int cm;
int inches;
void setup(){
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
pinMode(ledr, OUTPUT);
pinMode(ledy, OUTPUT);
pinMode(ledg, OUTPUT);
Serial.begin(9600);
}
void loop()
{
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
duration = pulseIn(echoPin, HIGH);
cm = duration * 0.034 / 2;
inches = cm / 2.54;
Serial.print(inches);
Serial.print(" in, ");
Serial.print(cm);
Serial.println(" cm");
if(inches < 20)
{
digitalWrite(ledr, LOW);
digitalWrite(ledy, LOW);
digitalWrite(ledg, HIGH);
}
else if(inches >= 20 && inches < 40)
{
}
digitalWrite(ledr, LOW);
digitalWrite(ledy, HIGH);
digitalWrite(ledg, LOW);
else
{
}
digitalWrite(ledr,  HIGH);
digitalWrite(ledy,  LOW);
digitalWrite(ledg, LOW);
delay(200);
}
