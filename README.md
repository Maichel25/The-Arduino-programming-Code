
#include <LiquidCrystal.h> 
 
LiquidCrystal lcd(12, 11, 5, 4, 3, 2); 
 
const int soundPin = A0; 
const int ledPin1 = 6; 
const int ledPin2 = 7; 
const int ledPin3 = 8; 
 
void setup() { 
  lcd.begin(16, 2); 
  pinMode(soundPin, INPUT); 
  pinMode(ledPin1, OUTPUT); 
  pinMode(ledPin2, OUTPUT); 
  pinMode(ledPin3, OUTPUT); 
} 
 
void loop() { 
  int soundValue = analogRead(soundPin); 
  int intensity = map(soundValue, 0, 1023, 0, 100); 
 
  lcd.clear(); 
  lcd.setCursor(0, 0); 
  lcd.print("Intensity: "); 
  lcd.print(intensity); 
  lcd.print("%"); 
 
  updateLEDs(intensity); 
  delay(500); // Adjust delay as needed 
} 
 
void updateLEDs(int intensity) { 
  if (intensity >= 30) { 
    digitalWrite(ledPin3, HIGH); 
  } else { 
    digitalWrite(ledPin3, LOW); 
  } 
 
  if (intensity >= 20) { 
    digitalWrite(ledPin2, HIGH); 
  } else { 
    digitalWrite(ledPin2, LOW); 
  } 
 
  if (intensity >= 10) { 
    digitalWrite(ledPin1, HIGH); 
  } else { 
    digitalWrite(ledPin1, LOW); 
  } 
}
