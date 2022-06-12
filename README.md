# FOURTH-CLASS

## TOPIC
- fuse LCD,CDS sensor and LED
- ultra sensor
- buzzer
### fuse LCD,CDS sensor and LED
![image](https://user-images.githubusercontent.com/102523600/173247658-63ab89d1-004c-4bc3-949a-eb512e85497e.png)
### CODE
1. #include <Wire.h> 
2. #include <LiquidCrystal_I2C.h>      //LCD header file
3. LiquidCrystal_I2C lcd(0x27,16,2);      // set the LCD address to 0x27 for a 16 chars and 2 line display, "0x27" means the address of LCD
4. int cds = A2;                         //Connect the CDS sensor to an analog pin2
5. int cdsValue = 0;                     // Read the value from the port
6. int LED=12;                           //connect the LED to pin 12
7. void setup(){                          //start  
8. Serial.begin(9600);                  
9. pinMode(LED, OUTPUT);                //use the LED as an output, as a result
10. lcd.init();                         // initialize the lcd, Print a message to the LCD.
11. lcd.backlight();               
12. }                                  
13. void loop() {
14. lcd.clear();                    // clear the LCD
15. lcd.setCursor(0,0);             //LCD의 첫 번째 줄 첫 번째 자리를 나타냄
16. lcd.print("Hello,Every one!"); //print "Hello,Every one!"
17. lcd.setCursor(0,1);            //LCD의 두 번째 줄 첫 번째 자리를 나타냄
18. lcd.print("Welcome Reader!");  //print "Welcome Reader!"
19. cdsValue  = analogRead(cds);   // read CDS sensor values
20. Serial.print("sensor = ");          // Enter CDS sensor values on the SERIAL monitor
21. Serial.println(cdsValue);           //Show sensor values on each line
22. if((cdsValue)<500)                   //If the CDS sensor value is less than 500,
23. { digitalWrite(led,HIGH); }          //turn on the LED
24. else                                 //if not
25. { digitalWrite(led,LOW); }           //turn off the LED
//The analog-to-digital converter is finished, read the las t value
delay(20); // wait 2milliseconds를 before moving to next loop

  1.   }                              //LCD,LED,CDS끝
     
