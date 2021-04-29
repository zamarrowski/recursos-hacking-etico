# Recursos de Hacking Ético

## Sniffing

Sniffing es la técnica de capturar paquetes de red para poder ver su contenido. Esto es muy importante ya que cuando somos capaces de capturar esos paquetes podemos llegar a conseguir usernames y passwords u otra información importante como tokens de autenticación o autorización. Para ello hay varias herramientas que vamos a ver. Para capturar paquetes de la red vamos a necesitar una interfaz de red especial que podamos poner en modo monitor. Una de las más recomendadas es [esta](https://www.amazon.es/gp/product/B00842T6YW/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1).

### tcpdump

Es una herramienta que viene por defecto con los sitemas Unix y la cual es muy fácil de usar pero a su vez es muy potente. Con ejecutar `tcpdump` en una terminal de un sistema Unix nos mostrará los paquetes que han sido capturados. En ella veremos cómo incluso resuelve una IP a su dominio. Si lo que queremos ver es la dirección IP podemos ejecutar `tcpdump -n`. Si queremos ver más información sobre los paquetes podemos incluir la flag `-v`, `-vv` o `-vvv` dependiendo del nivel de información que queramos obtener. Por último si queremos guardar la salida en un fichero podemos usar la flag `-o nombreDelFichero.txt`.

### Wireshark

Es una aplicación con interfaz gráfica que nos permite obtener los paquetes de una red de manera muy fácil y nos ayuda a visualizar todo lo que está pasando en una red. Es la aplicación más famosa para obtener paquetes de una red. Incluye funcionalidades como guardar en un fichero, importar datos de otros analizadores de paquetes, etc... Viene incluida con Kali Linux.

![wireshark](./../img/wireshark.png)

[Volver al inicio](./../README.md)
