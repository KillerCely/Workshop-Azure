# Workshop-Azure

- [Descripción de la implementación](#descripcion-de-la-implementacion)
- [Sensores](#etapa-de-desarrollo)
- [Hardware](#hardware)
- [Etapa de Implementación](#etapa-de-implementación)

Hecho por:
- Carlos Gutierrez
- Robinson Cely

# Descripción de la implementación

La Internet de las cosas (IoT) describe la red de objetos físicos ("cosas") que llevan incorporados sensores, software y otras tecnologías con el fin de conectarse e intercambiar datos con otros dispositivos y sistemas a través de Internet. Estos dispositivos van desde objetos domésticos comunes hasta herramientas industriales sofisticadas. Con más de 7 mil millones de dispositivos IoT conectados en la actualidad, los expertos prevén que este número aumentará a 10 mil millones para el 2020 y 22 mil millones para el 2025.

En los últimos años, IoT se ha convertido en una de las tecnologías más importantes del siglo XXI. Ahora que podemos conectar objetos cotidianos, electrodomésticos, coches, termostatos, monitores de bebés, a Internet a través de dispositivos integrados, es posible una comunicación fluida entre personas, procesos y cosas.

Mediante la informática de bajo costo, la nube, big data, analítica y tecnologías móviles, las cosas físicas pueden compartir y recopilar datos con una mínima intervención humana. En este mundo hiperconectado, los sistemas digitales pueden grabar, supervisar y ajustar cada interacción entre las cosas conectadas. El mundo físico y el digital van de la mano y cooperan entre sí.

Para la implementación, se conectara una Raspberry Pi con un sensor de temperatura y humedad que estara conectado a la plataforma de Azure, Microsoft Azure es un servicio de computación en la nube creado por Microsoft para construir, probar, desplegar y administrar aplicaciones y servicios mediante el uso de sus centros de datos. Con este servicio de Microsoft, queremos hacer la conexión de la Raspberry a IoT Hub de Azure y verificar como funciona el internet de las cosas.

# Sensores

En la implementación, se utiliza un sensor BME280, el sensor BME280 integra en un solo dispositivo sensores de presión atmosférica, temperatura y humedad relativa, con gran precisión, bajo consumo energético y un formato ultra compacto.

<p align="center">
  <img width="400" height="500" src="https://github.com/KillerCely/Workshop-Azure/blob/main/61A76CnJ-LL._SL1500_.jpg">
</p>

Se conecta directamente a un microcontrolador a través de I2C o SPI, el I2C es un puerto y protocolo de comunicación serial, define la trama de datos y las conexiones físicas para transferir bits entre 2 dispositivos digitales. El puerto incluye dos cables de comunicación, SDA y SCL. Mientras que SPI, es un estándar de comunicaciones, usado principalmente para la transferencia de información entre circuitos integrados en equipos electrónicos. El bus de interfaz de periféricos serie o bus SPI es un estándar para controlar casi cualquier dispositivo electrónico digital que acepte un flujo de bits serie regulado por un reloj (comunicación sincrónica).

# Hardware

Para el desarrollo del hardware, se implementa un simulador de Microsoft con una Raspberry Pi conectada al sensor mencionado anteriormente, de la siguiente manera.

<p align="center">
  <img width="400" height="500" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_194600290.png">
</p>

La Raspberry Pi es una serie de ordenadores de placa reducida, ordenadores de placa única u ordenadores de placa simple (SBC) de bajo costo desarrollado en el Reino Unido por la Raspberry Pi Foundation, como clon directo del Apple Mac Mini, que se lanzó en enero de 2005, con el objetivo de poner en manos de las personas de todo el mundo el poder de la informática y la creación digital.

Tambien, se implementa un codigo de comunicación entre la RaspBerry Pi con el Hub de Azure, donde estará alojada la información que este sensor mande, como se evidencia en la siguiente imagen.

<p align="center">
  <img width="600" height="600" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_200513627.png">
</p>

Mediante este codigo, y al IoT Hub y una clave primaria que da el mismo sistema de azure al crear un dispositivo nuevos como IoT, esta clave la usaremos para conectarnos.

# Etapa de Implementación

En Azure, se creara un IoT Hub, Azure IoT Hub ofrece un back-end de solución hospedado en la nube que permite conectarse prácticamente a cualquier dispositivo.

<p align="center">
  <img width="600" height="600" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_201553439.png">
</p>

Teniendo listo el Hub creado, procedemos a crear un nuevo dispositivo para conectar la IoT, para este paso definimos un nombre del dispositivo.

<p align="center">
  <img width="600" height="600" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_201856221.png">
</p>

Al crear el dispositivo, la misma plataforma nos informara una clave de acceso que tendra este dispositivo para conectarse al Hub y poder que lleguen los datos al mismo, procedemos a encontrar la clave primaria y la pegamos en el simulador, en el codigo en el rengln #15.

<p align="center">
  <img width="1000" height="800" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_202045340.png">
</p>

Y listo, se prueba la conexión corriendo la simulación y verificamos que por consola se verifique que se esta enviando la información al Hub.

<p align="center">
  <img width="1000" height="800" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_202251573.png">
</p>

Verificamos en el Hub que inicialmente tiene 0 mensajes recibidos.

<p align="center">
  <img width="1000" height="800" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-04_200216708.png">
</p>

Y encontramos que la conexción entre la RaspBerry Pi es correcta porque en el Hub nos evidencia o nos notifica la cantidad de mensajes recibidos.

<p align="center">
  <img width="1000" height="800" src="https://github.com/KillerCely/Workshop-Azure/blob/main/imagen_2022-05-02_152449275.png">
</p>


