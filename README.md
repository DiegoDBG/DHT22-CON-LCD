# DHT22 CON LCD
## Practica con un sensor DHT22 en una placa de desarrollo ESP32 y un LCD de 12C 
Este repositorio muestra como podemos programar una **ESP32** con el sensor **DHT22** y mostrar los datos optenidos en un **LCD 12c**.

### Introducción
**Descripción:**
La ESP32 la utilizamos en un entorno de adquision de datos, en esta practica ocuparemos un sensor DHT22 para adquirir temperatura y humedad del entorno, como tambien un **LCD de 12c** para visualizar los datos opotenidos, todo siendo simulado en una pagina llamda **WOKWI**

### Material Necesario
Para realizar esta practica necesitas lo siguiente:

- WOKWI
- Tarjeta ESP32
- Sensor DHT22
- LCD (16x2) 12c

### Requisitos previos:
Para poder usar este repositorio necesitas entrar a la plataforma WOKWI.

### Instrucciones de preparación de entorno:
1.-Abrir la terminal de programación y colocar la siguente programación:
```#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");

 lcd.clear(); 
  lcd.setCursor(4, 0);
  lcd.print("MODULO V");
  lcd.setCursor(6, 1);
  lcd.print("AIyM");
 delay(2000);

lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("diego bahena");
  lcd.setCursor(6, 1);
  lcd.print("I.E.E");
  delay(2000);

 lcd.clear(); 
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  delay(2000);
}
```

2.- Instalar las librerias de **DHT sensor library for ESPx** como de **LiquidCrystal I2C** como se muestra en la siguente imagen.

![image](https://github.com/user-attachments/assets/55199a48-6261-42d6-8754-bcbad5a4ea63)

3.- Hacer la conexion de **DHT22** con la **ESP32** y el **LCD 12C** como se muestra en la siguente imagen.

![image](https://github.com/user-attachments/assets/c4db0114-a616-426e-a106-0c082c3b6156)

### Instrucciónes de operación
- Iniciar simulador.
- Visualizar los datos en el LCD.
- Colocar la temperatura y humedad dando doble click al sensor DHT22
  
### Resultados
Cuando haya funcionado, verás los valores dentro del LCD como se muestra en la siguente imagen.

![image](https://github.com/user-attachments/assets/0468ccfa-a33e-40a4-a048-e903fb530e0e)

![image](https://github.com/user-attachments/assets/639baee6-c248-47cf-8ef0-0c9f60ff6a0d)

![image](https://github.com/user-attachments/assets/883f1e49-d4f5-4c4a-ab75-a3be13151ecb)


### Desarrollado por 
Diego David Bahena Galan

[GitHub](https://github.com/DiegoDBG)
