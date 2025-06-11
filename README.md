const int soilMoisturePin = A0;  
const int relayPin = 7;          

int moistureThreshold = 400;

void setup() {
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH); 
  Serial.begin(9600); 
}

void loop() {
  int soilMoistureValue = analogRead(soilMoisturePin);
  Serial.print("Soil Moisture: ");
  Serial.println(soilMoistureValue);

  if (soilMoistureValue < moistureThreshold) {
    digitalWrite(relayPin, LOW); 
    Serial.println("Soil is dry → Pump ON");
  } else {
    digitalWrite(relayPin, HIGH); 
    Serial.println("Soil is wet → Pump OFF");
  }

  delay(2000); 
}
