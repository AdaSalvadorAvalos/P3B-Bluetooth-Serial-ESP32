#Práctica 3: ejercicio B

Materiales
·ESP32

Presentacion: usar el periférico de bluetooth del ESP32  conectándolo al móvil


EXPLICACIÓN DEL CÓDIGO:
```
#include "BluetoothSerial.h"

//chequea si el bluetooth esta habilitado bien
#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to and enable it
#endif
//crea un objeto que sea BluetoothSerial
BluetoothSerial SerialBT;
//inicializa comunicación
void setup() {
  Serial.begin(115200); //inicialice una comunicación en serie a una velocidad de transmisión de 115200
  SerialBT.begin("AdaMiletest"); //el nombre del dispositivo Bluetooth del ESP32 
  Serial.println("The device started, now you can pair it with bluetooth!");
}

void loop() {
  if (Serial.available()) {//mira si hay bytes siendo recividos en el puerto serie si los hay envia la información al dispositivo conectado
    SerialBT.write(Serial.read()); // Serial.write(): envia datos usando el puerto serie bluetooth, Serial.read(): envia los datos recibidos
  }
  if (SerialBT.available()) { //mira si hay bytes listos para ser leídos en el puerto serie bluetooth, si los hay se escribirán por el monitor
    Serial.write(SerialBT.read());
  }
  delay(20);
}
```
Explicación de la salida en el vídeo
