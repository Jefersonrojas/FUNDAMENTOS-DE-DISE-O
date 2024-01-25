
<p align="left" style="margin-top: 50px; margin-bottom: 50px; font-family: Arial, sans-serif;">
  <p align="left">
    <img src="https://semanadelcannabis.cayetano.edu.pe/assets/img/logo-upch.png" width="300" alt="Facultad de Ciencias e ingeniería logo">
  </p>  
  <h1 align="center" style="margin-top: 30px; margin-bottom: 0px;">Taller 03: Internet de las Cosas (IoT)</h1>
</p>

# Imagen del grupo
<p align="center">
  <img src="https://i.postimg.cc/3RWdYGXH/Imagen-de-Whats-App-2024-01-24-a-las-18-27-08-48935e46.jpg)](https://postimg.cc/CBTF4zrv)" alt="" width="900px" />
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

#### CÓDIGO DEL EJERCICIO 1:

```cpp

#include <Arduino_MKRIoTCarrier.h>
MKRIoTCarrier carrier;

float temperature = 0;
float humidity = 0;

void setup() {
  Serial.begin(9600);

  //Establece si el gavinete tiene montado
  CARRIER_CASE = true;

  // Inicializa el operador IoTSK y muestra cualquier error en el monitor serie
  carrier.begin();
}
void loop() {

  // Leer los valores del sensor
  temperature = carrier.Env.readTemperature();
  humidity = carrier.Env.readHumidity();

  // Actualiza botones táctiles
  carrier.Buttons.update();

  // Imprime cada uno de los valores del sensor
  Serial.print("Temperature = ");
  Serial.print(temperature);
  Serial.println(" Â°C");
  Serial.print("Humidity = ");
  Serial.print(humidity);
  Serial.println(" %");

  //Función para imprimir valores
  if (carrier.Buttons.onTouchDown(TOUCH0)) {
    printTemperature();
  }
  if (carrier.Buttons.onTouchDown(TOUCH1)) {
    printHumidity();
  }

// IMPRIMIR TEMPERATURA
}
void printTemperature() {
  // Configurar la pantalla, configurar el color del fondo, el tamaño del texto y el color del texto
  carrier.display.fillScreen(ST77XX_RED);     // Fondo rojo
  carrier.display.setTextColor(ST77XX_WHITE); // Texto blanco 
  carrier.display.setTextSize(6);             // Tamaño del texto
  carrier.display.setCursor(30, 50);          // Establecer la posición para imprimir (x e y)
  carrier.display.print("Temp: ");
  carrier.display.setTextSize(4);             // Disminuyendo el tamaño del texto  
  carrier.display.setCursor(40, 120);         // Establece una nueva posición para imprimir (x e y)
  carrier.display.print(temperature);
  carrier.display.print(" C");
}

// IMPRIMIR HUMEDAD
void printHumidity() {
  // Configurar la pantalla, configurar el color del fondo, el tamaño del texto y el color del texto
  carrier.display.fillScreen(ST77XX_BLUE);     //  Fondo rojo
  carrier.display.setTextColor(ST77XX_WHITE);  //  Texto blanco 
  carrier.display.setTextSize(4);              // Texto de tamaño mediano
  carrier.display.setCursor(20, 110);         // Establecer la posición para imprimir (x e y)
  carrier.display.print("Humi: ");
  carrier.display.print(humidity);
  carrier.display.println(" %");
}
```

### Imagenes como prueba de los resultados del ejercicio

<p align="center">
  <img src="https://i.postimg.cc/1Rpg4V5Q/Imagen-de-Whats-App-2024-01-24-a-las-16-58-54-db18f646.jpg)](https://postimg.cc/jCSqF57g)" alt="" width="400px" />
</p>



##   EJERCICIO 2




### CÓDIGO DEL EJERCICIO 2:


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

## EXPLICACIÓN DEL CÓDIGO
### 1.INCLUSIÓN DE LA BIBLIOTECA (MKRIoTCarrier)


```cpp
#include <Arduino_MKRIoTCarrier.h>
````

### 2 DECLARACIÓN DE VARIABLES



```cpp
MKRIoTCarrier carrier;
double temperature = 0;
float humidity = 0;

````

### 3.CONFIGURACIÓN (setup)


```cpp
void setup() {
  Serial.begin(9600);
  CARRIER_CASE = true;
  carrier.begin();
}


````

### 4.FUNCIÓN DEL BUCLE (Loop)


```cpp
void loop() {
  temperature = carrier.Env.readTemperature();
  humidity = carrier.Env.readHumidity();
  carrier.Buttons.update();

  // Lecturas de temperatura y humedad
  Serial.print("Temperature = ");
  Serial.print(temperature);
  Serial.println(" °C");

  // Convertir a Fahrenheit y Kelvin
  double fahrenheit = (temperature * 9.0 / 5.0) + 32.0;
  double kelvin = temperature + 273.15;

  // Verificación de eventos de botones táctiles
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


````

* temperature = carrier.Env.readTemperature(); y humidity = carrier.Env.readHumidity().Lee la temperatura y la humedad del entorno utilizando los sensores del portador.
* carrier.Buttons.update();.Actualiza el estado de los botones táctiles.
* Imprime la temperatura actual en grados Celsius a través de la comunicación serie y convierte la temperatura a Fahrenheit y Kelvin.
* Verifica si se ha tocado alguno de los tres botones táctiles (TOUCH0, TOUCH1, TOUCH2) y, en caso afirmativo, llama a la función printTemperature con la temperatura convertida y la unidad correspondiente

### FUNCIÓN PARA IMPRIMIR LA TEMPERATURA EN LA PANTALLA (printTemperature)


```cpp
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

````

* Configura la pantalla TFT para mostrar la temperatura en un formato específico. En este caso se utiliza un fondo rojo y texto blanco.

### Imagenes como prueba de los resultados del ejercicio

<p align="center">
  <img src="" alt="" width="400px" />
</p>


## EJERCICIO 3 y 4

| Explicación  |  Error  | 
| :------------ |:---------------:| 
| | [![ERROR1.jpg](https://i.postimg.cc/15XLhL2H/ERROR1.jpg)](https://postimg.cc/KRX9tsZk)| [![Whats-App-Image-2024-01-23-at-2-20-01-AM.jpg](https://i.postimg.cc/Lss7b8kS/Whats-App-Image-2024-01-23-at-2-20-01-AM.jpg)](https://postimg.cc/DStBWFYp)|
| | [![Error-2.jpg](https://i.postimg.cc/5NQnm1DZ/Error-2.jpg)](https://postimg.cc/nCZ4F8Fk)| [![Whats-App-Image-2024-01-23-at-2-20-01-AM.jpg](https://i.postimg.cc/Lss7b8kS/Whats-App-Image-2024-01-23-at-2-20-01-AM.jpg)](https://postimg.cc/DStBWFYp)|

<p align="center">
  <img src="" alt="" width="400px" />
</p>

## Conclusión
En conclusion, todo lo experimentando y aprendido, tiene como objetivo principal familiarizar a los participantes con la MKR IoT Carrier del Arduino Oplà IoT Kit. que  permite aprender y comprender el uso de los actuadores y sensores. En el presente informe se realizo para cuatro ejercicios (por problemas tecnicos solo se logro para dos ejercicios). Tales ejercicios servira como base para proyectos futuros estableciendo una base sólida para la comprensión y aplicación práctica de este componente en el ámbito del Internet de las cosas.


