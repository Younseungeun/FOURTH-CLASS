# FOURTH-CLASS

## TOPIC
- fuse LCD,CDS sensor and LED
- ultra sensor
- buzzer
### fuse LCD,CDS sensor and LED
![image](https://user-images.githubusercontent.com/102523600/173247564-bab5b82d-f234-4f10-a524-fee3ba4840c9.png)
### CODE
1. #include <Wire.h> 
2. #include <LiquidCrystal_I2C.h>      //LCD header file
LiquidCrystal_I2C lcd(0x27,16,2);      // set the LCD address to 0x27 for a 16 chars and 2 line display, "0x27" means the address of LCD
int cds = A2;                         //Connect the CDS sensor to an analog pin2
int cdsValue = 0;                     // Read the value from the port
int LED=12;                           //LED를 12번 핀에 연결한다

void setup()                      
{                                    //start  
Serial.begin(9600);                  
pinMode(LED, OUTPUT);                //LED를 아웃풋 즉 결과로 사용하겠다
 lcd.init();                         // initialize the lcd, Print a message to the LCD.
     lcd.backlight();               
 }                                  
void loop() {
     lcd.clear();                    // clear the LCD
     lcd.setCursor(0,0);             //LCD의 첫 번째 줄 첫 번째 자리를 나타냄
     lcd.print("Hello,Every one!"); //LCD의 첫 번째 줄 첫 번째 자리에 Hello,Every one!을 표시함
     lcd.setCursor(0,1);            //LCD의 두 번째 줄 첫 번째 자리를 나타냄
     lcd.print("Welcome Reader!");  //LCD의 두 번째 줄 첫 번째 자리에 Welcome Reader!를 표시함
     cdsValue  = analogRead(cds);   // 조도 센서 값을 읽음
Serial.print("sensor = ");          // SERIAL 모니터에 센서 값 입력
Serial.println(cdsValue);           //줄마다 센서 값 표시
if((cdsValue)<500)                   //If the CDS sensor value is less than 500,
{ digitalWrite(led,HIGH); }          //
else                                 //if not
{ digitalWrite(led,LOW); }           //LED를 끈다
//아날로그-디지털 컨버터가 끝 맞쳐진 뒤 //마지막 값 읽은 뒤
delay(20); // wait 2milliseconds를 before moving to next loop

  1.   }                              //LCD,LED,CDS끝
     
