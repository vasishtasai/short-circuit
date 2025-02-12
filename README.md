# short-circuit
link: https://www.tinkercad.com/things/46jHcgWnatc-short-circuit-task/editel?sharecode=omA1M4OwU2XuDUKFX9UFnkbbiDyv7oQhXOQ3BbHbzbs 
code: 
// C++ code
//

const int redLedPin = 2;
const int yellowLedPin = 3;
const int greenLedPin = 4;
const int buttonPin = 5; 


int buttonState = 0;
int lastButtonState = 0;
unsigned long previousMillis = 0;
unsigned long ledInterval = 1000; 
int ledState = 0; 

void setup() {
  pinMode(redLedPin, OUTPUT);
  pinMode(yellowLedPin, OUTPUT);
  pinMode(greenLedPin, OUTPUT);
  pinMode(buttonPin, INPUT_PULLUP); 
}

void loop() {
  unsigned long currentMillis = millis();
  
 
  buttonState = digitalRead(buttonPin);

 
  if (buttonState == HIGH) {
    digitalWrite(redLedPin, HIGH);  
    digitalWrite(yellowLedPin, LOW); 
    digitalWrite(greenLedPin, LOW);  
  } else {
    
    if (currentMillis - previousMillis >= ledInterval) {
      previousMillis = currentMillis;  

      
      digitalWrite(redLedPin, LOW);
      digitalWrite(yellowLedPin, LOW);
      digitalWrite(greenLedPin, LOW);

      
      if (ledState == 0) {
        digitalWrite(greenLedPin, HIGH);
        ledState = 1; 
      } else if (ledState == 1) {
        digitalWrite(yellowLedPin, HIGH);
        ledState = 2; 
      } else if (ledState == 2) {
        digitalWrite(redLedPin, HIGH);
        ledState = 0; 
      }
    }
  }
}
