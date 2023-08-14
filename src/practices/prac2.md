# Practica 2

# Comandos Linux

## Comando ifconfig

- ¿Para que sirve el comando `ifconfig`?
    - Es utilizado para configurar, controlar y consultar interfaces de red TCP/IP.
    - Sus usos principales son visualizar la configuración de red, mostrar información sobre una interfaz especifica, asignar una dirección IP a una interfaz de red y habilitar o deshabilitar una interfaz de red.

- ¿Cual es su dirección IP?

Al ejecutar `ifconfig` obtengo lo siguiente:

```bash
wlx28ee521417b7: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::df03:83f7:3161:447b  prefixlen 64  scopeid 0x20<link>
        ether 28:ee:52:14:17:b7  txqueuelen 1000  (Ethernet)
        RX packets 14743  bytes 25445241 (25.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10427  bytes 1977549 (1.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

La linea que comienza con `inet` es la linea que contiene mi IP, en este caso es `192.168.0.100`.

- ¿Para que sirve el comando `ifconfig eth0 down`?

Sirve para deshabilitar una interfaz de red.

- ¿Con que parámetro se *activa* una interfaz de red?

`ifconfig eth0 up` para habilitarla una interfaz de red.

- Explique para qué sirve el parámetro `promisc` de `ifconfig`

Se utiliza para poner una interfaz de red en modo *promiscuo*. En este modo, la interfaz de red puede capturar todos los paquetes que pasan por la red. Esto es útil para el diagnostico de la red y para aplicaciones como los analizadores de paquetes.

## Interfaces

- Localice y describa el contenido del archivo `/etc/network/interfaces` para la interfaz `eth0`.

Contenido de `interfaces`

```bash
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    gateway 192.168.1.1
```

> eth0 tiene la palabra `static`, la dirección IP asignada es: `192.168.1.10`

## resolv.conf

```bash
nameserver 127.0.0.53
options edns0 trust-ad
search www.tendawifi.com
```

En mi caso, el archivo `resolv.conf` no tiene una linea `domain` porque mi sistema utiliza el programa `resolvconf` que genera dinámicamente el archivo `resolv.conf` y puede que no incluya la linea `domain`.

La linea `nameserver` indica la dirección IP del servidor DNS que el sistema consulta para la resolución de nombres de dominio, en mi caso indica `nameserver 127.0.0.53`.

<!-- #duda que es un DNS? -->
<!-- #duda para que sirve resolvconf? -->
<!-- #duda que es TCP/IP? -->

## Comando ping

Ejecute `ping www.google.com` y describa el resultado.

```bash
PING www.google.com (142.251.34.36) 56(84) bytes of data.
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=1 ttl=57 time=115 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=3 ttl=57 time=40.5 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=4 ttl=57 time=18.0 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=5 ttl=57 time=17.0 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=6 ttl=57 time=16.6 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=7 ttl=57 time=14.8 ms
64 bytes from qro01s28-in-f4.1e100.net (142.251.34.36): icmp_seq=8 ttl=57 time=21.5 ms
^C
--- www.google.com ping statistics ---
8 packets transmitted, 7 received, 12.5% packet loss, time 7024ms
rtt min/avg/max/mdev = 14.753/34.825/115.451/33.907 ms
```

`PING www.google.com (142.251.34.36) 56(84) bytes of data.` indica que se está enviando un ping a `www.google.com` que se resuelve en la ip `142.251.34.36`, se están enviando paquetes de 56 bytes cada uno.

Posteriormente obtengo respuestas de cada paquete enviado, por ejemplo:

```bash
64 bytes # Es el tamaño de la respuestas
from qro01s28-in-f4.1e100.net (142.251.34.36) # Es el servidor que responde
icmp_seq=1 # Es el numero de secuencia del paquete
ttl=57 # Es el tiempo de vida del paquete
time=115 ms # El tiempo que tardó en recibir la respuesta
```

Finalmente al detener la ejecución obtengo estadísticas como la cantidad de paquetes enviados, recibidos y perdidos y estadísticas adicionales sobre el tiempo de ida y vuelta mas corto, tiempo promedia y desviación media.

# Comando netstat

Ejecute netstat y describa el resultado

```bash
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 pop-os:49920            104.18.4.54:https       ESTABLISHED
tcp        0      0 pop-os:42632            209.100.149.34.bc:https ESTABLISHED
tcp        0      0 pop-os:52982            lb-140-82-112-6-i:https ESTABLISHED
tcp        0      0 pop-os:55350            123.208.120.34.bc:https ESTABLISHED
tcp        0      0 pop-os:43330            55.65.117.34.bc.g:https ESTABLISHED
tcp        0      0 pop-os:33064            qro01s28-in-f4.1e:https ESTABLISHED
tcp        0      0 pop-os:48338            qro04s06-in-f4.1e:https ESTABLISHED
tcp        0      0 pop-os:46766            192.229.211.108:http    ESTABLISHED
udp        0      0 pop-os:bootpc           _gateway:bootps         ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  3      [ ]         DGRAM      CONNECTED     22342    /run/systemd/notify
unix  2      [ ]         DGRAM                    22359    /run/systemd/journal/syslog
unix  17     [ ]         DGRAM      CONNECTED     22366    /run/systemd/journal/dev-log
unix  10     [ ]         DGRAM      CONNECTED     22368    /run/systemd/journal/socket
unix  2      [ ]         DGRAM                    38191    /run/user/1000/systemd/notify
unix  2      [ ]         DGRAM      CONNECTED     33402    /run/chrony/chronyd.sock
unix  2      [ ]         DGRAM                    32206    /run/wpa_supplicant/wlx28ee521417b7
unix  3      [ ]         STREAM     CONNECTED     57350    
unix  3      [ ]         STREAM     CONNECTED     41156    
unix  3      [ ]         STREAM     CONNECTED     33807    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     43031    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39723    
unix  3      [ ]         STREAM     CONNECTED     38531    
unix  3      [ ]         SEQPACKET  CONNECTED     56153    
unix  3      [ ]         STREAM     CONNECTED     52221    
unix  3      [ ]         STREAM     CONNECTED     41416    
unix  3      [ ]         STREAM     CONNECTED     40993    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM      CONNECTED     38251    
unix  3      [ ]         STREAM     CONNECTED     41355    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39711    
unix  3      [ ]         STREAM     CONNECTED     38828    
unix  3      [ ]         SEQPACKET  CONNECTED     54046    
unix  2      [ ]         STREAM     CONNECTED     54039    
unix  3      [ ]         STREAM     CONNECTED     40611    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     41157    
unix  3      [ ]         STREAM     CONNECTED     40985    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38628    
unix  3      [ ]         STREAM     CONNECTED     38248    
unix  3      [ ]         STREAM     CONNECTED     30717    
unix  3      [ ]         STREAM     CONNECTED     40903    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41375    
unix  3      [ ]         STREAM     CONNECTED     39488    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     42224    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38824    
unix  3      [ ]         DGRAM      CONNECTED     34983    
unix  2      [ ]         STREAM     CONNECTED     54058    
unix  3      [ ]         STREAM     CONNECTED     40559    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37538    
unix  3      [ ]         STREAM     CONNECTED     39720    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     38446    
unix  3      [ ]         STREAM     CONNECTED     38296    
unix  3      [ ]         STREAM     CONNECTED     33801    
unix  3      [ ]         STREAM     CONNECTED     56154    
unix  3      [ ]         STREAM     CONNECTED     43278    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     41667    
unix  3      [ ]         STREAM     CONNECTED     38832    
unix  3      [ ]         STREAM     CONNECTED     39519    
unix  3      [ ]         STREAM     CONNECTED     37537    
unix  3      [ ]         STREAM     CONNECTED     37384    /run/user/1000/bus
unix  2      [ ]         DGRAM                    40906    
unix  3      [ ]         STREAM     CONNECTED     42030    /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     41313    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     42504    
unix  3      [ ]         STREAM     CONNECTED     41438    
unix  3      [ ]         STREAM     CONNECTED     40965    /run/systemd/journal/stdout
unix  3      [ ]         DGRAM      CONNECTED     27436    
unix  3      [ ]         STREAM     CONNECTED     39684    
unix  3      [ ]         STREAM     CONNECTED     38833    
unix  3      [ ]         STREAM     CONNECTED     40680    
unix  3      [ ]         STREAM     CONNECTED     40606    
unix  3      [ ]         STREAM     CONNECTED     41119    
unix  3      [ ]         STREAM     CONNECTED     33804    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39733    
unix  3      [ ]         STREAM     CONNECTED     38575    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38478    
unix  3      [ ]         STREAM     CONNECTED     55612    
unix  3      [ ]         STREAM     CONNECTED     41593    
unix  3      [ ]         STREAM     CONNECTED     42308    
unix  3      [ ]         STREAM     CONNECTED     41241    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40528    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    38292    
unix  3      [ ]         STREAM     CONNECTED     39775    
unix  3      [ ]         STREAM     CONNECTED     57349    
unix  3      [ ]         STREAM     CONNECTED     40565    
unix  3      [ ]         STREAM     CONNECTED     39444    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31361    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39755    
unix  3      [ ]         STREAM     CONNECTED     42505    
unix  3      [ ]         STREAM     CONNECTED     39495    /run/user/1000/bus
unix  2      [ ]         DGRAM                    38295    
unix  3      [ ]         STREAM     CONNECTED     53781    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     40712    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    40677    
unix  3      [ ]         STREAM     CONNECTED     39681    
unix  2      [ ]         DGRAM                    41179    
unix  3      [ ]         STREAM     CONNECTED     38837    
unix  3      [ ]         STREAM     CONNECTED     40683    
unix  3      [ ]         STREAM     CONNECTED     40581    
unix  3      [ ]         STREAM     CONNECTED     38532    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     37501    
unix  3      [ ]         STREAM     CONNECTED     38868    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38290    
unix  3      [ ]         STREAM     CONNECTED     33803    
unix  3      [ ]         STREAM     CONNECTED     41296    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38825    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     42225    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41340    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     39503    
unix  3      [ ]         SEQPACKET  CONNECTED     57368    
unix  3      [ ]         STREAM     CONNECTED     40579    
unix  3      [ ]         STREAM     CONNECTED     37507    
unix  3      [ ]         STREAM     CONNECTED     37450    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38405    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM                    41357    
unix  3      [ ]         STREAM     CONNECTED     40561    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     56160    
unix  3      [ ]         STREAM     CONNECTED     41017    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM      CONNECTED     33797    
unix  3      [ ]         STREAM     CONNECTED     41869    
unix  2      [ ]         DGRAM      CONNECTED     40684    
unix  3      [ ]         STREAM     CONNECTED     38838    
unix  3      [ ]         DGRAM      CONNECTED     34984    
unix  3      [ ]         STREAM     CONNECTED     40609    
unix  3      [ ]         STREAM     CONNECTED     39046    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     31870    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38871    
unix  3      [ ]         STREAM     CONNECTED     39134    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41439    
unix  3      [ ]         STREAM     CONNECTED     41254    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40514    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41650    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39494    
unix  3      [ ]         STREAM     CONNECTED     32730    /run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     54047    
unix  3      [ ]         STREAM     CONNECTED     40608    
unix  3      [ ]         STREAM     CONNECTED     39081    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     32796    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39765    
unix  3      [ ]         STREAM     CONNECTED     40131    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38294    
unix  3      [ ]         STREAM     CONNECTED     42500    
unix  3      [ ]         STREAM     CONNECTED     41270    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39559    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41859    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     43109    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39491    
unix  3      [ ]         STREAM     CONNECTED     40540    
unix  3      [ ]         STREAM     CONNECTED     37601    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41223    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     39135    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38293    
unix  3      [ ]         STREAM     CONNECTED     33809    
unix  3      [ ]         STREAM     CONNECTED     39677    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     39557    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40719    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41376    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     39502    
unix  3      [ ]         SEQPACKET  CONNECTED     54075    
unix  3      [ ]         STREAM     CONNECTED     40610    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     38816    
unix  3      [ ]         STREAM     CONNECTED     40984    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38408    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40560    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33802    
unix  3      [ ]         STREAM     CONNECTED     41645    
unix  3      [ ]         STREAM     CONNECTED     42221    
unix  3      [ ]         STREAM     CONNECTED     41039    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     37172    
unix  3      [ ]         STREAM     CONNECTED     41867    
unix  3      [ ]         STREAM     CONNECTED     39487    
unix  3      [ ]         SEQPACKET  CONNECTED     54076    
unix  2      [ ]         DGRAM                    41857    
unix  3      [ ]         STREAM     CONNECTED     37379    /run/user/1000/bus
unix  2      [ ]         SEQPACKET  CONNECTED     88235    
unix  3      [ ]         STREAM     CONNECTED     39679    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     41120    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33812    
unix  3      [ ]         STREAM     CONNECTED     42107    
unix  3      [ ]         STREAM     CONNECTED     42160    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     39661    
unix  3      [ ]         STREAM     CONNECTED     38829    
unix  2      [ ]         DGRAM                    37500    
unix  3      [ ]         SEQPACKET  CONNECTED     57367    
unix  3      [ ]         STREAM     CONNECTED     41141    
unix  3      [ ]         STREAM     CONNECTED     37504    
unix  3      [ ]         STREAM     CONNECTED     90829    
unix  3      [ ]         STREAM     CONNECTED     41354    
unix  3      [ ]         STREAM     CONNECTED     41256    @/tmp/.X11-unix/X1
unix  3      [ ]         SEQPACKET  CONNECTED     56152    
unix  2      [ ]         STREAM     CONNECTED     56147    
unix  3      [ ]         STREAM     CONNECTED     41638    
unix  3      [ ]         STREAM     CONNECTED     42162    
unix  3      [ ]         STREAM     CONNECTED     40992    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39676    
unix  3      [ ]         STREAM     CONNECTED     38827    
unix  2      [ ]         STREAM     CONNECTED     57360    
unix  3      [ ]         STREAM     CONNECTED     42073    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40681    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     41234    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     40972    
unix  3      [ ]         STREAM     CONNECTED     39127    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38368    
unix  3      [ ]         STREAM     CONNECTED     55613    
unix  3      [ ]         STREAM     CONNECTED     40616    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     40517    /run/user/1000/bus
unix  3      [ ]         DGRAM      CONNECTED     27435    
unix  3      [ ]         STREAM     CONNECTED     42498    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39928    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     39675    
unix  3      [ ]         STREAM     CONNECTED     41337    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41140    
unix  3      [ ]         STREAM     CONNECTED     37477    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39043    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38842    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39102    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     30719    
unix  3      [ ]         STREAM     CONNECTED     40898    
unix  3      [ ]         STREAM     CONNECTED     42503    
unix  3      [ ]         STREAM     CONNECTED     38883    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40527    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     90830    
unix  3      [ ]         STREAM     CONNECTED     40731    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41293    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40386    
unix  3      [ ]         STREAM     CONNECTED     41872    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     37682    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39108    
unix  3      [ ]         STREAM     CONNECTED     38461    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33954    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     32791    
unix  2      [ ]         DGRAM      CONNECTED     27431    
unix  3      [ ]         STREAM     CONNECTED     53815    
unix  3      [ ]         STREAM     CONNECTED     41866    
unix  3      [ ]         STREAM     CONNECTED     41044    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39123    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38835    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     37808    
unix  3      [ ]         STREAM     CONNECTED     37967    
unix  3      [ ]         STREAM     CONNECTED     31856    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42080    
unix  3      [ ]         STREAM     CONNECTED     38807    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39122    
unix  3      [ ]         STREAM     CONNECTED     33806    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38874    
unix  3      [ ]         STREAM     CONNECTED     40475    
unix  3      [ ]         STREAM     CONNECTED     38778    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40099    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     32707    
unix  3      [ ]         STREAM     CONNECTED     34582    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27422    
unix  3      [ ]         STREAM     CONNECTED     72699    
unix  3      [ ]         SEQPACKET  CONNECTED     52870    
unix  3      [ ]         STREAM     CONNECTED     41036    
unix  3      [ ]         STREAM     CONNECTED     41282    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40424    
unix  3      [ ]         STREAM     CONNECTED     32842    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39458    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40293    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39131    
unix  3      [ ]         STREAM     CONNECTED     41295    
unix  3      [ ]         STREAM     CONNECTED     41048    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38821    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38918    
unix  3      [ ]         STREAM     CONNECTED     40502    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39467    
unix  3      [ ]         STREAM     CONNECTED     40264    
unix  3      [ ]         STREAM     CONNECTED     36845    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     32272    
unix  2      [ ]         DGRAM                    32926    
unix  3      [ ]         STREAM     CONNECTED     32847    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     54754    
unix  3      [ ]         STREAM     CONNECTED     42035    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     37804    
unix  3      [ ]         STREAM     CONNECTED     40421    
unix  3      [ ]         STREAM     CONNECTED     37441    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39050    
unix  3      [ ]         STREAM     CONNECTED     42532    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41290    
unix  2      [ ]         DGRAM      CONNECTED     32788    
unix  3      [ ]         STREAM     CONNECTED     41041    
unix  3      [ ]         STREAM     CONNECTED     39483    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39474    
unix  2      [ ]         STREAM                   40068    
unix  3      [ ]         STREAM     CONNECTED     32344    
unix  3      [ ]         STREAM     CONNECTED     31413    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38789    
unix  3      [ ]         STREAM     CONNECTED     40378    
unix  3      [ ]         STREAM     CONNECTED     31865    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42033    
unix  3      [ ]         STREAM     CONNECTED     40409    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39080    
unix  3      [ ]         STREAM     CONNECTED     32086    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     32931    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61083    
unix  3      [ ]         STREAM     CONNECTED     39085    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39049    
unix  3      [ ]         STREAM     CONNECTED     38875    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     41054    
unix  3      [ ]         STREAM     CONNECTED     40493    @/tmp/.ICE-unix/2099
unix  3      [ ]         STREAM     CONNECTED     39407    
unix  3      [ ]         STREAM     CONNECTED     38784    
unix  3      [ ]         STREAM     CONNECTED     38361    
unix  3      [ ]         STREAM     CONNECTED     42034    
unix  3      [ ]         STREAM     CONNECTED     40415    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     37777    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39072    
unix  2      [ ]         DGRAM      CONNECTED     38924    
unix  3      [ ]         STREAM     CONNECTED     32732    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40520    
unix  3      [ ]         STREAM     CONNECTED     38808    /run/user/1000/at-spi/bus_1
unix  2      [ ]         DGRAM      CONNECTED     28283    
unix  3      [ ]         SEQPACKET  CONNECTED     90899    
unix  3      [ ]         SEQPACKET  CONNECTED     90645    
unix  2      [ ]         STREAM     CONNECTED     72508    
unix  3      [ ]         STREAM     CONNECTED     40557    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41045    
unix  3      [ ]         STREAM     CONNECTED     32349    
unix  3      [ ]         DGRAM      CONNECTED     22344    
unix  3      [ ]         STREAM     CONNECTED     42099    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     37681    
unix  2      [ ]         STREAM     CONNECTED     37153    
unix  3      [ ]         STREAM     CONNECTED     41311    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39383    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39301    
unix  3      [ ]         STREAM     CONNECTED     28115    
unix  3      [ ]         STREAM     CONNECTED     87754    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     34515    /run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     90898    
unix  3      [ ]         STREAM     CONNECTED     40901    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     41013    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41005    
unix  3      [ ]         STREAM     CONNECTED     40417    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40095    
unix  3      [ ]         STREAM     CONNECTED     27525    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38792    
unix  3      [ ]         STREAM     CONNECTED     37662    
unix  3      [ ]         STREAM     CONNECTED     38514    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     32930    
unix  3      [ ]         STREAM     CONNECTED     42042    
unix  3      [ ]         STREAM     CONNECTED     38745    @/tmp/.X11-unix/X1
unix  2      [ ]         DGRAM      CONNECTED     33831    
unix  2      [ ]         STREAM     CONNECTED     38910    
unix  3      [ ]         STREAM     CONNECTED     37595    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     63943    /run/user/1000/pipewire-0
unix  3      [ ]         SEQPACKET  CONNECTED     52873    
unix  3      [ ]         STREAM     CONNECTED     41030    
unix  3      [ ]         STREAM     CONNECTED     39449    
unix  3      [ ]         STREAM     CONNECTED     40428    /run/user/1000/bus
unix  2      [ ]         STREAM     CONNECTED     37896    @/tmp/dbus-j8IH3QG4
unix  3      [ ]         STREAM     CONNECTED     54755    
unix  3      [ ]         STREAM     CONNECTED     37779    
unix  3      [ ]         STREAM     CONNECTED     37483    
unix  3      [ ]         STREAM     CONNECTED     39051    /run/user/1000/bus
unix  2      [ ]         DGRAM      CONNECTED     32347    
unix  3      [ ]         STREAM     CONNECTED     42010    
unix  3      [ ]         STREAM     CONNECTED     38771    /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     32837    
unix  3      [ ]         STREAM     CONNECTED     40529    
unix  3      [ ]         STREAM     CONNECTED     38803    @touchegg
unix  3      [ ]         STREAM     CONNECTED     42529    
unix  3      [ ]         STREAM     CONNECTED     42015    @touchegg
unix  3      [ ]         STREAM     CONNECTED     41073    
unix  3      [ ]         STREAM     CONNECTED     41009    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37807    
unix  3      [ ]         STREAM     CONNECTED     38757    
unix  3      [ ]         STREAM     CONNECTED     39132    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     31860    
unix  3      [ ]         STREAM     CONNECTED     42009    
unix  3      [ ]         STREAM     CONNECTED     40501    
unix  3      [ ]         STREAM     CONNECTED     39468    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     37795    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37229    
unix  3      [ ]         STREAM     CONNECTED     35371    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33840    
unix  2      [ ]         DGRAM      CONNECTED     32809    
unix  3      [ ]         STREAM     CONNECTED     41228    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     41051    
unix  3      [ ]         STREAM     CONNECTED     37209    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41335    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40418    
unix  3      [ ]         STREAM     CONNECTED     31901    
unix  3      [ ]         STREAM     CONNECTED     40402    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37766    @/tmp/.X11-unix/X1
unix  2      [ ]         DGRAM      CONNECTED     34693    
unix  3      [ ]         STREAM     CONNECTED     38880    
unix  3      [ ]         STREAM     CONNECTED     41033    /run/systemd/journal/stdout
unix  2      [ ]         DGRAM      CONNECTED     39302    
unix  3      [ ]         STREAM     CONNECTED     72700    
unix  3      [ ]         SEQPACKET  CONNECTED     52871    
unix  3      [ ]         STREAM     CONNECTED     39486    
unix  3      [ ]         STREAM     CONNECTED     37875    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40076    
unix  3      [ ]         STREAM     CONNECTED     36442    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     62337    
unix  3      [ ]         STREAM     CONNECTED     41871    
unix  3      [ ]         STREAM     CONNECTED     41258    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39111    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33327    
unix  3      [ ]         STREAM     CONNECTED     29811    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     38774    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39389    /run/dbus/system_bus_socket
unix  2      [ ]         DGRAM      CONNECTED     38702    
unix  3      [ ]         STREAM     CONNECTED     33370    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     61081    
unix  3      [ ]         STREAM     CONNECTED     57373    
unix  3      [ ]         STREAM     CONNECTED     41037    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40476    
unix  3      [ ]         SEQPACKET  CONNECTED     90646    
unix  2      [ ]         STREAM     CONNECTED     90638    
unix  3      [ ]         STREAM     CONNECTED     38884    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40094    
unix  3      [ ]         STREAM     CONNECTED     39730    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     40414    
unix  3      [ ]         STREAM     CONNECTED     37776    
unix  3      [ ]         STREAM     CONNECTED     38447    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     32844    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31847    
unix  3      [ ]         STREAM     CONNECTED     64650    /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     40472    /run/user/1000/bus
unix  2      [ ]         DGRAM      CONNECTED     1953     
unix  3      [ ]         STREAM     CONNECTED     61084    
unix  3      [ ]         STREAM     CONNECTED     38881    
unix  3      [ ]         STREAM     CONNECTED     41008    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40427    
unix  3      [ ]         STREAM     CONNECTED     37789    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     91351    
unix  3      [ ]         SEQPACKET  CONNECTED     52874    
unix  3      [ ]         STREAM     CONNECTED     40098    
unix  3      [ ]         STREAM     CONNECTED     35925    
unix  2      [ ]         DGRAM                    41339    
unix  3      [ ]         STREAM     CONNECTED     41310    
unix  3      [ ]         STREAM     CONNECTED     37773    
unix  3      [ ]         STREAM     CONNECTED     40381    
unix  3      [ ]         STREAM     CONNECTED     40271    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     31572    
unix  3      [ ]         STREAM     CONNECTED     42098    
unix  3      [ ]         STREAM     CONNECTED     32779    
unix  3      [ ]         STREAM     CONNECTED     33805    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40500    
unix  3      [ ]         STREAM     CONNECTED     38498    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     33851    
unix  3      [ ]         STREAM     CONNECTED     40526    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37457    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     42003    
unix  3      [ ]         STREAM     CONNECTED     39450    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39434    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40419    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     64651    
unix  3      [ ]         STREAM     CONNECTED     39556    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40496    
unix  3      [ ]         DGRAM      CONNECTED     38193    
unix  3      [ ]         STREAM     CONNECTED     34697    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33833    
unix  3      [ ]         STREAM     CONNECTED     39709    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39485    
unix  3      [ ]         STREAM     CONNECTED     40072    
unix  3      [ ]         STREAM     CONNECTED     37386    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41315    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38804    
unix  3      [ ]         STREAM     CONNECTED     32085    
unix  3      [ ]         STREAM     CONNECTED     39598    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39303    
unix  3      [ ]         STREAM     CONNECTED     32843    
unix  3      [ ]         STREAM     CONNECTED     31904    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     61082    
unix  3      [ ]         STREAM     CONNECTED     57372    
unix  3      [ ]         STREAM     CONNECTED     38876    
unix  3      [ ]         STREAM     CONNECTED     40523    
unix  3      [ ]         STREAM     CONNECTED     39553    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40492    
unix  3      [ ]         STREAM     CONNECTED     37879    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     38520    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42535    
unix  2      [ ]         DGRAM                    40376    
unix  2      [ ]         DGRAM      CONNECTED     37735    
unix  3      [ ]         DGRAM      CONNECTED     22343    
unix  3      [ ]         STREAM     CONNECTED     41279    
unix  3      [ ]         STREAM     CONNECTED     41074    
unix  3      [ ]         STREAM     CONNECTED     40031    
unix  3      [ ]         STREAM     CONNECTED     31481    
unix  3      [ ]         STREAM     CONNECTED     53814    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     42522    
unix  3      [ ]         STREAM     CONNECTED     40676    
unix  3      [ ]         STREAM     CONNECTED     39077    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33975    
unix  3      [ ]         SEQPACKET  CONNECTED     57169    
unix  3      [ ]         STREAM     CONNECTED     53087    
unix  3      [ ]         STREAM     CONNECTED     38492    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     35335    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     53816    
unix  3      [ ]         STREAM     CONNECTED     34987    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31471    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41082    
unix  3      [ ]         STREAM     CONNECTED     40038    
unix  3      [ ]         STREAM     CONNECTED     52866    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     53790    
unix  3      [ ]         STREAM     CONNECTED     37302    
unix  3      [ ]         STREAM     CONNECTED     33968    
unix  3      [ ]         STREAM     CONNECTED     42523    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     42198    /tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     37467    
unix  3      [ ]         STREAM     CONNECTED     31374    
unix  3      [ ]         STREAM     CONNECTED     37454    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     41083    
unix  2      [ ]         DGRAM      CONNECTED     33896    
unix  3      [ ]         STREAM     CONNECTED     31473    
unix  2      [ ]         SEQPACKET  CONNECTED     90423    
unix  3      [ ]         STREAM     CONNECTED     53796    
unix  3      [ ]         STREAM     CONNECTED     40620    
unix  3      [ ]         STREAM     CONNECTED     38392    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     31998    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33983    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31387    
unix  3      [ ]         STREAM     CONNECTED     41231    
unix  3      [ ]         STREAM     CONNECTED     38417    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33859    /run/dbus/system_bus_socket
unix  2      [ ]         SEQPACKET  CONNECTED     85578    
unix  3      [ ]         STREAM     CONNECTED     41084    
unix  2      [ ]         SEQPACKET  CONNECTED     84329    
unix  3      [ ]         STREAM     CONNECTED     32790    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40737    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39795    
unix  3      [ ]         STREAM     CONNECTED     37466    
unix  3      [ ]         STREAM     CONNECTED     38404    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39987    /run/dbus/system_bus_socket
unix  2      [ ]         DGRAM      CONNECTED     34006    
unix  3      [ ]         STREAM     CONNECTED     33978    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     90866    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     41245    
unix  3      [ ]         STREAM     CONNECTED     38401    /run/user/1000/bus
unix  2      [ ]         DGRAM      CONNECTED     31513    
unix  3      [ ]         STREAM     CONNECTED     31421    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41092    
unix  2      [ ]         DGRAM      CONNECTED     33934    
unix  3      [ ]         STREAM     CONNECTED     53786    
unix  3      [ ]         STREAM     CONNECTED     40619    
unix  2      [ ]         STREAM     CONNECTED     37171    
unix  3      [ ]         STREAM     CONNECTED     31940    
unix  3      [ ]         STREAM     CONNECTED     39836    
unix  3      [ ]         STREAM     CONNECTED     39399    
unix  3      [ ]         STREAM     CONNECTED     41240    
unix  3      [ ]         STREAM     CONNECTED     40003    
unix  3      [ ]         STREAM     CONNECTED     41088    
unix  3      [ ]         STREAM     CONNECTED     40050    
unix  2      [ ]         DGRAM      CONNECTED     37239    
unix  2      [ ]         DGRAM                    33955    
unix  3      [ ]         STREAM     CONNECTED     31438    
unix  3      [ ]         STREAM     CONNECTED     40615    
unix  3      [ ]         STREAM     CONNECTED     38196    
unix  3      [ ]         SEQPACKET  CONNECTED     52883    
unix  3      [ ]         STREAM     CONNECTED     54459    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39833    
unix  3      [ ]         STREAM     CONNECTED     37455    
unix  3      [ ]         STREAM     CONNECTED     40512    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     31879    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41252    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     87454    
unix  3      [ ]         STREAM     CONNECTED     57181    
unix  3      [ ]         STREAM     CONNECTED     52840    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     37465    
unix  3      [ ]         STREAM     CONNECTED     32912    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     31414    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31391    
unix  3      [ ]         STREAM     CONNECTED     41333    
unix  3      [ ]         STREAM     CONNECTED     40515    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     32882    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40059    
unix  3      [ ]         STREAM     CONNECTED     37380    
unix  2      [ ]         STREAM     CONNECTED     87479    
unix  3      [ ]         STREAM     CONNECTED     40640    
unix  3      [ ]         SEQPACKET  CONNECTED     33404    
unix  3      [ ]         STREAM     CONNECTED     33852    
unix  2      [ ]         STREAM     CONNECTED     52876    
unix  3      [ ]         STREAM     CONNECTED     54505    
unix  3      [ ]         STREAM     CONNECTED     54464    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     37383    
unix  3      [ ]         STREAM     CONNECTED     34053    /run/dbus/system_bus_socket
unix  2      [ ]         DGRAM      CONNECTED     22676    
unix  3      [ ]         STREAM     CONNECTED     39561    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     42519    
unix  3      [ ]         STREAM     CONNECTED     41232    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     31459    
unix  3      [ ]         STREAM     CONNECTED     56155    
unix  3      [ ]         STREAM     CONNECTED     40629    
unix  3      [ ]         STREAM     CONNECTED     40624    @/tmp/.X11-unix/X1
unix  3      [ ]         SEQPACKET  CONNECTED     57170    
unix  3      [ ]         STREAM     CONNECTED     40733    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     37462    
unix  3      [ ]         STREAM     CONNECTED     38236    
unix  3      [ ]         STREAM     CONNECTED     38400    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33864    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     40516    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41677    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     40056    
unix  3      [ ]         STREAM     CONNECTED     31470    
unix  3      [ ]         STREAM     CONNECTED     87455    
unix  2      [ ]         SEQPACKET  CONNECTED     84120    
unix  3      [ ]         STREAM     CONNECTED     42541    
unix  3      [ ]         STREAM     CONNECTED     40621    
unix  3      [ ]         STREAM     CONNECTED     37284    
unix  3      [ ]         STREAM     CONNECTED     33376    
unix  3      [ ]         STREAM     CONNECTED     31853    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37456    
unix  3      [ ]         STREAM     CONNECTED     31509    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39615    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     38415    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     32840    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41249    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     87490    
unix  3      [ ]         STREAM     CONNECTED     53783    
unix  3      [ ]         STREAM     CONNECTED     39041    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     32009    
unix  3      [ ]         STREAM     CONNECTED     33622    
unix  3      [ ]         STREAM     CONNECTED     54602    
unix  3      [ ]         STREAM     CONNECTED     42268    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38820    
unix  3      [ ]         STREAM     CONNECTED     33969    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39560    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     37405    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     32910    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41280    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33762    
unix  3      [ ]         STREAM     CONNECTED     34169    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     38460    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33907    
unix  3      [ ]         STREAM     CONNECTED     53088    
unix  3      [ ]         STREAM     CONNECTED     54506    
unix  3      [ ]         STREAM     CONNECTED     53787    @/tmp/.ICE-unix/2099
unix  3      [ ]         STREAM     CONNECTED     38406    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     34084    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41093    @/tmp/.X11-unix/X1
unix  2      [ ]         DGRAM                    37382    
unix  3      [ ]         STREAM     CONNECTED     39040    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41246    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     40004    
unix  3      [ ]         STREAM     CONNECTED     33985    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     31415    
unix  3      [ ]         STREAM     CONNECTED     53777    
unix  3      [ ]         SEQPACKET  CONNECTED     33403    
unix  3      [ ]         STREAM     CONNECTED     31918    
unix  3      [ ]         STREAM     CONNECTED     39837    
unix  3      [ ]         STREAM     CONNECTED     33377    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41251    
unix  3      [ ]         STREAM     CONNECTED     38416    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41098    
unix  3      [ ]         STREAM     CONNECTED     33984    
unix  2      [ ]         DGRAM      CONNECTED     33960    
unix  3      [ ]         STREAM     CONNECTED     37487    
unix  3      [ ]         STREAM     CONNECTED     38439    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     34856    
unix  3      [ ]         STREAM     CONNECTED     57182    
unix  3      [ ]         STREAM     CONNECTED     41679    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     42165    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40721    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     41089    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     34168    
unix  3      [ ]         STREAM     CONNECTED     41243    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     31437    
unix  3      [ ]         STREAM     CONNECTED     56159    
unix  3      [ ]         STREAM     CONNECTED     42525    
unix  3      [ ]         STREAM     CONNECTED     39834    /run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     37768    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33863    
unix  3      [ ]         SEQPACKET  CONNECTED     52884    
unix  3      [ ]         STREAM     CONNECTED     53791    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41323    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     41676    
unix  3      [ ]         STREAM     CONNECTED     41248    
unix  2      [ ]         DGRAM                    52374    
unix  3      [ ]         STREAM     CONNECTED     41097    
unix  3      [ ]         STREAM     CONNECTED     40014    
unix  3      [ ]         STREAM     CONNECTED     31420    
unix  3      [ ]         STREAM     CONNECTED     38393    /run/user/1000/pipewire-0
unix  3      [ ]         STREAM     CONNECTED     39990    
unix  3      [ ]         STREAM     CONNECTED     33922    
unix  3      [ ]         STREAM     CONNECTED     54601    
unix  3      [ ]         STREAM     CONNECTED     42133    /run/user/1000/bus
unix  2      [ ]         DGRAM      CONNECTED     38160    
unix  3      [ ]         STREAM     CONNECTED     41101    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39388    
unix  3      [ ]         STREAM     CONNECTED     73926    
unix  3      [ ]         DGRAM      CONNECTED     38192    
unix  3      [ ]         STREAM     CONNECTED     90044    
unix  3      [ ]         STREAM     CONNECTED     39622    
unix  3      [ ]         SEQPACKET  CONNECTED     70477    
unix  3      [ ]         STREAM     CONNECTED     41103    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39332    
unix  3      [ ]         STREAM     CONNECTED     40736    
unix  3      [ ]         STREAM     CONNECTED     35926    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     89840    
unix  3      [ ]         STREAM     CONNECTED     39628    
unix  3      [ ]         STREAM     CONNECTED     41106    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39371    
unix  3      [ ]         STREAM     CONNECTED     35331    
unix  2      [ ]         STREAM     CONNECTED     88858    
unix  3      [ ]         STREAM     CONNECTED     41095    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     91139    
unix  3      [ ]         STREAM     CONNECTED     54998    
unix  3      [ ]         STREAM     CONNECTED     40741    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     41108    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39321    
unix  3      [ ]         STREAM     CONNECTED     39629    
unix  3      [ ]         STREAM     CONNECTED     36822    
unix  3      [ ]         STREAM     CONNECTED     33662    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     39305    
unix  3      [ ]         STREAM     CONNECTED     41114    
unix  3      [ ]         STREAM     CONNECTED     34171    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     34523    
unix  3      [ ]         STREAM     CONNECTED     41113    
unix  3      [ ]         STREAM     CONNECTED     38738    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     39758    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     38917    /run/systemd/journal/stdout
unix  3      [ ]         SEQPACKET  CONNECTED     89848    
unix  3      [ ]         STREAM     CONNECTED     39393    
unix  3      [ ]         STREAM     CONNECTED     41100    
unix  3      [ ]         STREAM     CONNECTED     88866    
unix  3      [ ]         STREAM     CONNECTED     40543    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     37208    @/tmp/dbus-Cv0vs1px
unix  3      [ ]         STREAM     CONNECTED     42533    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     41105    
unix  3      [ ]         STREAM     CONNECTED     40382    /run/user/1000/at-spi/bus_1
unix  3      [ ]         STREAM     CONNECTED     88867    
unix  3      [ ]         STREAM     CONNECTED     89839    
unix  3      [ ]         STREAM     CONNECTED     39605    
unix  3      [ ]         STREAM     CONNECTED     54997    
unix  3      [ ]         STREAM     CONNECTED     41665    @/tmp/.X11-unix/X1
unix  3      [ ]         STREAM     CONNECTED     40325    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     33661    
unix  3      [ ]         SEQPACKET  CONNECTED     89847    
unix  3      [ ]         STREAM     CONNECTED     36823    
unix  3      [ ]         STREAM     CONNECTED     39382    
unix  3      [ ]         STREAM     CONNECTED     36085    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     34522    
unix  3      [ ]         STREAM     CONNECTED     41107    
unix  3      [ ]         STREAM     CONNECTED     40549    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     33666    
unix  3      [ ]         STREAM     CONNECTED     41139    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  3      [ ]         STREAM     CONNECTED     39333    
unix  3      [ ]         STREAM     CONNECTED     40740    
unix  3      [ ]         STREAM     CONNECTED     90043    
unix  3      [ ]         STREAM     CONNECTED     39547    
unix  3      [ ]         STREAM     CONNECTED     34518    
unix  3      [ ]         STREAM     CONNECTED     41102    
unix  3      [ ]         STREAM     CONNECTED     37728    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     88793    
unix  3      [ ]         STREAM     CONNECTED     40547    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     41115    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     73927    
unix  3      [ ]         STREAM     CONNECTED     39306    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     88792    
unix  3      [ ]         STREAM     CONNECTED     38916    /run/systemd/journal/stdout
unix  3      [ ]         STREAM     CONNECTED     40545    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     40379    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     35334    
unix  2      [ ]         STREAM     CONNECTED     88791    
unix  3      [ ]         STREAM     CONNECTED     39548    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     91140    
unix  3      [ ]         SEQPACKET  CONNECTED     70476    
unix  3      [ ]         STREAM     CONNECTED     40552    /run/user/1000/bus
unix  3      [ ]         STREAM     CONNECTED     39304    
unix  3      [ ]         STREAM     CONNECTED     33713    
unix  3      [ ]         STREAM     CONNECTED     36821    
unix  3      [ ]         STREAM     CONNECTED     40723    
unix  3      [ ]         STREAM     CONNECTED     41118    
unix  3      [ ]         STREAM     CONNECTED     40330    /run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     33667    /run/dbus/system_bus_socket
```

`netstat` permite identificar las conexiones activas en la máquina en la que se ejecuta el comando creando una lista con todos los puertos TCP y UDP que estén abiertos en la computadora, también permite obtener estadísticas de otros protocolos.

<!-- #duda que es UDP? -->
<!-- #duda que quiere decir "estado de escucha"? -->

- ¿Para que sirve la opción `-l`?

Se utiliza para listar todas las conexiones de red en estado de escucha en el sistema, incluye tanto TCP como UDP.

```bash
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:domain        0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:cbtd            0.0.0.0:*               LISTEN     
tcp        0      0 localhost:ipp           0.0.0.0:*               LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                          
udp        0      0 localhost:domain        0.0.0.0:*                          
udp        0      0 localhost:323           0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*                          
udp        0      0 0.0.0.0:59366           0.0.0.0:*                          
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 localhost:323           [::]:*                             
udp6       0      0 [::]:57954              [::]:*                             
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     22345    /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     22347    /run/systemd/userdb/io.systemd.DynamicUser
unix  2      [ ACC ]     STREAM     LISTENING     22348    /run/systemd/io.system.ManagedOOM
unix  2      [ ACC ]     STREAM     LISTENING     38692    @/tmp/.ICE-unix/2099
unix  2      [ ACC ]     STREAM     LISTENING     22357    /run/lvm/lvmpolld.socket
unix  2      [ ACC ]     STREAM     LISTENING     22370    /run/systemd/journal/stdout
unix  2      [ ACC ]     SEQPACKET  LISTENING     22372    /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     33633    @touchegg
unix  2      [ ACC ]     STREAM     LISTENING     41110    @/home/miguehm/.cache/ibus/dbus-AoIEWIjL
unix  2      [ ACC ]     STREAM     LISTENING     40069    @/tmp/.X11-unix/X1
unix  2      [ ACC ]     STREAM     LISTENING     1951     /run/systemd/journal/io.systemd.journal
unix  2      [ ACC ]     STREAM     LISTENING     38194    /run/user/1000/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     38200    /run/user/1000/bus
unix  2      [ ACC ]     STREAM     LISTENING     38202    /run/user/1000/gnupg/S.dirmngr
unix  2      [ ACC ]     STREAM     LISTENING     38204    /run/user/1000/gnupg/S.gpg-agent.browser
unix  2      [ ACC ]     STREAM     LISTENING     38206    /run/user/1000/gnupg/S.gpg-agent.extra
unix  2      [ ACC ]     STREAM     LISTENING     38208    /run/user/1000/gnupg/S.gpg-agent.ssh
unix  2      [ ACC ]     STREAM     LISTENING     38210    /run/user/1000/gnupg/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     38212    /run/user/1000/pulse/native
unix  2      [ ACC ]     STREAM     LISTENING     38214    /run/user/1000/pipewire-0
unix  2      [ ACC ]     STREAM     LISTENING     34060    @/tmp/dbus-j8IH3QG4
unix  2      [ ACC ]     STREAM     LISTENING     38216    /run/user/1000/pk-debconf-socket
unix  2      [ ACC ]     STREAM     LISTENING     38218    /run/user/1000/snapd-session-agent.socket
unix  2      [ ACC ]     STREAM     LISTENING     40037    /run/user/1000/keyring/control
unix  2      [ ACC ]     STREAM     LISTENING     28301    /run/systemd/resolve/io.systemd.Resolve
unix  2      [ ACC ]     STREAM     LISTENING     40274    /run/user/1000/at-spi/bus_1
unix  2      [ ACC ]     STREAM     LISTENING     38666    /run/user/1000/keyring/ssh
unix  2      [ ACC ]     STREAM     LISTENING     40306    /run/user/1000/keyring/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     34059    @/tmp/dbus-Cv0vs1px
unix  2      [ ACC ]     STREAM     LISTENING     40070    /tmp/.X11-unix/X1
unix  2      [ ACC ]     STREAM     LISTENING     38693    /tmp/.ICE-unix/2099
unix  2      [ ACC ]     STREAM     LISTENING     53302    /run/user/1000/keyring/.ssh
unix  2      [ ACC ]     STREAM     LISTENING     61906    /run/user/1000/nvim.5903.0
unix  2      [ ACC ]     STREAM     LISTENING     31347    /run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     31349    /run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     31351    /run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     31353    /run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     31355    /run/snapd.socket
unix  2      [ ACC ]     STREAM     LISTENING     31357    /run/snapd-snap.socket
unix  2      [ ACC ]     STREAM     LISTENING     31359    /run/uuidd/request
unix  2      [ ACC ]     STREAM     LISTENING     35960    /var/snap/cups/common/run/cups.sock
```

- ¿Para que sirve la opción `-c`?

Se utiliza para actualizar y mostrar la información de `netstat` en tiempo real.

## Comando traceroute

Ejecute `traceroute www.google.com` y describa el resultado.

```bash
traceroute to www.google.com (142.251.34.36), 30 hops max, 60 byte packets
 1  _gateway (192.168.0.1)  8.865 ms  9.875 ms  9.860 ms
 2  13.0.0.1 (13.0.0.1)  14.591 ms  19.010 ms  19.000 ms
 3  fixed-187-188-171-226.totalplay.net (187.188.171.226)  32.544 ms  33.634 ms  33.617 ms
 4  * 10.180.49.7 (10.180.49.7)  20.572 ms *
 5  10.180.49.6 (10.180.49.6)  20.537 ms *  21.973 ms
 6  74.125.119.138 (74.125.119.138)  25.753 ms  40.183 ms  40.510 ms
 7  * * *
 8  192.178.72.68 (192.178.72.68)  42.488 ms 74.125.243.33 (74.125.243.33)  40.398 ms qro01s28-in-f4.1e100.net (142.251.34.36)  40.369 ms
