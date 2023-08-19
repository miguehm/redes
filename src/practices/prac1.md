# Practica 1

# Comando HOSTNAME

a) ¿Para que sirve este comando?

Sirve para mostrar el nombre del equipo

b) ¿Cual es el nombre de tu equipo?

DESKTOP_DQ1BRT

c) ¿Tiene algun parametro ese comando?

```bash
-a, --alias: Muestra el nombre alias del host.
-A, --all-fqdns: Muestra todos los FQDN (Fully Qualified Domain Name) del ordenador.
-b, --boot: Establece siempre un nombre de host.
-d, --domain: Muestra el nombre de dominio DNS.
-f, --fqdn, --long: Muestra el FQDN.
-F, --file: Comprueba un archivo para recuperar y mostrar el nombre de host.
-h, --help: Imprime el mensaje de ayuda como salida.
-i, --ip-address: Muestra la dirección IP del ordenador.
-I, --all-ip-addresses: Muestra todas las direcciones de red del ordenador.
-s, --short: Muestra la versión corta del nombre de host.
-v, --verbose: Expande toda la salida a verbose.
-y, --yp, --nis: Muestra el nombre de dominio NIS.
```

# Comando PING

Probar los siguientes ejemplos y anotar los resultados obtenidos

a) ping –t localhost

```bash
C:\Users\user>ping -t localhost

Haciendo ping a DESKTOP-DQP1BRI [::1] con 32 bytes de datos:
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m

Estadísticas de ping para ::1:
    Paquetes: enviados = 9, recibidos = 9, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

b) ping –a localhost

```bash
C:\Users\user>ping -a localhost

Haciendo ping a DESKTOP-DQP1BRI [::1] con 32 bytes de datos:
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m

Estadísticas de ping para ::1:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

c) ping –n 10 localhost

```bash
C:\Users\user>ping -n 10 localhost

Haciendo ping a DESKTOP-DQP1BRI [::1] con 32 bytes de datos:
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m

Estadísticas de ping para ::1:
    Paquetes: enviados = 10, recibidos = 10, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

d) ping –f localhost

```bash
C:\Users\user>ping -f localhost

Haciendo ping a DESKTOP-DQP1BRI [127.0.0.1] con 32 bytes de datos:
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128

Estadísticas de ping para 127.0.0.1:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

e) ping –i 200 localhost

```bash
C:\Users\user>ping -i 200 localhost

Haciendo ping a DESKTOP-DQP1BRI [::1] con 32 bytes de datos:
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m

Estadísticas de ping para ::1:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

f) ping –r 6 localhost

```bash
C:\Users\user>ping -r 6 localhost

Haciendo ping a DESKTOP-DQP1BRI [127.0.0.1] con 32 bytes de datos:
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128
Respuesta desde 127.0.0.1: bytes=32 tiempo<1m TTL=128

Estadísticas de ping para 127.0.0.1:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

g) ping –w 233 localhost

```bash
C:\Users\user>ping -w 233 localhost

Haciendo ping a DESKTOP-DQP1BRI [::1] con 32 bytes de datos:
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m
Respuesta desde ::1: tiempo<1m

Estadísticas de ping para ::1:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 0ms, Máximo = 0ms, Media = 0ms

```

# Comando IPCONFIG

Muestra la configuración IP de tu equipo

Probar los siguientes ejemplo y anotarlos

a. ipconfig

```bash
C:\Users\user>ipconfig

Configuración IP de Windows


Adaptador de Ethernet Ethernet:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Conexión de área local* 1:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Conexión de área local* 2:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Wi-Fi:

   Sufijo DNS específico para la conexión. . : www.tendawifi.com
   Vínculo: dirección IPv6 local. . . : fe80::8315:b7f7:8d99:e169%16
   Dirección IPv4. . . . . . . . . . . . . . : 192.168.0.106
   Máscara de subred . . . . . . . . . . . . : 255.255.255.0
   Puerta de enlace predeterminada . . . . . : 192.168.0.1

```

b. ipconfig /all

