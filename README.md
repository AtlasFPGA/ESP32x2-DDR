# RECOLOCADOR ESP32x2-DDR, ESP32x2-DDR-RELOCATOR
Conseguir unir 2 Esp32, creando un bus DDR de 12Bits.

En este inicio del esquema del ESP32x2-DDR se plantea incorporar y tener accesibles los buses ARDUINO MKR y ARDUINO MEGA.
![Esquema](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/PRIMER-MULTI-ESQUEMA-DIFERETES-PINEADOS.jpg)

Idea del bus DDR, 12 pines, permite buses de datos de 8Bits en adelante, y direcciones igualmente de 8 direccionamientos a los ya no lógicos para un microcontrolador superar los 16Mbytes. Así que definimos un escenario para dos ESP32 que comparten memoria mediante un bus DDR programado.

![IDEA ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/MAPEO-LINEAL-ESP32x2-SI5351-photo_2023-04-09_17-04-53-ANTI.png)

Es un diseño en fase muy inicial, pero con el uso de la VGA64, es muy importante el ESP32, como esta definido con un sólo ESP32 y recolocando con dupont, se puede recompilar los proyectos actuales, un punto de apoyo, al tener Teclado y Vga en el ESP32-VIDEO.

Como es un bús que tiene que ser analizado y creado, se han posicionado 12 puntos de test:

- CLK+    --> Señal generada por el SI5351.
- CLK-    --> Señal generada por el SI5351 con un restraso de 180º o pi Radianes.
- SEL01   --> Matriz de estados Señal 01
- SEL02   --> Matriz de estados Señal 01
- AD[7:0] --> Bus de direcciones y de datos, sin definir sus tamaños en realidad.

Al tener los relojes podemos diseñar un bus DDR.

Se define un bus de intercambio lineal.

Matriz de casos:
| MATRIZ ESTADOS | SEL01 | SEL02 |
| ------------- | ------------- | ------------- |
| Dirección de lectura  | 0  | 0 |
| Lectura de datos  | 0  | 1 |
| Dirección de escritura  | 1  | 0 |
| Escritura de datos  | 1  | 1 |

Al aplciar el bus ddr tenemos 1 pin más que con un ESP32 único:

Mapa de señales del ESP32x2-DDR, son en total 26 señales:
(Hay que tener en cuenta que cada ESP32 tiene 4 entradas marcadas como de sólo entrada)

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


CARA SUPERIOR ESP32x2-DDR:

![CARA SUPERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-SUPERIOR-ESP32x2-DDR.jpg)

CARA INFERIOR se puede ver que hay un bus de ARDUINO MEGA:

![CARA INFERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-INFERIOR-ESP32x2-DDR.jpg)

Perpectiva ESP32x2-DDR

![PERSPECTIVA ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/VISION-PERSPECTIVA-ESP32x2-DDR.jpg)
