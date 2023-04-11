# RECOLOCADOR ESP32x2-DDR, ESP32x2-DDR-RELOCATOR
   Conseguir unir 2 Esp32, creando un bus DDR de 12 señales es muy importante.
   Las placas ESP32 tienen una gran intrucción en el mercado por sus prestaciones/precios desde hace más de 8 años.

   En este inicio del esquema del ESP32x2-DDR se plantea incorporar y tener accesibles los buses ARDUINO MKR y ARDUINO MEGA.
![Esquema](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/PRIMER-MULTI-ESQUEMA-DIFERETES-PINEADOS.jpg)

   El sistema con el ESP32x1-GO, puede usar todos los códigos, únicamente teniendo en cuenta que hay que variar las posiciones de los pines; dado que estas vienen marcadas por la asignación previa de usar el diseño ESP32-2-DDR, con esta placa ESP32x1-GO sería dar el primer;despues sería agregar un módulo SI5351 y otro ESP32 DEV KIT V1.
   
   Asignaciones ESP32x1-GO que substituyen al ESP32-AUDIO:
   
![ESP32x1-GO ASIGNACIONES](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/ASIGNACIONES-ESP32x1-GO-photo_2023-04-11_12-57-55.jpg)

   Vista en perspectiva:
   
![COMPATIBILIDAD VIA FUENTES ESP32x1-GO](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/PLACA-ESP32x1-GO-photo_2023-04-11_12-50-03.jpg)

   Diagrama ESP32-VIDEO ESP32-AUDIO:
  
| BLOQUES FUNCIONALES ESP32-VIDEO CARA INFERIOR|
| ------------- |
| VGA64_222_HS_VS  |
| TECLADO PS2  |
| RATÓN_PS2 |
| EAR  |


| BLOQUES FUNCIONALES ESP32-AUDIO CARA SUPERIOR|
| ------------- |
| MANDO ATARI DB9 |
| SD_SPI  |
| I2C_SI5351  |
| DELTASIGMA MONO  |


   Idea del bus DDR, 12 pines, permite buses de datos de 8Bits en adelante, y direcciones igualmente de 8/16/24 usando bloques de 8bit, a los ya no lógicos 32bit para un microcontrolador que son unos 4Gbytes, para un microcontrolador esp32 los 24 bits de direcciones usando AD[7:0] tres veces en el tiempo, los 16Mbytes permite tanto mapear parte de la memoria sram interna como la spesudosram de ambos ESP32. Así que definimos un escenario para dos ESP32 que comparten memoria mediante un bus DDR programado(sólo se plantea el mismo).

![IDEA ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/MAPEO-LINEAL-ESP32x2-SI5351-photo_2023-04-09_17-04-53-ANTI.png)

   Es un diseño en fase muy inicial, pero con el uso de la "VGA64" o "EUROCONECTOR128" hay salida de vídeo analógica lo que es muy importante; es que con un sólo ESP32, y cables dupont se tienen los 25 pines del ESP32 DEV KIT V1,es necesario tener un punto de apoyo inicial, al tener el que llamamos ESP32-VIDEO Teclado así como Vga, si se cambia el pineado se obtiene como resultado la compatibilidad con gran parte del software preexistente.

   Todo el proyecto ESP32x2-DDR no tiene software actualmente, teóricamente parece viable, y al descargar de proceso cuando se tiene un SI5351, habrá que ver como se puede subir las frecuencias del bus ESP32x2-DDR.

   Como es un bús que tiene que ser analizado y creado, se han posicionado 12 puntos de test:

- CLK+    --> Señal generada por el SI5351.
- CLK-    --> Señal generada por el SI5351 con un restraso de 180º o pi Radianes.
- SEL01   --> Matriz de estados Señal 02.
- SEL02   --> Matriz de estados Señal 01.
- AD[7:0] --> Bus de direcciones y de datos, sin definir sus tamaños en realidad.

   Al tener los relojes podemos diseñar un bus DDR.

   Se define un bus de intercambio lineal.

   Matriz de casos/estados:

| MATRIZ DE ESTADOS | SEL01 | SEL02 |
| ------------- | ------------- | ------------- |
| Dirección de lectura  | 0  | 0 |
| Lectura de datos  | 0  | 1 |
| Dirección de escritura  | 1  | 0 |
| Escritura de datos  | 1  | 1 |

   Al aplicar el bus ESP32x2-DDR tenemos 1 pin más que con un ESP32 único:

   Mapa de señales del ESP32x2-DDR, son en total 26 señales(Hay que tener en cuenta que cada ESP32 tiene 4 entradas marcadas como de sólo entrada):
   

| Número de pines o señales  | nombre de la señal|
| ------------- | ------------- |
| 8 Señales   | VGA64_222_HS_VS  |
| 4 Señales   | SD_SPI  |
| 6 Señales   | MANDO ATARI DB9 |
| 2 Señales   | I2C_SI5351  |
| 2 Señales   | TECLADO PS2  |
| 2 Señales   | RATÓN_PS2 |
| 1 Señales   | DELTASIGMA MONO  |
| 1 Señales   | EAR  |


   CARA SUPERIOR ESP32x2-DDR vemos los 12 puntos de test:

![CARA SUPERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-SUPERIOR-ESP32x2-DDR.jpg)

   CARA INFERIOR se puede ver que hay un bus de ARDUINO MEGA:

![CARA INFERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-INFERIOR-ESP32x2-DDR.jpg)

   Perspectiva ESP32x2-DDR

![PERSPECTIVA ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/VISION-PERSPECTIVA-ESP32x2-DDR.jpg)
