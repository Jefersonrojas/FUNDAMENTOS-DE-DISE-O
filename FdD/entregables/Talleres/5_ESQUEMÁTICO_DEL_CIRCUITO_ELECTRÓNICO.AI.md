
  <p align="center" style="margin-top: 50px; margin-bottom: 50px; font-family: Arial, sans-serif;">
  <p align="center">
    <img src="https://i.postimg.cc/pXjm2knB/Grupo-08.jpg)](https://postimg.cc/ZCTbH8H9)" width="1000" alt="logo">
  </p>  
 
   </p>  
  <h1 align="center" style="margin-top: 30px; margin-bottom: 0px;">Taller N° 05:</h1>
</p>
 </p>  
  <h1 align="center" style="margin-top: 30px; margin-bottom: 0px;">"  Esquemático del Circuito Electrónico en Flux.ia"</h1>
</p>
 
#### Profesores a cargo de la actividad:
* ###### *Mg. Umbert Lewis De la Cruz Rodriguez*
* ###### *Mg. Moises Stevend Meza Rodriguez*
* ###### *Dr. Harry Anderson Rivera Tito*


## 1. INTRODUCCIÓN
*Los esquemáticos de un circuito electrónico son una representación gráfica  de un circuito eléctrico que sirve como herramienta visual para el diseño proporcionando una visualización clara y concisa de la estructura y conexiones de los componentes electrónicos en un sistema, asi como la construcción y el mantenimiento de equipos eléctricos y electrónicos utilizando imágenes de los distintos componentes o símbolos estándar. La elaboración de esquemáticos presenta una representación simplificada de los elementos del circuito y sus interconexiones.

## 2. EJERCICIOS REALIZADOS EN CLASE 

### Ejercicio 1: Circuito electrónico: "Encendido de un Led"

