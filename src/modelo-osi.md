# Modelo OSI

<!-- toc -->

Describe la comunicación y el envió de los datos entre un sistema remitente y destinatario.

## Capas

1. Física
2. Encale de Datos
3. Red
4. Transporte
5. Sesión
6. Presentación
7. Aplicación

## Definiciones

### Trama

Una trama es una unidad de paquete de datos compuesta por bits que transportan información y permiten al receptor extraer información.

Consta por un encabezado - datos - tráiler. En el encabezado se suele encontrar información del protocolo y en el tráiler algún tipo de chequeo de errores.

### Protocolo

Es un estándar para la comunicación de red entre emisor y receptor, análogo a un idioma, necesitamos comunicarnos en el mismo idioma (p.e Español) para que el emisor y receptor puedan entenderse.

## Capa 1. Física

<!-- #AraSuspended78 -->

Medio de transmisión binaria de cable o inalámbrica.

### Funciones

Medio en el que se envían los datos en forma de en señales eléctricas para su transmisión física a nivel de bits en forma serial o paralela.

<!-- #EgidiusEmptied8 -->

## Capa 2. Enlace de Datos

<!-- #ChericeDrys123 -->

Direcciona las señales físicas recibidas a su destino local.

Es un intermediaria entre la capa de red y la capa física. Actúa en el área local (LAN), transfiere tramas de datos entre dos nodos conectados directamente en la misma red.

### Funciones

- Codifica las tramas de la capa de red para su transmisión a la capa física.
- <!-- #duda --> Funciona con una tabla de direcciones MAC.

### Subcapas

La capa de enlace de Datos se divide en dos subcapas importantes que son LLC y MAC.

#### LLC

> Control de Enlace Lógico

- Mantiene las conexiones lógicas.
- Controla la secuencia de las tramas.
- detecta y corrige errores, asegurando que los datos se transmiten correctamente.

#### MAC

> Método de Acceso al Medio

- Controla como los dispositivos acceden y utilizan el medio (p.e Ethernet) para enviar y recibir datos.
- Gestiona como  un equipo en la red obtiene acceso a los datos y permisos con el fin de transmitirlos.

<!-- #duda cual es la relación exacta entre LLC y MAC? -->

<!-- #JehialFilled62 -->

<!-- cablemap.info -->
