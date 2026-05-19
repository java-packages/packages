int pirsensor = 0;
void setup()
{
pinMode(13, OUTPUT);
pinMode(2, INPUT);
}
void loop()
{
pirsensor  =  digitalRead(2); 
if (pirsensor == HIGH)
{
digitalWrite(13, HIGH);
}
else
{ 
digitalWrite(13, LOW);
}
delay(1000);
digitalWrite(13, LOW);
}