##### COMPONENTES DEL CIRCUITO 
*Dos módulos de infrarrojos*
*un adaptador I2C*
*LCD 1602 pantalla LCD*
*un servomotor*
*Un Arduino nano*
| IMAGEN |   | 
| :------------ |:---------------:| 
| 1. [![Whats-App-Image-2024-02-09-at-11-13-21-PM.jpg](https://i.postimg.cc/fbBj1qP1/Whats-App-Image-2024-02-09-at-11-13-21-PM.jpg)](https://postimg.cc/VS0CCgmF)| [2. [![Whats-App-Image-2024-02-09-at-11-14-01-PM.jpg](https://i.postimg.cc/QdDz3P6M/Whats-App-Image-2024-02-09-at-11-14-01-PM.jpg)](https://postimg.cc/Wh98m9cR)|
| 3. [![Whats-App-Image-2024-02-09-at-11-16-08-PM.jpg](https://i.postimg.cc/Ls60qPFK/Whats-App-Image-2024-02-09-at-11-16-08-PM.jpg)](https://postimg.cc/3kVZVdwn) | 4.[![Whats-App-Image-2024-02-09-at-11-14-59-PM.jpg](https://i.postimg.cc/cHv9hNJF/Whats-App-Image-2024-02-09-at-11-14-59-PM.jpg)](https://postimg.cc/N9wkGSmX) |


FUENTE: Elaboración grupo 8,Fundamentos de Diseño, 2024-0

* #### DESCRIPCIÓN
En el presente ejercicio con guía del docente Moises, se logró elaborar un circuito empleando una placa Arduino Nano (no empleamos el Arduino Uno, que fue lo recomendable para nuestro ejercicio, ya que será la placa con la que se trabajara en nuestro proyecto general, debido a que esta no se encontraba apta en la plataforma Flux.ia), así también, se hizo uso de un led, botón, resistor y dos tierras, que serán los elementos para la conexión. El resistor será conectado con un PIN libre en nuestro caso empleamos el D9 que a su vez estará conectado con el led y este con la tierra, por consiguiente, se escogió otro PIN libre, en nuestro caso el D10 que se conectó con el botón y este a tierra. Para este ejercicio los dispositivos estaban orientados en la posición botón (cuadro 2) que se caracteriza por estar de color azul, por otro lado, para tener una vista más amplia a la conexión se puso todo el circuito en vista 3D (cuadro 3 y 4).

### Ejercicio 2: Circuito electrónico "Control de acceso a parking"
El siguiente ejercicio tuvo como finalidad reforzar los conocimientos adquiridos en el primer ejercicio. El cual era realizar el diseño de un circuito electrónico considerando 6 componentes como mínimo.  

| Componentes |  IMAGEN | 
| :------------ |:---------------:| 
|  Arduino Nano 
Microcontrolador con 16 pines digitales, versión reducida de la placa Arduino Uno R3, pero con dos pines analógicos adicionales. Entre sus características técnicas contiene un microcontrolador ATMega328P con velocidad de reloj de 16 MHz.|[![Arduino-Nano-V3-0-con-FT232-Incluye-cable-USB-Mini-1.jpg](https://i.postimg.cc/63zTBK25/Arduino-Nano-V3-0-con-FT232-Incluye-cable-USB-Mini-1.jpg)](https://postimg.cc/Fddhx2V2) |
|Pantalla LCD 16x2
Permite mostrar texto y números en una disposición de dos líneas de texto de 16 caracteres cada una. Esta conformado por dos partes principalmente: un PCB que aloja el controlador de pantalla LCD y la pantalla de cristal liquido (LCD) propiamente. | [![Pantalla-LCD.jpg](https://i.postimg.cc/fRjV8Yz9/Pantalla-LCD.jpg)](https://postimg.cc/SnRQs2zS) |
| Servomotor 
Alimentado por corriente continua que puede controlar de modo muy exacto la posición (de 0º a 180º) o la velocidad (en revoluciones por minuto, rpm, en sentido horario o antihorario). Tienen 3 pines para su conexión: alimentación (5V), tierra (GND) y el pin de la señal|[![Servomotor.jpg](https://i.postimg.cc/Nf86FBp8/Servomotor.jpg)](https://postimg.cc/PPxpFsGN)| 
| Sensor ultrasónico
Detecta objetos a distancias que van desde pocos centímetros hasta varios metros y emite un sonido, además mide el tiempo que la señal tarda en regresar. Su funcionamiento solamente es en el aire, y puede detectar objetos con diferentes formas, colores, superficies y de diferentes materiales.| [![sensor-ultrasonico.jpg](https://i.postimg.cc/2jxm1tq7/sensor-ultrasonico.jpg)](https://postimg.cc/grr15NHx)|
| Potenciómetro 
Componente electrónico similar a los resistores pero cuyo valor de resistencia en vez de ser fijo es variable, haciendo posible controlar la intensidad de corriente a lo largo de un circuito conectándolo en paralelo ó la caida de tensión al conectarlo en serie.|[![Potenci-metro.jpg](https://i.postimg.cc/Zqx2xGb6/Potenci-metro.jpg)](https://postimg.cc/qtg1kZC7)| 
|Led rojo y blanco|[![Led.png](https://i.postimg.cc/CxW9kd52/Led.png)](https://postimg.cc/k2vjdJxN) |
|2 Resistencias de 500 ohmios|[![resistencias.png](https://i.postimg.cc/jqgWkBWQ/resistencias.png)](https://postimg.cc/yWRYDQyk)|



## 3. CONCLUSIÓN 
Por todo lo hablado, se queda por concluir que los esquemáticos de los circuitos electrónicos, son de suma importancia ya que es la herramienta visual que nos permite comprender y entender el diseño de los circuitos electrónicos, tal fue el caso con el ejercicio número 1 que se realizó en clase, nos permitió interpretar de manera global la conección de cada elemento, así también, entendiendo conceptos como bottom y top y ya a manera de práctica empleando los conceptos proporcionados en clase se realizó un nuevo circuito con seis elementos, donde el objetivo era dar a conocer la disponibilidad de espacio en un estacionamiento de carros,brindando a los usuarios la disponibilidad del espacio en el área de parqueo, con los conceptos más sólidos pudimos comprender el taller en la plataforma Flux.ia.

