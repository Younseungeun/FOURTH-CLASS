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
15. lcd.setCursor(0,0);             //Indicates the first line of the LCD 
16. lcd.print("Hello,Every one!"); //print "Hello,Every one!"
17. lcd.setCursor(0,1);            //Indicates the second line of the LCD 
18. lcd.print("Welcome Reader!");  //print "Welcome Reader!"
19. cdsValue  = analogRead(cds);   // read CDS sensor values
20. Serial.print("sensor = ");          // Enter CDS sensor values on the SERIAL monitor
21. Serial.println(cdsValue);           //Show sensor values on each line
22. if((cdsValue)<500)                   //If the CDS sensor value is less than 500,
23. { digitalWrite(led,HIGH); }          //turn on the LED
24. else                                 //if not
25. { digitalWrite(led,LOW); }           //turn off the LED
26. //The analog-to-digital converter is finished, read the las t value
27. delay(20); // wait 2milliseconds를 before moving to next loop
### ultra sensor
![image](https://user-images.githubusercontent.com/102523600/173248387-e1131813-2189-4fe9-a8a4-2a1093984b1c.png)
### CODE
1. int echo_pin= 10; //connect eco pin to 10pin 
2. int trig_pin= 11; //connect trig pin to 11pin 
3. void setup() {
4. Serial.begin(9600);
5. pinMode(echo_pin,INPUT); //Set to INPUT because it receives
6. pinMode(trig_pin,OUTPUT); //Set to OUTPUT because it sends
7. }
8. void loop() {
9. float duration, distance ;
10. digitalWrite(trig_pin,HIGH); //turn on trigr pin
11. delay(10);//the trigger pin is fired for 10 millieseconds
12. digitalWrite(trig_pin,LOW); //low
13. duration = pulseIn( echo_pin,HIGH);      //Bring duration value 
14. // the pulsIn function is in the form of pulsIn (pin number, pin state) and when the pin state changes,
15. //Returns the time elapsed in ms (microseconds)
16. distance = (float(duration/2) / 29.1);// The reason why we divide is because we go back and forth.
         Serial.print(distance); //open the serial port to check the distance.
         Serial.println("mm"); // the unit is milliemeter
         delay(3);
      }

### buzzer
![image](https://user-images.githubusercontent.com/102523600/173248978-e39f46b5-5f14-4b56-ba6a-e94a2bd9f680.png)
### CODE
     