```bash
C:\Users\user>ipconfig /all

Configuración IP de Windows

   Nombre de host. . . . . . . . . : DESKTOP-DQP1BRI
   Sufijo DNS principal  . . . . . :
   Tipo de nodo. . . . . . . . . . : híbrido
   Enrutamiento IP habilitado. . . : no
   Proxy WINS habilitado . . . . . : no
   Lista de búsqueda de sufijos DNS: www.tendawifi.com

Adaptador de Ethernet Ethernet:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :
   Descripción . . . . . . . . . . . . . . . : Realtek PCIe GbE Family Controller
   Dirección física. . . . . . . . . . . . . : F0-2F-74-CC-FE-5C
   DHCP habilitado . . . . . . . . . . . . . : sí
   Configuración automática habilitada . . . : sí

Adaptador de LAN inalámbrica Conexión de área local* 1:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :
   Descripción . . . . . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter
   Dirección física. . . . . . . . . . . . . : 2A-EE-52-14-17-B7
   DHCP habilitado . . . . . . . . . . . . . : sí
   Configuración automática habilitada . . . : sí

Adaptador de LAN inalámbrica Conexión de área local* 2:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :
   Descripción . . . . . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter #2
   Dirección física. . . . . . . . . . . . . : 28-EE-52-14-17-B7
   DHCP habilitado . . . . . . . . . . . . . : sí
   Configuración automática habilitada . . . : sí

Adaptador de LAN inalámbrica Wi-Fi:

   Sufijo DNS específico para la conexión. . : www.tendawifi.com
   Descripción . . . . . . . . . . . . . . . : TP-Link High Power Wireless USB Adapter
   Dirección física. . . . . . . . . . . . . : 28-EE-52-14-17-B7
   DHCP habilitado . . . . . . . . . . . . . : sí
   Configuración automática habilitada . . . : sí
   Vínculo: dirección IPv6 local. . . : fe80::8315:b7f7:8d99:e169%16(Preferido)
   Dirección IPv4. . . . . . . . . . . . . . : 192.168.0.106(Preferido)
   Máscara de subred . . . . . . . . . . . . : 255.255.255.0
   Concesión obtenida. . . . . . . . . . . . : domingo, 3 de julio de 1887 08:42:23 p. m.
   La concesión expira . . . . . . . . . . . : jueves, 10 de agosto de 2023 09:10:39 p. m.
   Puerta de enlace predeterminada . . . . . : 192.168.0.1
   Servidor DHCP . . . . . . . . . . . . . . : 192.168.0.1
   IAID DHCPv6 . . . . . . . . . . . . . . . : 153677394
   DUID de cliente DHCPv6. . . . . . . . . . : 00-01-00-01-2C-0C-57-8A-F0-2F-74-CC-FE-5C
   Servidores DNS. . . . . . . . . . . . . . : 192.168.0.1
   NetBIOS sobre TCP/IP. . . . . . . . . . . : habilitado

```
c. ipconfig /displaydns

