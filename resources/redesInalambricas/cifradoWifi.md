# Recursos de Hacking Ético

## Redes inalambricas: cifrado Wi-Fi

Ya que los datos se transmiten por el aire los datos son más sensibles a ser interceptados por eso desde que las redes Wi-Fi se empezaron a usar para uso comercial se ha puesto mucho incapié en que sean seguras y los datos vayan cifrados para conservar la privacidad.

### Wired Equivalent Privacy (WEP)

Este sistema de cifrado es el más inseguro de los que hay hoy en día y utiliza el algoritmo de cifrado RC4 el cual utiliza claves de 64 bits o 128 bits. Si usa la clave de 64 bits hay 40 bits donde son la clave y un vector de inicialización de 24 bits. Con la de 128 bits pasa lo mismo pero la clave es más fuerte. El problema de esto es que se está asumiendo que el vector de inicialización es totalmente random y esto no es verdad ya que con la suficiente cantidad de paquetes en la red se repetirá en algún momento y podemos conseguir crackear la contraseña Wi-Fi.

### Wi-Fi Protected Access (WPA)

Desde que se descubrió que WEP era problemático y muy fácil de hackear se intentó buscar un mejor sistema de cifrado. Ahí es donde nació WPA. Lo curioso de este sistema de cifrado es que no hubo que hacer ningún cambio en el hardware para hacerlo funcionar, simplemente se podía habilitar haciendo una actualización del firmware. WPA introdujo el Temporal Key Integrity Protocol (TKIP). Ahora todos los paquetes tienen su propia clave para cifrar y descifrar el contenido y esto es temporal. WPA soporta dos modos de autenticación. El primero (WPA-Personal) es básicamente el mismo que WEP pero usando el método PSK. Lo que hace este método y es proveer una contraseña que es usada en el vector de inicialización para generar la clave cifrada que se usa el el algoritmo RC4.

El otro método de autenticación es el WPA-Enterprise que hace uso de una base de datos como podría ser el Windows Active Directory.
Por último, está el método WPS que lo traen algunos puntos de acceso y permite que al pulsar un botón los clientes no tengan que saber cual es la clave de acceso sino que la conexión se hace a través de un PIN. El problema con este método es que es muy fácil de hackear.

### Wifi Protected Access 2 (WPA2)

La mayor mejora que se hizo fue usar el Estandar de Cifrado Avanzado (AES) lo peor es que sigue siendo posible hackear una red Wi-Fi através de WPS.

[Volver al inicio](./../../README.md)
