#include <SPI.h>
#include <MFRC522.h>
#define SS_PIN 10
#define RST_PIN 9
#define GREEN_LED 6
#define RED_LED 5
#define BUZZER 7
MFRC522 mfrc522(SS_PIN, RST_PIN);
// Replace with your RFID UID (Check from Serial first)
String authorizedUID = "A1B2C3D4";
void setup() {
Serial.begin(9600);
SPI.begin();
mfrc522.PCD_Init();
pinMode(GREEN_LED, OUTPUT);
pinMode(RED_LED, OUTPUT);
pinMode(BUZZER, OUTPUT);
Serial.println("RFID Asset Tracking System Started...");
}
void loop() {
digitalWrite(GREEN_LED, LOW);
digitalWrite(RED_LED, LOW);
digitalWrite(BUZZER, LOW);
// Check for card
if (!mfrc522.PICC_IsNewCardPresent()) {
return;
}
if (!mfrc522.PICC_ReadCardSerial()) {
return;
}
String readUID = "";
for (byte i = 0; i < mfrc522.uid.size; i++) {
readUID += String(mfrc522.uid.uidByte[i], HEX);
}
readUID.toUpperCase();
Serial.print("Card UID: ");
Serial.println(readUID);
if (readUID == authorizedUID) {
Serial.println("Access Granted - Authorized Asset");
digitalWrite(GREEN_LED, HIGH);
digitalWrite(BUZZER, HIGH);
delay(500);
} else {
Serial.println("Access Denied - Unauthorized Asset");
digitalWrite(RED_LED, HIGH);
digitalWrite(BUZZER, HIGH);
delay(1000);
}
digitalWrite(BUZZER, LOW);
Serial.println("----------------------------");
delay(2000);
mfrc522.PICC_HaltA();
}