```bash
C:\Users\user>ipconfig /displaydns

Configuración IP de Windows

    static-ecst.licdn.com
    ----------------------------------------
    Nombre de registro  . : static-ecst.licdn.com
    Tipo de registro  . . : 5
    Período de vida . . . : 2805
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : cs1404.wpc.epsiloncdn.net


    Nombre de registro  . : cs1404.wpc.epsiloncdn.net
    Tipo de registro  . . : 1
    Período de vida . . . : 2805
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 152.199.24.163


    www-amazon-com-mx.customer.fastly.net
    ----------------------------------------
    Nombre de registro  . : www-amazon-com-mx.customer.fastly.net
    Tipo de registro  . . : 28
    Período de vida . . . : 2367
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2606:2cc0::878


    Nombre de registro  . : www-amazon-com-mx.customer.fastly.net
    Tipo de registro  . . : 28
    Período de vida . . . : 2367
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2606:2cc0:1::878


    Nombre de registro  . : www-amazon-com-mx.customer.fastly.net
    Tipo de registro  . . : 28
    Período de vida . . . : 2367
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2606:2cc0:2::878


    Nombre de registro  . : www-amazon-com-mx.customer.fastly.net
    Tipo de registro  . . : 28
    Período de vida . . . : 2367
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2606:2cc0:3::878


    www-amazon-com-mx.customer.fastly.net
    ----------------------------------------
    Nombre de registro  . : www-amazon-com-mx.customer.fastly.net
    Tipo de registro  . . : 1
    Período de vida . . . : 2315
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 162.219.227.110


    rr4---sn-uvu5a2a5t-hxmle.googlevideo.com
    ----------------------------------------
    Nombre de registro  . : rr4---sn-uvu5a2a5t-hxmle.googlevideo.com
    Tipo de registro  . . : 5
    Período de vida . . . : 341
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : rr4.sn-uvu5a2a5t-hxmle.googlevideo.com


    Nombre de registro  . : rr4.sn-uvu5a2a5t-hxmle.googlevideo.com
    Tipo de registro  . . : 1
    Período de vida . . . : 341
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 186.96.52.79


    camo.githubusercontent.com
    ----------------------------------------
    Nombre de registro  . : camo.githubusercontent.com
    Tipo de registro  . . : 1
    Período de vida . . . : 719
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 185.199.109.133


    Nombre de registro  . : camo.githubusercontent.com
    Tipo de registro  . . : 1
    Período de vida . . . : 719
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 185.199.110.133


    Nombre de registro  . : camo.githubusercontent.com
    Tipo de registro  . . : 1
    Período de vida . . . : 719
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 185.199.111.133


    Nombre de registro  . : camo.githubusercontent.com
    Tipo de registro  . . : 1
    Período de vida . . . : 719
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 185.199.108.133


    tsfe.trafficshaping.dsp.mp.microsoft.com
    ----------------------------------------
    Nombre de registro  . : tsfe.trafficshaping.dsp.mp.microsoft.com
    Tipo de registro  . . : 5
    Período de vida . . . : 23
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : tsfe.trafficmanager.net


    Nombre de registro  . : tsfe.trafficmanager.net
    Tipo de registro  . . : 1
    Período de vida . . . : 23
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 40.119.46.46


    3.au.download.windowsupdate.com
    ----------------------------------------
    Nombre de registro  . : 3.au.download.windowsupdate.com
    Tipo de registro  . . : 5
    Período de vida . . . : 166
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : au.download.windowsupdate.com.c.footprint.net


    Nombre de registro  . : au.download.windowsupdate.com.c.footprint.net
    Tipo de registro  . . : 1
    Período de vida . . . : 166
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 8.50.5.254


    Nombre de registro  . : au.download.windowsupdate.com.c.footprint.net
    Tipo de registro  . . : 1
    Período de vida . . . : 166
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 8.50.13.126


    Nombre de registro  . : au.download.windowsupdate.com.c.footprint.net
    Tipo de registro  . . : 1
    Período de vida . . . : 166
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 8.50.4.254


    Nombre de registro  . : au.download.windowsupdate.com.c.footprint.net
    Tipo de registro  . . : 1
    Período de vida . . . : 166
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 8.50.12.254


    ocsp.digicert.com
    ----------------------------------------
    Nombre de registro  . : ocsp.digicert.com
    Tipo de registro  . . : 5
    Período de vida . . . : 2182
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : ocsp.edge.digicert.com


    Nombre de registro  . : ocsp.edge.digicert.com
    Tipo de registro  . . : 5
    Período de vida . . . : 2182
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : fp2e7a.wpc.2be4.phicdn.net


    Nombre de registro  . : fp2e7a.wpc.2be4.phicdn.net
    Tipo de registro  . . : 5
    Período de vida . . . : 2182
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : fp2e7a.wpc.phicdn.net


    Nombre de registro  . : fp2e7a.wpc.phicdn.net
    Tipo de registro  . . : 1
    Período de vida . . . : 2182
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 192.229.211.108


    blogger.l.google.com
    ----------------------------------------
    Nombre de registro  . : blogger.l.google.com
    Tipo de registro  . . : 28
    Período de vida . . . : 113
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2607:f8b0:4012:81e::2009


    blogger.l.google.com
    ----------------------------------------
    Nombre de registro  . : blogger.l.google.com
    Tipo de registro  . . : 1
    Período de vida . . . : 84
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 192.178.52.169


    rr4.sn-uvu5a2a5t-hxmle.googlevideo.com
    ----------------------------------------
    Nombre de registro  . : rr4.sn-uvu5a2a5t-hxmle.googlevideo.com
    Tipo de registro  . . : 28
    Período de vida . . . : 43
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2806:2f0:394:a203::f


    rr1---sn-uvu5a2a5t-hxmek.googlevideo.com
    ----------------------------------------
    Nombre de registro  . : rr1---sn-uvu5a2a5t-hxmek.googlevideo.com
    Tipo de registro  . . : 5
    Período de vida . . . : 42
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : rr1.sn-uvu5a2a5t-hxmek.googlevideo.com


    Nombre de registro  . : rr1.sn-uvu5a2a5t-hxmek.googlevideo.com
    Tipo de registro  . . : 1
    Período de vida . . . : 42
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 187.188.208.236


    array505.prod.do.dsp.mp.microsoft.com
    ----------------------------------------
    Nombre de registro  . : array505.prod.do.dsp.mp.microsoft.com
    Tipo de registro  . . : 1
    Período de vida . . . : 836
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 52.184.216.226


    rr1.sn-uvu5a2a5t-hxmek.googlevideo.com
    ----------------------------------------
    Nombre de registro  . : rr1.sn-uvu5a2a5t-hxmek.googlevideo.com
    Tipo de registro  . . : 28
    Período de vida . . . : 259
    Longitud de datos . . : 16
    Sección . . . . . . . : respuesta
    Registro AAAA . . . . : 2806:2f0:394:3200::c


    rr1.sn-uvu5a2a5t-hxmek.googlevideo.com
    ----------------------------------------
    Nombre de registro  . : rr1.sn-uvu5a2a5t-hxmek.googlevideo.com
    Tipo de registro  . . : 1
    Período de vida . . . : 43
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 187.188.208.236


    fe3cr.delivery.mp.microsoft.com
    ----------------------------------------
    Nombre de registro  . : fe3cr.delivery.mp.microsoft.com
    Tipo de registro  . . : 5
    Período de vida . . . : 134
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : fe3.delivery.mp.microsoft.com


    Nombre de registro  . : fe3.delivery.mp.microsoft.com
    Tipo de registro  . . : 5
    Período de vida . . . : 134
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : glb.cws.prod.dcat.dsp.trafficmanager.net


    Nombre de registro  . : glb.cws.prod.dcat.dsp.trafficmanager.net
    Tipo de registro  . . : 1
    Período de vida . . . : 134
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 20.242.39.171


    download.windowsupdate.com
    ----------------------------------------
    Nombre de registro  . : download.windowsupdate.com
    Tipo de registro  . . : 5
    Período de vida . . . : 97
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : wu-fg-shim.trafficmanager.net


    Nombre de registro  . : wu-fg-shim.trafficmanager.net
    Tipo de registro  . . : 5
    Período de vida . . . : 97
    Longitud de datos . . : 8
    Sección . . . . . . . : respuesta
    Registro CNAME. . . . : cds.d2s7q6s2.hwcdn.net


    Nombre de registro  . : cds.d2s7q6s2.hwcdn.net
    Tipo de registro  . . : 1
    Período de vida . . . : 97
    Longitud de datos . . : 4
    Sección . . . . . . . : respuesta
    Un registro (host). . : 209.197.3.8

```

