# ESP32x2-RELOCATOR-DDR
Conseguir unir 2 Esp32, creando un bus DDR de 12Bits.

En este inicio del esquema del ESP32x2-DDR se plantea incorporar y tener accesibles los buses ARDUINO MKR y ARDUINO MEGA.
![Esquema](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/PRIMER-MULTI-ESQUEMA-DIFERETES-PINEADOS.jpg)

Idea del bus DDR, 12 pines, permite buses de datos de 8Bits en adelante, y direcciones igualmente de 8 direccionamientos a los ya no lógicos para un microcontrolador superar los 16Mbytes. Así que definimos un escenario para dos ESP32 que comparten memoria mediante un bus DDR programado.

![IDEA ESP32x2-DDR]([Primera definición bus ESP32x2-DDR](https://github.com/AtlasFPGA/ESP32x2-DDR/blob/main/FOTOS/MAPEO-LINEAL-ESP32x2-SI5351-photo_2023-04-09_17-04-53-ANTI.png)