```

Nos muestra la dirección y la ip a la cual haremos el trazado de ruta. También especifica que se permiten hasta 30 saltos en el rastreo y que se están enviando paquetes de 60 bytes.

Posteriormente obtengo una numeración de todos los saltos que realizó para llegar a la IP destino.

## Comando tcpdump

- Ejecute `tcpdump` y describa el resultado.

El comando `tcpdump` es una herramienta de linea de comandos utilizada para analizar el tráfico de red en tiempo real, el usuario puede capturar y mostarar los paquetes transmitidos y recibidos por la red a la que está conectado.

```bash
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on wlx28ee521417b7, link-type EN10MB (Ethernet), snapshot length 262144 bytes
09:01:25.026701 IP 192.168.0.104.8001 > st-routers.mcast.net.8001: UDP, length 200
09:01:25.078664 IP pop-os.58726 > _gateway.domain: 3369+ PTR? 104.0.168.192.in-addr.arpa. (44)
09:01:25.192340 IP _gateway.domain > pop-os.58726: 3369 NXDomain 0/0/0 (44)
09:01:25.193313 IP pop-os.44053 > _gateway.domain: 56195+ PTR? 1.0.168.192.in-addr.arpa. (42)
09:01:25.825220 ARP, Request who-has _gateway tell pop-os, length 28
09:01:25.828278 ARP, Reply _gateway is-at 08:40:f3:ad:53:48 (oui Unknown), length 28
09:01:25.846680 IP 192.168.0.104.56991 > 192.168.0.255.15600: UDP, length 35
09:01:26.972323 IP 192.168.0.104.8001 > st-routers.mcast.net.8001: UDP, length 200
09:01:28.815600 IP 192.168.0.104.48243 > 239.255.255.250.15600: UDP, length 35
09:01:29.019956 IP 192.168.0.104.8001 > st-routers.mcast.net.8001: UDP, length 200
09:01:30.216990 IP pop-os.44053 > _gateway.domain: 56195+ PTR? 1.0.168.192.in-addr.arpa. (42)
09:01:30.334424 IP _gateway.domain > pop-os.44053: 56195 NXDomain 0/0/0 (42)
09:01:30.335324 IP pop-os.41749 > _gateway.domain: 42515+ PTR? 106.0.168.192.in-addr.arpa. (44)
09:01:30.455095 IP pop-os.55124 > _gateway.domain: 25818+ PTR? 255.0.168.192.in-addr.arpa. (44)
09:01:30.965557 IP 192.168.0.104.8001 > st-routers.mcast.net.8001: UDP, length 200
09:01:35.656141 IP pop-os.40692 > _gateway.domain: 10912+ PTR? 250.255.255.239.in-addr.arpa. (46)
09:01:36.260857 IP _gateway.domain > pop-os.40692: 10912 NXDomain 0/1/0 (103)
^C09:01:36.688913 IP pop-os.44324 > virginia.time.system76.com.ntp: NTPv4, Client, length 228