d. ipconfig /renew

```bash
C:\Users\user>ipconfig /renew

Configuración IP de Windows

No se puede realizar ninguna operación en Ethernet mientras los medios
estén desconectados.
No se puede realizar ninguna operación en Conexión de área local* 1 mientras los medios
estén desconectados.
No se puede realizar ninguna operación en Conexión de área local* 2 mientras los medios
estén desconectados.

Adaptador de Ethernet Ethernet:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Conexión de área local* 1:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Conexión de área local* 2:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . :

Adaptador de LAN inalámbrica Wi-Fi:

   Sufijo DNS específico para la conexión. . : www.tendawifi.com
   Vínculo: dirección IPv6 local. . . : fe80::8315:b7f7:8d99:e169%16
   Dirección IPv4. . . . . . . . . . . . . . : 192.168.0.106
   Máscara de subred . . . . . . . . . . . . : 255.255.255.0
   Puerta de enlace predeterminada . . . . . : 192.168.0.1

```

# Comando ARP

¿Qué significa ARP?

ARP, o Protocolo de Resolución de Direcciones, es un protocolo de red que se utiliza para descubrir la dirección MAC (Media Access Control) de un dispositivo en la red a partir de su dirección IP. ARP es una parte integral de la comunicación en red y es responsable de mapear las direcciones IP a direcciones MAC

