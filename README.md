# 2023_08_11_HC00Write

I forget each time how to connect HC05-06 to my Arduino X. So let's make a wiki of it.






## How to connect HC05-HC06 with Raspberry Pi Pico

https://github.com/EloiStree/ToStudyNext/issues/1



Code Mirroir pour faire des tests.
```
char a;
#include <SoftwareSerial.h>

SoftwareSerial BT(2, 3); // RX | TX

void setup() {
//  delay(2000);

Serial.begin(9600);
while (!Serial) {
    ; // wait for serial port to connect. Needed for Leonardo only
  }
BT.begin(9600);
while (!BT) {
    ; // wait for serial port to connect. Needed for Leonardo only
  }

Serial.println("Start");
BT.println("Ready to trancive data");
}

void loop() {
  
  if (BT.available())
    Serial.write(BT.read());
    
  if (Serial.available())
    BT.write(Serial.read());

  while(BT.available() > 0) {
  
a= BT.read();// read the incoming data as string
Serial.println(a);

  }
}
```
