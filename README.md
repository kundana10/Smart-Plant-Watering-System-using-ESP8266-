# Smart-Plant-Watering-System-using-ESP8266-
This project enables efficient water management and can be expanded into a full IoT smart gardening system.
#define SOIL_SENSOR A0
#define RELAY D1
#define LED D2

int soilValue = 0;
int threshold = 600;   // adjust based on soil moisture

void setup()
{
  Serial.begin(9600);

  pinMode(RELAY, OUTPUT);
  pinMode(LED, OUTPUT);

  digitalWrite(RELAY, LOW);
}

void loop()
{
  soilValue = analogRead(SOIL_SENSOR);

  Serial.print("Soil Moisture Value: ");
  Serial.println(soilValue);

  if(soilValue > threshold)   // soil dry
  {
    digitalWrite(RELAY, HIGH);   // pump ON
    digitalWrite(LED, HIGH);
    Serial.println("Soil Dry - Pump ON");
  }
  else
  {
    digitalWrite(RELAY, LOW);    // pump OFF
    digitalWrite(LED, LOW);
    Serial.println("Soil Moist - Pump OFF");
  }

  delay(2000);
}