https://aprendeinformaticas.com/arp/

Un ejemplo práctico de esto podría ser el siguiente: Un dispositivo A en una red necesita enviar un paquete de datos a un dispositivo B. El dispositivo A conoce la dirección IP del dispositivo B, pero necesita su dirección MAC para la comunicación en la red. En este punto, el dispositivo A envía una solicitud ARP a todos los dispositivos en la red. Cuando el dispositivo B recibe esta solicitud y la encuentra dirigida a él, responde con su dirección MAC. El dispositivo A luego almacena esta información en su tabla ARP y utiliza la dirección MAC del dispositivo B para enviar el paquete de datos.

a) ¿Qué es una dirección MAC?

Una dirección MAC (Media Access Control) es un identificador único asignado por el fabricante a una pieza de hardware de red, como una tarjeta inalámbrica o una tarjeta Ethernet. Este código tiene la intención de ser único para un dispositivo en particular

https://help.gnome.org/users/gnome-help/stable/net-macaddress.html.es

La dirección MAC consta de seis grupos de dos caracteres, separados por dos puntos. Un ejemplo de una dirección MAC sería 00:1B:44:11:3A:B7. Este identificador es crucial para permitir que los dispositivos en una red se comuniquen entre síhelp.gnome.org.

Cada dirección MAC es única e indica el fabricante del equipo y el modelo exacto del dispositivo. Los tres primeros conjuntos identifican al fabricante y el resto es el identificador de producto en sí

b) ¿Qué MAC tienen tus adaptadores de RED? Apúntalos

```bash
Adaptador Ethernet
   Dirección física. . . . . . . . . . . . . : F0-2F-74-CC-FE-5C

Adaptador de LAN inalámbrica Conexión de área local* 1:
   Dirección física. . . . . . . . . . . . . : 2A-EE-52-14-17-B7

Adaptador de LAN inalámbrica Conexión de área local* 2:
   Dirección física. . . . . . . . . . . . . : 28-EE-52-14-17-B7

Adaptador de LAN inalámbrica Wi-Fi:
   Dirección física. . . . . . . . . . . . . : 28-EE-52-14-17-B7
```

c) ¿Qué entradas tiene tu equipo en la tabla caché ARP?

Para consultar la tabla cache se ejecuta el siguiente comando:

```bash
arp -av # muestra en modo detallado
```

Obteniendo lo siguiente:

```bash
C:\Users\user>arp -av

Interfaz: 127.0.0.1 --- 0x1
  Dirección de Internet          Dirección física      Tipo
  224.0.0.2                                   estático
  224.0.0.7                                   estático
  224.0.0.22                                  estático
  224.0.0.113                                 estático
  224.0.0.251                                 estático
  224.0.0.252                                 estático
  239.255.255.250                             estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.22            01-00-5e-00-00-16     estático
  224.0.0.113           01-00-5e-00-00-71     estático
  224.0.0.251           01-00-5e-00-00-fb     estático
  224.0.0.252           01-00-5e-00-00-fc     estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.22            01-00-5e-00-00-16     estático
  224.0.0.113           01-00-5e-00-00-71     estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.22            01-00-5e-00-00-16     estático
  224.0.0.113           01-00-5e-00-00-71     estático

Interfaz: 192.168.0.106 --- 0x10
  Dirección de Internet          Dirección física      Tipo
  192.168.0.1           08-40-f3-ad-53-48     dinámico
  192.168.0.104         fc-d9-08-da-9b-be     dinámico
  192.168.0.105         08-f4-58-7e-38-4f     dinámico
  192.168.0.109         00-00-00-00-00-00     no válido
  192.168.0.255         ff-ff-ff-ff-ff-ff     estático
  192.168.2.1           00-00-00-00-00-00     no válido
  224.0.0.22            01-00-5e-00-00-16     estático
  224.0.0.113           01-00-5e-00-00-71     estático
  224.0.0.251           01-00-5e-00-00-fb     estático
  224.0.0.252           01-00-5e-00-00-fc     estático
  239.255.255.250       01-00-5e-7f-ff-fa     estático
  255.255.255.255       ff-ff-ff-ff-ff-ff     estático

```

d) ¿Cómo se borra la tabla de caché de ARP ? compruébalo en tu equipo

```bash
arp -d *  # Elimina la caché de ARP (requiere modo administrador)
```

