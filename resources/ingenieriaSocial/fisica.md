# Recursos de Hacking Ético

## Ingeniería social física

No toda la información es digital, por lo que podemos conseguir mucha información a través de las personas o incluso si podemos acceder a un edificio. Si podemos acceder a un edificio podemos obtener información mirando a las pantallas, viendo ordenadores que no se han bloqueado, robando USBs o conectándonos a la red por cable. Sin embargo, hay medidas de seguridad físicas que nos complican esta tarea.

### Tarjetas de acceso

Una de las medidas de seguridad más clásicas son las tarjetas de acceso. Normalmente un empleado acerca su tarjeta a un lector y la puerta se abre. Estas tarjetas suelen funcionar con una identificación de radio frecuencia (RFID) que son capaces de leer esos lectores. Sin embargo, esta medida tiene algunos problemas. El primero sería algo conocido como "tailgating", que es cuando una persona usa su tarjeta de acceso y entra muy rápido y tu entras detrás de él antes de que la puerta o el torno se cierre.
Otro de los problemas de las tarjetas de acceso es que se pueden clonar muy fácilmente.

### Puertas dobles

Estas son las típicas puertas que hay en algunos bancos donde debemos pasar primero una puerta, esperar que se cierre y después se abrirá la siguiente puerta. Esto sirve para verificar el acceso de una persona. Es decir, si alguien entra con una tarjeta de acceso que no es suya el guardia de seguridad puede pedirle la identificación antes de abrir la segunda puerta y se quedaría atrapado.

### Dispositivos de biometría

En la actualidad estamos muy acostumbrados a ver estos dispositivos. Ya desbloqueamos nuestros móviles con la huella dactilar y también con la cara. Apple tiene el FaceID y Android tiene también un sistema de reconocimiento facial. Estos son algunos de los que más usamos en el día a día pero podemos encontrarnos con:

* Huellas dactilares: son muy utilizados pero con una réplica de alta resolución se les puede llegar a engañar. Hay algunos más modernos que tienen en cuenta la temperatura pero igualmente se les podría engañar.
* Escáner de iris: es la versión más moderna del escaneo de ojos. El patrón del iris se considera único por cada persona y una de sus ventajas es que se utiliza luz para iluminar el ojo, por lo que podría funcionar en la oscuridad.
* Escáner de retina: la retina contiene patrones de los vasos sanguíneos y esto se usa para identificar a la persona.
* Reconocimiento de voz: hay muchos problemas con los lectores de voz. Uno de ellos es que tu voz puede cambiar durante el día debido a muchos factores. Por ejemplo, el frío afecta a nuestra voz y no sería muy eficaz.

Elegir uno de estos sistemas de seguridad dependerá de el ratio de éxito al intentar identificar a una persona.

### Llamadas telefónicas

No es exactamente algo físico pero se puede obtener bastante información a través de una llamada telefónica. Los atacantes a veces llaman a números de empleados de una empresa que quieren atacar haciéndose pasar por el soporte IT diciendo que han detectado actividad anómala en su equipo y que no se preocupe que están ahí para ayudar. A partir de ahí pueden intentar obtener contraseñas, usuarios o lo que se les ocurra.

### Cebos

Imagina que estás saliendo del trabajo y te encuentras un USB al lado de tu coche. Un USB de 256gb, bonito y que te encanta. Seguramente lo cogerías e irías a casa a enchufarlo al ordenador e intentar ver qué tiene dentro o simplemente para formatearlo y usarlo para tus cosas. Pues esto era un ataque muy común para sistemas operativos Windows XP y Windows Vista. Se podía hacer que se ejecutase un fichero a través del `autorun.inf`. Si un atacante mete un script que cree una conexión inversa le estarías dando acceso sin darte cuenta.

[Volver al inicio](./../../README.md)