18 packets captured
153 packets received by filter
131 packets dropped by kernel
```

Nos muestra la interfaz de red en lo que se está realizando la captura, el tipo de enlace y lo longitud máxima de paquetes.

También cada línea de paquete capturado muestra información sobre el paquete, como la dirección IP de origen y destino, los puertos utilizados, el protocolo y la longitud del paquete.

- Describa 3 parametros del comando `tcpdump`

**-i** o **--interface**: Este parámetro se utiliza para especificar la interfaz de red en la que se realizará la captura de paquetes. Puede ser útil cuando el sistema tiene múltiples interfaces de red y se desea capturar el tráfico de una interfaz específica.

Ejemplo de uso: tcpdump -i eth0

**-n** o **--numeric**: Este parámetro se utiliza para mostrar direcciones IP y números de puerto en formato numérico en lugar de intentar realizar una resolución inversa de DNS. Usar este parámetro puede acelerar la captura de paquetes y evitar retrasos si hay problemas de resolución DNS.

Ejemplo de uso: tcpdump -n

**-w** o **--write**: Este parámetro se utiliza para escribir la salida de tcpdump en un archivo en lugar de mostrarla en la pantalla. Esto puede ser útil para capturar y almacenar el tráfico de red para su posterior análisis.

Ejemplo de uso: tcpdump -w archivo.pcap