Resultado al volver a consultar la tabla caché:

```bash
C:\Windows\system32>arp -av

Interfaz: 127.0.0.1 --- 0x1
  Dirección de Internet          Dirección física      Tipo
  224.0.0.22                                  estático
  224.0.0.113                                 estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.113           01-00-5e-00-00-71     estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.113           01-00-5e-00-00-71     estático

Interfaz: 0.0.0.0 --- 0xffffffff
  Dirección de Internet          Dirección física      Tipo
  224.0.0.113           01-00-5e-00-00-71     estático

Interfaz: 192.168.0.106 --- 0x10
  Dirección de Internet          Dirección física      Tipo
  192.168.0.1           08-40-f3-ad-53-48     dinámico
  192.168.0.104         00-00-00-00-00-00     no válido
  192.168.0.105         00-00-00-00-00-00     no válido
  192.168.0.109         00-00-00-00-00-00     no válido
  192.168.2.1           00-00-00-00-00-00     no válido
  224.0.0.22            01-00-5e-00-00-16     estático
  224.0.0.113           01-00-5e-00-00-71     estático
```

# Comando TRACERT

Sirve para:

Rastrear la ruta que los paquetes de datos toman desde la computadora hasta un destino especificado. Esta herramienta es útil para identificar dónde se producen los problemas de red, ya que muestra cada salto que los paquetes toman en su camino al destino.

Responda lo siguiente:

a. ¿Para qué sirve tracert –d?

Traza la ruta sin obtener los hostnames de los routers intermedios, incrementando el rendimiento de tracert

```bash
C:\Windows\system32>tracert -d google.com

Traza a la dirección google.com [192.178.52.142]
sobre un máximo de 30 saltos:

  1     3 ms     3 ms     8 ms  192.168.0.1
  2    21 ms    11 ms     7 ms  13.0.0.1
  3    13 ms     8 ms     8 ms  187.188.171.226
  4    10 ms     9 ms     9 ms  10.180.49.7
  5     *        *        *     Tiempo de espera agotado para esta solicitud.
  6    22 ms    19 ms    23 ms  74.125.119.138
  7    19 ms    12 ms    12 ms  142.251.250.97
  8    15 ms    14 ms    13 ms  192.178.72.41
  9    12 ms    14 ms   103 ms  192.178.52.142

Traza completa.

```

b. ¿Para qué sirve tracert –w?

Establece un tiempo de espera en milisegundos por cada respuesta

```bash
C:\Windows\system32>tracert -w 500 google.com

Traza a la dirección google.com [192.178.52.142]
sobre un máximo de 30 saltos:

  1     8 ms    30 ms    12 ms  192.168.2.1
  2    61 ms     *       36 ms  192.168.1.254
  3    67 ms    67 ms    80 ms  dsl-servicio-l200.uninet.net.mx [200.38.193.226]
  4    64 ms     *       38 ms  reg-qro-triara-48-ae23_0.uninet.net.mx [201.154.113.110]
  5    39 ms    16 ms    58 ms  72.14.242.160
  6    98 ms    30 ms    16 ms  142.251.250.39
  7     *       21 ms    26 ms  192.178.72.43
  8    64 ms    49 ms    44 ms  tzqroa-aa-in-f14.1e100.net [192.178.52.142]

Traza completa.
```

2. Ejecute tracert www.google.com y anote el resultado

```bash
C:\Windows\system32>tracert google.com

Traza a la dirección google.com [142.251.218.142]
sobre un máximo de 30 saltos:

  1    26 ms    22 ms     4 ms  192.168.2.1
  2     *       33 ms    64 ms  192.168.1.254
  3     9 ms    26 ms     *     dsl-servicio-l200.uninet.net.mx [200.38.193.226]
  4     *      115 ms   194 ms  reg-qro-triara-48-ae23_0.uninet.net.mx [201.154.113.110]
  5    88 ms    48 ms    16 ms  ext-189-247-252-37.uninet.net.mx [189.247.252.37]
  6    52 ms    50 ms    32 ms  142.251.250.35
  7    28 ms    41 ms    67 ms  209.85.251.153
  8    55 ms    43 ms    63 ms  qro04s06-in-f14.1e100.net [142.251.218.142]

Traza completa.
```
