
<p align="left" style="margin-top: 50px; margin-bottom: 50px; font-family: Arial, sans-serif;">
  <p align="left">
    <img src="https://semanadelcannabis.cayetano.edu.pe/assets/img/logo-upch.png" width="300" alt="Facultad de Ciencias e ingeniería logo">
  </p>  
  <h1 align="center" style="margin-top: 30px; margin-bottom: 0px;">Taller 03: Internet de las Cosas (IoT)</h1>
</p>

## 1. Introduccíon 
#### *El Internet de las Cosas (IoT) es el proceso de conectar los objetos físicos cotidianos al Internet, mediante dispositivos integrados con sensores, software y conectividad de red. Estos dispositivos pueden recopilar y compartir datos, así como interactuar con otros dispositivos o sistemas. El IoT tiene aplicaciones en diversos ámbitos, como el hogar, la industria, la salud, la movilidad y las ciudades inteligentes. El IoT puede ofrecer beneficios como la optimización de las operaciones, la mejora de la eficiencia y la productividad, y la creación de experiencias personalizadas para los usuarios**

## 2.- Lista de materiales utilizados en el laboratorio


| MATERIALES |  IMAGEN | 
| :------------ |:---------------:| 
| SENSOR PIR| [![PIR.jpg](https://i.postimg.cc/VsjYHfPs/descarga.jpg)](https://postimg.cc/QVdGFrMv)|
| Arduino MKR WIFI 1010| [![ARDUINO.jpg](https://i.postimg.cc/dQSZf2tx/descarga-9.jpg)](https://postimg.cc/hhTGz7mL) |
| Arduino MKR IoT Carrier | [![Arduino MKR IoT Carrier.jpg](https://i.postimg.cc/SQ5PB5CZ/descarga-1.jpg)](https://postimg.cc/V5q4MK7M)| 


## 2.- Ejercicios desarrollados en la práctica del laboratorio

###  EJERCICIO 1

#### CODIGO DEL EJERCICIO 1:

```cpp
/*
  Explore IoT - Activity 01
 
  Read values from a temperature and humidity sensor
  and print it in Serial Monitor and on a colored display.
 
  This example uses the IoT carrier and the MKR WiFi 1010.
 
  Based on code by
  (c) 2019 D. Cuartielles for Arduino
 
  Written by:
  (c) 2020 K. SÃ¶derby for Arduino
 
  This code is Free Software licensed under GPLv3
*/
#include <Arduino_MKRIoTCarrier.h>
MKRIoTCarrier carrier;
float temperature = 0;
float humidity = 0;
void setup() {
  Serial.begin(9600);
  //Wait to open the Serial monitor to start the program and see details on errors
  
  //Set if it has the Enclosure mounted
  CARRIER_CASE = true;
  //Initialize the IoTSK carrier and output any errors in the serial monitor
  carrier.begin();
}
void loop() {
  // read the sensor values
  temperature = carrier.Env.readTemperature();
  humidity = carrier.Env.readHumidity();
  //Update touch buttons
  carrier.Buttons.update();
  // print each of the sensor values
  Serial.print("Temperature = ");
  Serial.print(temperature);
  Serial.println(" Â°C");
  Serial.print("Humidity = ");
  Serial.print(humidity);
  Serial.println(" %");
  //function to print out values
  if (carrier.Buttons.onTouchDown(TOUCH0)) {
    printTemperature();
  }
  if (carrier.Buttons.onTouchDown(TOUCH1)) {
    printHumidity();
  }
}
void printTemperature() {
  //configuring display, setting background color, text size and text color
  carrier.display.fillScreen(ST77XX_RED); //red background
  carrier.display.setTextColor(ST77XX_WHITE); //white text
  carrier.display.setTextSize(6); //large sized text
  carrier.display.setCursor(30, 50); //sets position for printing (x and y)
  carrier.display.print("Temp: ");
  carrier.display.setTextSize(4); //decreasing text size
  carrier.display.setCursor(40, 120); //sets new position for printing (x and y)
  carrier.display.print(temperature);
  carrier.display.print(" C");
}
void printHumidity() {
  //configuring display, setting background color, text size and text color
  carrier.display.fillScreen(ST77XX_BLUE); //red background
  carrier.display.setTextColor(ST77XX_WHITE); //white text
  carrier.display.setTextSize(4); //medium sized text
  carrier.display.setCursor(20, 110); //sets position for printing (x and y)
  carrier.display.print("Humi: ");
  carrier.display.print(humidity);
  carrier.display.println(" %");
}
```

##### Imagenes como prueba de los resultados del ejercicio

<p align="center">
  <img src="https://i.postimg.cc/1Rpg4V5Q/Imagen-de-Whats-App-2024-01-24-a-las-16-58-54-db18f646.jpg)](https://postimg.cc/jCSqF57g)" alt="" width="400px" />
</p>



* ##   EJERCICIO 2




#### CODIGO DEL EJERCICIO 2:


```cpp

#include <Arduino_MKRIoTCarrier.h>
MKRIoTCarrier carrier;
double temperature = 0;
float humidity = 0;

void setup() {
  Serial.begin(9600);
  CARRIER_CASE = true;
  carrier.begin();
}

void loop() {
  temperature = carrier.Env.readTemperature();
  humidity = carrier.Env.readHumidity();
  carrier.Buttons.update();

  Serial.print("Temperature = ");
  Serial.print(temperature);
  Serial.println(" °C");

  // Convertir a Fahrenheit y Kelvin
  double fahrenheit = (temperature * 9.0 / 5.0) + 32.0;
  double kelvin = temperature + 273.15;

  if (carrier.Buttons.onTouchDown(TOUCH0)) {
    printTemperature(temperature, "C");
  }
  if (carrier.Buttons.onTouchDown(TOUCH1)) {
    printTemperature(fahrenheit, "F");
  }
  if (carrier.Buttons.onTouchDown(TOUCH2)) {
    printTemperature(kelvin, "K");
  }
}

void printTemperature(double temp, const char *unit) {
  carrier.display.fillScreen(ST77XX_RED);
  carrier.display.setTextColor(ST77XX_WHITE);
  carrier.display.setTextSize(6);
  carrier.display.setCursor(30, 50);
  carrier.display.print("Temp: ");
  carrier.display.setTextSize(4);
  carrier.display.setCursor(40, 120);
  carrier.display.print(temp);
  carrier.display.print(" ");
  carrier.display.print(unit);
}
```






* ## EJERCICIO 3


<p align="center">
  <img src="" alt="" width="400px" />
</p>

