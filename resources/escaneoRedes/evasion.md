# Recursos de Hacking Ético

## Técnicas de evasión

Cualquier sistema de una empresa tendrá algún sistema de detección de intrusos, de bloqueo o algún sistema de alertas que hará que si no tenemos cuidado nos descubran. Si esto pasa y estamos en un Red Team hemos fracaso en nuestro objetivo. Por fortuna, hay algunas técnicas de evasión y las más comunes son:

* Esconder los datos: podemos usar algún tipo de cifrado o ofuscar los datos para que no se distinga lo que estamos haciendo y no sea fácil para los sistemas de detección analizar lo que estamos haciendo y que mande alguna alerta. Por ejemplo, podemos usar URL encoding que remplaza los caracteres con valores hexadecimales del código ASCII.
* Alteraciones: los sistemas de detección suelen usar un sistema que analiza las firmas de nuestro malware. Esto puede ser un hash, por ejemplo. Muchos malware ya están registrados, por lo que si detectan un programa con el mismo hash que ellos tienen en la base de datos podemos ser descubiertos. Pero si nosotros alteramos el programa ese hash cambiará y no seremos detectados.
* Fragmentación: esta técnica se usa para evadir los mecanismos de seguridad de una red ya que cuando dividimos un paquete tiene que volver a montar todos los fragmentos para intentar leer el paquete y esto a veces no se hace ya que toma mucho tiempo y añadiría latencia a la red.
* Datos mal formados: hay veces que cuando no seguimos al pie de la letra un protocolo recibimos respuestas inesperadas y esto puede ser útil ya que hay veces que nos da cierta información que antes no teníamos.
* Ir lento: los scans rápidos suelen ser muy fáciles de detectar pero un scan lento es más difícil de detectar porque no genera tanto ruido en una red.
* Bomba de humo: si hay un sistema de alertas y generamos grandes cantidades de alertas no nos tendremos que preocupar ya que las personas que estén mirando todas esas alertas estarán perdiendo tiempo en ver lo que está pasando y no en lo realmente importante.
* Tunneling: podemos usar túnes SSH para sacar información de manera cifrada sin que un sistema nos detecte ya que no podrá ver qué datos se están sacando.

[Volver al inicio](./../../README.md)
