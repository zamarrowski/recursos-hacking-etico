# Recursos de Hacking Ético

## Escaneo de puertos

Normalmente las aplicaciones usan distintos puertos para poder recibir mensajes. Por ejemplo, tenemos el puerto 27017 que es el puerto por defecto que usa MongoDB y que se utiliza para abrir una conexión hacia la base de datos. Esto quiere decir que si hacemos un escaneo de puertos nos dirá que ese puerto está abierto y que probablemente hay un MongoDB detrás.

Los puertos existen en la capa de transporte por lo que usan el protocolo UDP o TCP para estar escuchando. Esto es importante tenerlo en cuenta para saber como las herramientas de escaneo de puerto funcionan para identificar el software que hay en un puerto abierto.

Cuando un puerto usa el protocolo TCP usan unos flags para saber si está abierto o cerrado. Un puerto abierto responde con la flag SYN al mensaje SYN/ACK y un puerto cerrado responderá con RST.
Sin embargo, cuando se usa el protocolo UDP es un poco más complicado ya que no hay una comunicación definida por defecto y depende del servidor como responder. Esto puede ser un reto para las herramientas que escanean de puertos ya que como puede recibir varias respuestas no sabe si está abierto, el servidor ha recibido un mensaje que no espera o simplemente está cerrado.

### nmap

Es la herramienta más famosa para escanear puertos que existe. Se utiliza a través de la línea de comandos y puede escanear puertos UDP y TCP. Lo bueno que tiene nmap es que además puede identificar sistemas operativos, aplicaciones y versiones de las mismas. Incluso permite correr scripts personalizados para poder extender la funcionalidad de nmap.

### Escaneo TCP

Es el tipo de escaneo más detallado y complejo ya que hay muchos puertos en una máquina. En concreto 65536 y escanear todos los puertos sería muy costoso y más cuando la mayoría no van a estar abiertos por lo que nmap solo escanea 1000 puertos por defecto.
Lo hace de la siguiente manera:

1. nmap manda un mensaje SYN al puerto.
2. si el sistema responde con SYN/ACK nmap manda un mensaje RST para decir que no quiere seguir con la comunicación.
3. si el sistema manda RST es que el puerto está cerrado.

Esto se hace usando la línea de comandos y para probar hay varios sitios webs que nos permiten lanzar scans (sin pasarnos). El sitio web es: http://scanme.nmap.org/
Lo primero que tenemos que hacer es saber la IP por lo que ejecutaríamos:

```sh
└─$ host scanme.nmap.org
scanme.nmap.org has address 45.33.32.156
scanme.nmap.org has IPv6 address 2600:3c01::f03c:91ff:fe18:bb2f
```

Una vez que tenemos la IP ejecutaríamos nmap:

```sh
nmap 45.33.32.156
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-24 05:53 EDT
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.16s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
9929/tcp  open  nping-echo
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 30.06 seconds
```

Como vemos nos dice que los puertos 22, 80, 9929 y 31337 están abiertos y que servicio es el que está expuesto en ese puerto.

nmap tiene otro tipo de escaneo que basicamente es en vez de responde RST al mensaje SYN/ACK intentará hacer la conexión completa y después cerrará la conexión. Esto se hace con el parametro ```-sT```

```
└─$ nmap -sT 45.33.32.156
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-24 05:59 EDT
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.17s latency).
Not shown: 993 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
80/tcp    open     http
1002/tcp  filtered windows-icfw
1037/tcp  filtered ams
1186/tcp  filtered mysql-cluster
9929/tcp  open     nping-echo
31337/tcp open     Elite
```

nmap se puede lanzar contra una subnet entera si hacemos uso de bloque CIDR. Por ejemplo, podemos lanzar
```sh
nmap -sT 192.168.86.0/24
```

### Escaneo UDP

El escaneo UDP es menos preciso y además casi todas las aplicaciones usan el protocolo TCP pero vamos a ver como funciona. Básicamente nmap manda un mensaje a los puertos y si no recibe nada se considera que está cerrado pero podría ser que esté abierto. Si recibe algún tipo de respuesta se considera que está abierto y si recibe un error ICMP se marca el puerto como cerrado o filtrado.

Hay un parámetro que se le pueda pasar con la flag `-T` que indica el tiempo de espera entre el envío de mensajes. Por defecto es 3 pero si queremos ir más lentos para no ser detectados podemos bajarlo a 1

Lanzaríamos el scan así:

```sh
nmap -sU 45.33.32.156
```

### Sacando información más detallada

Una de las cosas buenas de nmap es que nos puede decir la versión del software que hay detrás de un puerto. Esto es muy útil ya que si sabemos la versión de un software podemos buscar que vulnerabilidades tiene e intentar explotar alguna para poder conseguir acceso a un sistema.
Para que nmap nos de información del software hay detrás ejecutaríamos:

```sh
nmap -sV 45.33.32.156
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-24 06:12 EDT
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.17s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE    VERSION
22/tcp    open  ssh        OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
80/tcp    open  http       Apache httpd 2.4.7 ((Ubuntu))
9929/tcp  open  nping-echo Nping echo
31337/tcp open  tcpwrapped
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 38.73 seconds
```

Otra de las cosas que podemos hacer con nmap es sacar el sistema operativo que tiene la máquina ejecutando nmap con la flag `-O`:

```
nmap -O 45.33.32.156
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-24 06:14 EDT
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.13s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
9929/tcp  open  nping-echo
31337/tcp open  Elite
Device type: VoIP phone|firewall|webcam|specialized
Running (JUST GUESSING): Grandstream embedded (91%), FireBrick embedded (87%), Garmin embedded (87%), 2N embedded (87%)
OS CPE: cpe:/h:grandstream:gxp1105 cpe:/h:firebrick:fb2700 cpe:/h:garmin:virb_elite cpe:/h:2n:helios
Aggressive OS guesses: Grandstream GXP1105 VoIP phone (91%), FireBrick FB2700 firewall (87%), Garmin Virb Elite action camera (87%), 2N Helios IP VoIP doorbell (87%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 40.51 seconds
```

### Scripting con nmap

nmap incluye una funcionalidad de scripting que permite ejecutar scripts escritos en Lua y hay un montón de ellos. En kali linux podemos encontrar esos scripts en: `/usr/share/nmap/scripts`.
Hay un listado enorme y podemos ejecutar cualquiera de ellos usando el flag `--script=`.
Por ejemplo, voy a usar un script que me dirá los métodos http que se pueden usar en un sistema:

```sh
nmap -sS --script=http-methods.nse 45.33.32.156

Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-24 06:20 EDT
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 1 undergoing Ping Scan
Parallel DNS resolution of 1 host. Timing: About 0.00% done
Stats: 0:00:00 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 0.50% done
Stats: 0:00:01 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 11.00% done; ETC: 06:21 (0:00:08 remaining)
Stats: 0:00:01 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 55.50% done; ETC: 06:20 (0:00:01 remaining)
Stats: 0:00:02 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 56.67% done; ETC: 06:20 (0:00:02 remaining)
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
| http-methods:
|_  Supported Methods: OPTIONS GET HEAD POST
9929/tcp  open  nping-echo
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 31.18 seconds
```

Como vemos nos dice que podemos usar en el puerto 80 los métodos OPTIONS, GET, HEAD y POST.


[Volver al inicio](./../../README.md)
