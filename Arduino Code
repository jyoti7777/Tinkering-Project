#include<DHT.h>
#define outpin 13

int flag = 0;
int flag2 ;
char message [1000];
 #include "twilio.hpp"

 // Set these - but DON'T push them to GitHub!
 static const char *ssid = "AP";
 static const char *password = "12345678";

 // Values from Twilio (find them on the dashboard)
 static const char *account_sid = "AC3086e58569a58e17db75f6d71ae59981";
 static const char *auth_token = "9b52a2d3e1a4cc15446a67d5cc755b46";
// Phone number should start with "+<countrycode>"
 static const char *from_number = "+12565769086";

 // You choose!
 // Phone number should start with "+<countrycode>"
 static const char *to_number = "+918968110885";
 //static char *message ;

 Twilio *twilio;

int k = 1;

//dht DHT
DHT dht(outpin, DHT11);

const int buzz = 5;
const int MQ4 = 32;
const int MQ7 =  34; 
const int MQ135 = 33;
const int MQ2 = 35;


float sensorValue0; 
float sensorValue1;
float sensorValue2;
float sensorValue3;
float sensorValue4;



void setup()
{ dht.begin();
  Serial.println("Gas sensor warming up!");
  delay(20000); // allow the MQ to warm up
  Serial.begin(9600);
  

}

void loop()
{  
  
  String response;
  flag = 0;
  sensorValue0 = analogRead(MQ2) ; // read analog input pin 0
  sensorValue1=analogRead(MQ4) ;
  sensorValue2 = analogRead(MQ7);
  sensorValue3 = analogRead(MQ135) ;
  sensorValue4 = dht.readTemperature();
  float t = dht.readTemperature();
  float h = dht.readHumidity();


 
  Serial.println("MQ2:");
  Serial.println(sensorValue0);
  if(sensorValue0>3650){
     Serial.println(" SMOKE ALERT!!");
     digitalWrite(buzz,HIGH);
     flag = 1;
     delay(2000);
  }
  delay(2000);
  
  
  Serial.println("MQ4:");
  Serial.println(sensorValue1);
   if(sensorValue1>50000){
     Serial.println(" CNG ALERT!!");
     flag = 2;
     digitalWrite(buzz,HIGH);
     delay(2000);
  }
  delay(2000);

 
  Serial.println("MQ7:");
  Serial.println(sensorValue2);
   if(sensorValue2>2100){
     Serial.println(" CO ALERT!!");
     flag = 3;
     digitalWrite(buzz,HIGH);
     delay(2000);
  }
  delay(2000);

   Serial.println("MQ135:");
  Serial.println(sensorValue3);
   if(sensorValue3>3000){
     Serial.println(" SMOKE ALERT!!");
     flag = 1;
     digitalWrite(buzz,HIGH);
     delay(2000);
  }
  delay(2000);


  // Serial.println("dht:");
  // Serial.print("Temperature=");
  // Serial.println(t);
  // if(t > 40){
  //     flag2 = 1;
  // }
  // Serial.print("HUMIDITY=");
  // Serial.println(h);
  delay(2000);


  digitalWrite(buzz, HIGH);
  delay(1000);
  digitalWrite(buzz, LOW);

  if(flag){
    if(flag == 1)
      snprintf(message, sizeof(message), "SMOKE ALERT!!! \n The current air monitor stats are \n Smoke - Sensor Value: %f \n CO Alert - Sensor Value : %f ", sensorValue0, sensorValue3);
     if(flag == 3)
      snprintf(message, sizeof(message), "CO ALERT!!! \n The current air monitor stats are \n CO  - Sensor Value: %f ", sensorValue2);
      if(flag == 2)
      snprintf(message, sizeof(message), "CNG ALERT!!! \n The current air monitor stats are \n Sensor Value: %f", sensorValue1);

  }
  else
        snprintf(message, sizeof(message), "ALERT!!!\nSmoke - Sensor Value: %f \n CO Alert - Sensor Value : %f \n CNG Senosr Value : %f ", sensorValue0,sensorValue1, sensorValue2);

   if(flag != 0){
    Serial.print("Connecting to WiFi network ;");
   Serial.print(ssid);
   Serial.println("'...");
   WiFi.begin(ssid, password);
   //Serial.println("Warming Up");
   delay(1000);

   while (WiFi.status() != WL_CONNECTED) {
     Serial.println("Connecting...");
     delay(500);
  }
  Serial.println("Connected!");

  twilio = new Twilio(account_sid, auth_token);

  delay(1000);
    bool success = twilio->send_message(to_number, from_number, message, response);
   if (success) {
      Serial.println("Sent message successfully!");
  } else {
      Serial.println(response);
    }
    WiFi.disconnect();
    k++;
    delay(20000);
  }
    else{
    k++;
    }
  delay(2000);

  }
