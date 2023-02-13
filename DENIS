#include <AccelStepper.h>
#define dirPin 9
#define stepPin 10
#define motorInterfaceType 1

AccelStepper stepper = AccelStepper(motorInterfaceType, stepPin, dirPin);

int joystickX = 0;

// Aldagaiak definitu
const int buttonPinA = 2;
const int ledPin1 = 13;
int ledState1 = HIGH; // LED-aren hasierako balioa
int buttonState1; // Sakatzailearen oraingo egoera
int lastButtonState1 = LOW; // Sakatzailearen aurreko egoera

// DEBOUNCE denborak.
unsigned long lastDebounceTime1 = 0; // Lehen aldiz sakatua
unsigned long debounceDelay1 = 50; // Debounce denbora.

const int buttonPinB = 3;
const int ledPin2 = 12;
int ledState2 = HIGH; // LED-aren hasierako balioa
int buttonState2; // Sakatzailearen oraingo egoera
int lastButtonState2 = LOW; // Sakatzailearen aurreko egoera

// DEBOUNCE denborak.
unsigned long lastDebounceTime2 = 0; // Lehen aldiz sakatua
unsigned long debounceDelay2 = 50; // Debounce denbora.

// Aldagaiak definitu
const int buttonPinC = 4;
const int ledPin3 = 11;
int ledState3 = HIGH; // LED-aren hasierako balioa
int buttonState3; // Sakatzailearen oraingo egoera
int lastButtonState3 = LOW; // Sakatzailearen aurreko egoera

// DEBOUNCE denborak.
unsigned long lastDebounceTime3 = 0; // Lehen aldiz sakatua
unsigned long debounceDelay3 = 50; // Debounce denbora.

void setup() {
  Serial.begin(9600); // Serie komunikazioa martxan jarri.
  pinMode(buttonPinA, INPUT);
  pinMode(ledPin1, OUTPUT);
  digitalWrite(ledPin1, ledState1);
  pinMode(buttonPinB, INPUT);
  pinMode(ledPin2, OUTPUT);
  digitalWrite(ledPin2, ledState2);
  pinMode(buttonPinC, INPUT);
  pinMode(ledPin3, OUTPUT);
  digitalWrite(ledPin3, ledState3);

  stepper.stop();
  stepper.setMaxSpeed(2000);
  stepper.setAcceleration(500);
}

void loop() {

  int reading1 = digitalRead(buttonPinA);
  if (reading1 != lastButtonState1) { //Sakatzailea sakatu
    lastDebounceTime1 = millis();   //Timerra inizializatu
  }
  // Botoiaren egoera aldatu baldin bada:
  if ((millis() - lastDebounceTime1) > debounceDelay1) {
    if (reading1 != buttonState1) {  // Botoia aldatu bada
      buttonState1 = reading1; // Balioak eguneratu
      if (buttonState1 == LOW) {//LED-a HIGH bada soilik
        ledState1 = !ledState1;
        Serial.print("LED-a: ");
        Serial.println(ledState1);
      }
    }
  }
  digitalWrite(ledPin1, ledState1); // LED-a freskatu
  lastButtonState1 = reading1; // Balioak eguneratu


  int reading2 = digitalRead(buttonPinB);
  if (reading2 != lastButtonState2) { //Sakatzailea sakatu
    lastDebounceTime2 = millis();   //Timerra inizializatu
  }
  // Botoiaren egoera aldatu baldin bada:
  if ((millis() - lastDebounceTime2) > debounceDelay2) {
    if (reading2 != buttonState2) {  // Botoia aldatu bada
      buttonState2 = reading2; // Balioak eguneratu
      if (buttonState2 == LOW) {//LED-a HIGH bada soilik
        ledState2 = !ledState2;
        Serial.print("LED-a: ");
        Serial.println(ledState2);
      }
    }
  }
  digitalWrite(ledPin2, ledState2); // LED-a freskatu
  lastButtonState2 = reading2; // Balioak eguneratu

  int reading3 = digitalRead(buttonPinC);
  if (reading3 != lastButtonState3) { //Sakatzailea sakatu
    lastDebounceTime3 = millis();   //Timerra inizializatu
  }
  // Botoiaren egoera aldatu baldin bada:
  if ((millis() - lastDebounceTime3) > debounceDelay3) {
    if (reading3 != buttonState3) {  // Botoia aldatu bada
      buttonState3 = reading3; // Balioak eguneratu
      if (buttonState3 == LOW) {//LED-a HIGH bada soilik
        ledState3 = !ledState3;
        Serial.print("LED-a: ");
        Serial.println(ledState3);
      }
    }
  }
  digitalWrite(ledPin3, ledState3); // LED-a freskatu
  lastButtonState3 = reading3; // Balioak eguneratu

  joystickX = analogRead(0); //  position kontrola

  Serial.print("Joystick-a: (X)  ");
  Serial.println(joystickX);


  while (joystickX < 153 ) {
    // Set the target position:
    stepper.move(500);
    stepper.run();
    joystickX = analogRead(0);
    delay(0);
  }
  while (joystickX > 953 ) {
    // Set the target position:
    stepper.move(-500);
    stepper.run();
    joystickX = analogRead(0);
    delay(0);
  }
}
