# Telemetro-Ultrasonico
Telemetro Ultrasonico Versionado con sus respectivos commit

Modificación v1:
Telemetro ultrasonico v1.

/*
  Ping))) Sensor

  This circuito lee PING))) ultrasonic

  Para este circuito en Arduino en particular,
  consta de una placa Arduino Uno R3 y un sensor de proximidad
  de ultrasonido PING.
  
  Referencias sobre el circuito.
-	La conexión ping debe ir al voltaje +5[V]
-	GND conectado a ground
-	Ping conectado al pin digital 7
  
*/
int inches = 0;
int cm = 0;
/*
Las principales variables presentadas en el código representan
distancias, y estas se encuentran en unidades de inches (pulgadas) 
y centímetros, 
ambas variables globales. 

*/
long readUltrasonicDistance(int triggerPin
echoPin, int triggerPin
echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Limpia el desescadenado
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Setea el pin de disparo en estado maximo high, 
  //por un periodo de 10 microsegundos
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // En esta parte se lee el pin encargado de recibir el eco  
  //y devuelve el tiempo de viaje de la onda de sonido en microsegundos
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  // Este apartado mide el tiempo de ping en centimetro
  cm = 0.01723 * readUltrasonicDistance(7, 7);
  // convert to inches by dividing by 2.54 Convierte a pulgadas dividiendo
  //por 2,54
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.println("cm");
  delay(100); // Espera de 100 milisegundos
}