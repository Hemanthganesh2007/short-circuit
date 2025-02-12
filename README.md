# short-circuit
link: https://www.tinkercad.com/things/i7WjI5p3aml-short-circuit/editel?sharecode=KIYDxZjNhjmHEF9iNWCquBic-ykqfjlUdqpGUaEHypg 


    const int greenLED = 7;     
    const int yellowLED = 6;    
    const int redLED = 5;       
    const int buttonPin = 2;    

    int buttonState = 0;        
    int lastButtonState = 0;    


    unsigned long previousMillis = 0;
    const long interval = 1000;  

     void setup() {
    pinMode(greenLED, OUTPUT);
    pinMode(yellowLED, OUTPUT);
    pinMode(redLED, OUTPUT);
  
    pinMode(buttonPin, INPUT);
    }

    void loop() {
    buttonState = digitalRead(buttonPin);

    if (buttonState == HIGH) {
    digitalWrite(redLED, HIGH);  
    digitalWrite(greenLED, LOW); 
    digitalWrite(yellowLED, LOW); 
    } else {
    unsigned long currentMillis = millis();

    if (currentMillis - previousMillis >= interval) {
      previousMillis = currentMillis;

      if (digitalRead(greenLED) == HIGH) {
        digitalWrite(greenLED, LOW);
        digitalWrite(yellowLED, HIGH);
      } else if (digitalRead(yellowLED) == HIGH) {
        digitalWrite(yellowLED, LOW);
        digitalWrite(redLED, HIGH);
      } else if (digitalRead(redLED) == HIGH) {
        digitalWrite(redLED, LOW);
        digitalWrite(greenLED, HIGH);
      }
    }
      }
      }
