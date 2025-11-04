# Home_Automation_with_Blynk

#define BLYNK_PRINT Serial  
#define BLYNK_TEMPLATE_ID "TMPL3QHORJLb4"  
#define BLYNK_TEMPLATE_NAME "Home Automation Using NodeMCU and Blynk IoT"  
#define BLYNK_AUTH_TOKEN "55IaW_RlkhymdVuV6LvAKJcSMCnSY_xq"  

#include <ESP8266WiFi.h>  
#include <BlynkSimpleEsp8266.h>  

// Your WiFi credentials.  
// Set password to "" for open networks.  
char ssid[] = "Nitish_Mehta";  
char pass[] = "niti$h392";  

int led = D0;  
int Motor= D1;  

int pinValue1;  
int pinValue2;  

BLYNK_WRITE(V1)  //FAN switch  
{  
 int pinValue1 = param.asInt();  
 digitalWrite(led,pinValue1);  
  
  Blynk.virtualWrite(V1,pinValue1);  
  Serial.println(pinValue1);  
}  
BLYNK_WRITE(V2)  //LED switch  
{
  int pinValue2 = param.asInt();  
  digitalWrite(Motor,pinValue2);  
  Blynk.virtualWrite(V2,pinValue2);  
  Serial.println(pinValue2);  
}  

void setup()  
{
  pinMode(Motor, OUTPUT);  
  pinMode(led, OUTPUT);  
  Serial.begin(115200);  
  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);  
}

void loop()  
{
  Blynk.run();  
  delay(1000); // Update every 1 seconds  
}
