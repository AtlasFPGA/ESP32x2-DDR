# ESP32x2-RELOCATOR-DDR
Conseguir unir 2 Esp32, creando un bus DDR de 12Bits.

En este inicio del esquema del ESP32x2-DDR se plantea incorporar y tener accesibles los buses ARDUINO MKR y ARDUINO MEGA.
![Esquema](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/PRIMER-MULTI-ESQUEMA-DIFERETES-PINEADOS.jpg)

Idea del bus DDR, 12 pines, permite buses de datos de 8Bits en adelante, y direcciones igualmente de 8 direccionamientos a los ya no lógicos para un microcontrolador superar los 16Mbytes. Así que definimos un escenario para dos ESP32 que comparten memoria mediante un bus DDR programado.

![IDEA ESP32x2-DDR](Primera definición bus ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/MAPEO-LINEAL-ESP32x2-SI5351-photo_2023-04-09_17-04-53-ANTI.png)

Es un diseño en fase muy inicial, pero con el uso de la VGA64, es muy importante el ESP32, como esta definido con un sólo ESP32 y recolocando con dupont, se puede recompilar los proyectos actuales, un punto de apoyo, al tener Teclado y Vga en el ESP32-VIDEO.1

Como es un bús que tiene que ser analizado y creado, se han posicionado 12 puntos de test:

CLK+
CLK-
SEL01
SEL02
AD[7:0]

CARA SUPERIOR ESP32x2-DDR:

![CARA SUPERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-SUPERIOR-ESP32x2-DDR.jpg)

CARA INFERIOR se puede ver que hay un bus de ARDUINO MEGA:

![CARA INFERIOR ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/CARA-INFERIOR-ESP32x2-DDR.jpg)

Perpectiva ESP32x2-DDR

![PERSPECTIVA ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/VISION-PERSPECTIVA-ESP32x2-DDR.jpg)
