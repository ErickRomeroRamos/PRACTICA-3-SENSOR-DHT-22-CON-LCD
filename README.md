# PRACTICA-3-SENSOR-DHT-22-CON-LCD

##Este repositorio muestra la tercera practica practica del diplomado de como podemos programar una ESP32 con el sensor DHT22 y mostrando el resutado en la LCD.

## Introducción
### Descripción
La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (DTH22) para obtener temperatura y humedad, ademas agrgaremos un (LCD 16X2 I2C) para mostrar los resultados en la pantalla lcd; Esta practica se usara un simulador llamado WOKWI.

## Material Necesario
### A continuacion se utilizaron los siguientes materiales.

WOKWI


Tarjeta ESP 32

Sensor DHT22

LCD 16X2 I2C

## Instrucciones

Requisitos previos
Para realizar la practica de este repositorio se necesita entrar a la plataforma WOKWI.

Instrucciones de preparación de entorno
Abrir la terminal de programación y colocar la siguente codigo:

#include "DHTesp.h"
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
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
}

## Instalar la libreria de Cristal líquido I2C.
### Seleccionar pestaña de Librery Manager --> Add a New library -Colocamos el nombre de libreria

![image](https://github.com/ErickRomeroRamos/PRACTICA-3-SENSOR-DHT-22-CON-LCD/assets/153964793/abc69382-3623-47ff-b55b-a8574b801b58)

## Realizar la conexion de DHT22 con la ESP32 y de la LCD de la siguiente manera

![image](https://github.com/ErickRomeroRamos/PRACTICA-3-SENSOR-DHT-22-CON-LCD/assets/153964793/94e0e208-e290-4709-8b6a-ca0b1f30d18f)

Conexion lcd -GND -VCC -SDA --> esp:21 -SCL --> esp:22

## Instrucciónes de operación
### Iniciar simulador.
Visualizar los datos en el monitor serial y en la lcd .
Colocar la temperatura y humedad dando doble click al sensor DHT22
## Resultados
### Una vez terminado iniciamos simulacion y se observaran los valores en la lcd.

![image](https://github.com/ErickRomeroRamos/PRACTICA-3-SENSOR-DHT-22-CON-LCD/assets/153964793/6bba42d5-83d5-4034-b645-0eaf64550c46)


