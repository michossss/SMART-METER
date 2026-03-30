# ULTRASONIC-METER
A METER THAT WORKS WITH ULTRASONİC DİSTANCE SENSOR

 HOW İS İT WORK:

OUR DİSTANCE METER İS WORK WİTH DİSTANCE SENSOR.<img width="766" height="524" alt="image" src="https://github.com/user-attachments/assets/6260773d-5a42-4200-b563-449c60c092df" />

FİRST THE DİSTANCE SENSOR MEASURE THE DİSTANCE BETWEEN ITSELF AND THE WALL.

AFTER THAT İT SENDS DATA TO ARDUNİO NANO WİTH TRİG AND ECHO PİNS.

THEN OUR NANO TRANSFORM OUR DİGİTS FROM THE ULTRASONİC SENSOR İNTO ENGLİSH FOR THE DİSPLAY SCREEN.

THİS İS THE CODE THAT İT USES TO TRANSFORM DİGİTS İNTO ENGLİSH.

 ```cpp
 
  const int trigPin = 9;
  const int echoPin = 10;
  long duration;
  int distance;

  void setup() {
    pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
    pinMode(echoPin, INPUT);  // Sets the echoPin as an Input
    Serial.begin(9600);       // Starts the serial communication
  }

  void loop() {
    // Clearing the trigPin
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);

    // Triggering the sensor by setting the trigPin HIGH for 10 microseconds
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);

    // Reading the echoPin, returns the sound wave travel time in microseconds
    duration = pulseIn(echoPin, HIGH);

    // Calculating the distance (Speed of sound is 0.034 cm/us)
    distance = duration * 0.034 / 2;

    // Prints the distance on the Serial Monitor
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");

    delay(60); // Essential delay for measurement efficiency
  }
```

THİS SİGNAL İS THEN SENT TO OUR DİSPLAY, WİCH HAS AN I2C MODULE İNSTALLED. THE I2C MODULE İS VERY İMPORTANT BECAUSE THE PRODUCTS SİZE NECESSİTATES THE USE OF FEWER CABLES.

  3D MODELS

FULL DESİGN AND THE 3D PARTS

OUR PROJECT WAS DESİGNED İN THİNKERCAD 3D AND AT THE END WE GET TWO MODELS. ONE OF THEM İS THE FULL PRODUCT WİTH SCREEN AND SENSORS. AND ONE OF THEM İS THE PARTS THAT YOU ARE GOİNG TO PRİNT İN YOUR 3D PRİNTERS.

FULL PROJECT HOW İS İT GOİNG TO LOOK:
*   🔍 **[View Printable Case (STL)](Ultrasonic_Meter_2_0.stl)**
*   🔍 **[View Full Assembly (STL)](Ultrasonic_Meter_Full.stl)**
