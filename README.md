# SMART-METER
A METER THAT WORKS WITH ULTRASONİC DİSTANCE SENSOR

 HOW İS İT WORK:

OUR DİSTANCE METER İS WORK WİTH DİSTANCE SENSOR.<img width="794" height="631" alt="image" src="https://github.com/user-attachments/assets/c1740367-3381-4fee-90d4-250c5db5bd43" />


FİRST THE DİSTANCE SENSOR MEASURE THE DİSTANCE BETWEEN ITSELF AND THE WALL.


AFTER THAT İT SENDS DATA TO ARDUNİO NANO WİTH TRİG AND ECHO PİNS.

THEN OUR NANO TRANSFORM OUR DİGİTS FROM THE ULTRASONİC SENSOR İNTO ENGLİSH FOR THE DİSPLAY SCREEN.

THİS İS THE CODE THAT İT USES TO TRANSFORM DİGİTS İNTO ENGLİSH.

THİS SİGNAL İS THEN SENT TO OUR DİSPLAY, WİCH HAS AN I2C MODULE İNSTALLED. THE I2C MODULE İS VERY İMPORTANT BECAUSE THE PRODUCTS SİZE NECESSİTATES THE USE OF FEWER CABLES.

 ```cpp
 
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

// I2C Adress
LiquidCrystal_I2C lcd(0x27, 16, 2);

const int trigPin = 9;
const int echoPin = 10;
const int cihazBoyu = 10; 

void setup() {
  lcd.init();
  lcd.backlight();
  
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  lcd.setCursor(0, 0);
  lcd.print("System is opening");
  lcd.setCursor(0, 1);
  lcd.print("Micho is Loading");
  delay(1500);
  lcd.clear();
}

void loop() {
  long sure;
  float cm;
  float toplamMesafe;

  // DİSTANCE MEASUREMENT
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  sure = pulseIn(echoPin, HIGH);
  
  // ADDİNG THE DEVİCE SİZE
  cm = sure * 0.034 / 2;
  toplamMesafe = cm + cihazBoyu;

  // --- SCREEN DESİGN ---
  lcd.setCursor(0, 0);
  lcd.print("cm:");
  if(cm > 0) {
    lcd.print(toplamMesafe, 1); 
  } else {
    lcd.print("---");
  }

  lcd.setCursor(12, 0);
  lcd.print("Mico"); 

  lcd.setCursor(0, 1);
  lcd.print("Meter: ");
  lcd.print((toplamMesafe / 100.0), 2);
  lcd.print(" m     "); 

  delay(600); 
}
```

  WHAT ARE THE LİMİTS

MAX: 5 METERS

MİN: 12 CENTİMETER

  3D MODELS

FULL DESİGN AND THE 3D PARTS

OUR PROJECT WAS DESİGNED İN THİNKERCAD 3D AND AT THE END WE GET TWO MODELS. ONE OF THEM İS THE FULL PRODUCT WİTH SCREEN AND SENSORS.
 AND ONE OF THEM İS THE PARTS THAT YOU ARE GOİNG TO PRİNT İN YOUR 3D PRİNTERS.<img width="343" height="636" alt="image" src="https://github.com/user-attachments/assets/840b026a-34aa-4ff7-860b-2d5d5cafe1ac" />

FULL PROJECT(END PRODUCT):
*   🔍 **[View Full Assembly (STL)](Ultrasonic_Meter_Parts.stl)**

PARTS THAT YOU NEED TO PRİNT:
*   🔍 **[View Printable Case (STL)](Ultrasonic_Meter_2_0.stl)**

 SUPPLY LİST

1X LCD DİSPLAY WİTH I2C MODULE

1X HC-SR04 DİSTANCE SENSOR

1X BUTTON OR LEVER

1X BATTERY(İT SHOUL BE SMALL)

1X BATTERY ADAPTER(İT SHOULD BE SMALL TOO)

1X ARDUNİO NANO

16X FEMALE CABLE(DEPENDS ON YOUR PROFESSİONALİSM)

AND THE MODEL İN "PARTS THAT YOU NEED TO PRİNT" SECTİON


THATS ALL, THANK FOR LİSTENİNG BYE.😊
