# Practice 3-B: ESP32 Bluetooth Serial (English Version)

## Materials
- ESP32

## Introduction
In this practice, for my Digital Processors course, I learned how to use the Bluetooth peripheral of the ESP32 to communicate with a mobile device. The ESP32 acts as a Bluetooth serial device, sending and receiving data between the board and a paired device.

## Code Explanation (with line-by-line comments):
```cpp
#include "BluetoothSerial.h"

// Check if Bluetooth is enabled
#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to enable it
#endif

BluetoothSerial SerialBT; // Create a BluetoothSerial object

void setup() {
  Serial.begin(115200);                // Initialize Serial at 115200 bps
  SerialBT.begin("AdaMiletest");       // Set the Bluetooth device name
  Serial.println("The device started, now you can pair it with Bluetooth!");
}

void loop() {
  if (Serial.available()) {            // Check if bytes are received via USB Serial
    SerialBT.write(Serial.read());     // Send the data over Bluetooth
  }

  if (SerialBT.available()) {          // Check if bytes are received via Bluetooth
    Serial.write(SerialBT.read());     // Send the data to USB Serial monitor
  }

  delay(20);
}
```
## How to Run

1. **Install PlatformIO**
   - Install [VS Code](https://code.visualstudio.com/)
   - Install the [PlatformIO extension](https://platformio.org/install/ide?install=vscode)

2. **Create a New Project**
   - Open PlatformIO in VS Code
   - Create a new project and select your board (e.g., ESP32 Dev Module)
   - Choose **Arduino framework**

3. **Add the Code**
   - Replace the contents of `src/main.cpp` with the code provided above

4. **Connect the Hardware**
   - Connect the ESP32 board to your computer via USB

5. **Build and Upload**
   - Click **Build (✓)** to compile the code
   - Click **Upload (→)** to flash the code to your ESP32

6. **Observe the Output**
   - Pair your mobile device with the ESP32 Bluetooth device named **AdaMiletest**
   - Open a serial terminal app on your phone and send messages
   - Messages will appear on the Serial Monitor of VS Code, and messages from the PC will appear on your mobile


### Resources
- **Video Demonstration in Spanish:** [Watch video](assets/practica3Bvideo.mp4)
- **ESP32 Documentation:** [Espressif ESP32](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/index.html)  
- **ESP32 Bluetooth Serial Documentation:** [ESP32 BluetoothSerial](https://github.com/espressif/arduino-esp32/tree/master/libraries/BluetoothSerial)  
- **Arduino Bluetooth Reference:** [Arduino Bluetooth](https://docs.arduino.cc/libraries/bluetoothserial/)  
- **ESP32 Bluetooth Guide:** [ESP32 Bluetooth Tutorial](https://randomnerdtutorials.com/esp32-bluetooth-classic-arduino-ide/)  

# Práctica 3-B: Serial Bluetooth en ESP32 (Versión en Español)

## Materiales
- ESP32

## Introducción

En esta práctica, para mi curso de Procesadores Digitales, aprendí a usar el periférico Bluetooth del ESP32 para comunicarme con un dispositivo móvil. El ESP32 actúa como un dispositivo Bluetooth Serial, enviando y recibiendo datos entre la placa y el dispositivo emparejado.


## Explicación del código (con comentarios línea por línea):
```cpp
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
## Cómo Ejecutar

1. **Instalar PlatformIO**
   - Instala [VS Code](https://code.visualstudio.com/)
   - Instala la [extensión PlatformIO](https://platformio.org/install/ide?install=vscode)

2. **Crear un Nuevo Proyecto**
   - Abre PlatformIO en VS Code
   - Crea un nuevo proyecto y selecciona tu placa (ejemplo: ESP32 Dev Module)
   - Elige el **framework Arduino**

3. **Agregar el Código**
   - Reemplaza el contenido de `src/main.cpp` con el código proporcionado arriba

4. **Conectar el Hardware**
   - Conecta la placa ESP32 a tu computadora mediante USB

5. **Compilar y Subir**
   - Haz clic en **Build (✓)** para compilar el código
   - Haz clic en **Upload (→)** para cargar el código en tu ESP32

6. **Observar el Resultado**
   - Empareja tu dispositivo móvil con el ESP32 Bluetooth llamado **AdaMiletest**
   - Abre una app de terminal serial en el móvil y envía mensajes
   - Los mensajes aparecerán en el Monitor Serial de VS Code, y los mensajes enviados desde el PC aparecerán en tu móvil

### Recursos
- **Video demostrativo en español:** [Ver video](assets/practica3Bvideo.mp4)
- **Documentación del ESP32:** [Espressif ESP32](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/index.html)  
- **Documentación ESP32 Bluetooth Serial:** [ESP32 BluetoothSerial](https://github.com/espressif/arduino-esp32/tree/master/libraries/BluetoothSerial)  
- **Referencia de Arduino Bluetooth:** [Arduino Bluetooth](https://docs.arduino.cc/libraries/bluetoothserial/)  
- **Guía de Bluetooth en ESP32:** [ESP32 Bluetooth Tutorial](https://randomnerdtutorials.com/esp32-bluetooth-classic-arduino-ide/)  

