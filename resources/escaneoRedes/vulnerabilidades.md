# Recursos de Hacking Ético

## Escaneo de vulnerabilidades

Una vez que sabemos que puertos están abiertos y que aplicaciones y versiones de las mismas hay en esos puertos podemos ir a buscar que vulnerabilidades tienen esas aplicaciones e intentar lanzar varios exploits. El problema de hacer esto a mano es que, además de ser muy costoso en cuanto a tiempo, ya que tenemos que hacerlo a mano, puede ser que dañemos algún sistema al lanzar un exploit lo cual sería un poco desastroso a pesar de que esto siempre puede pasar.
Por otro lado, si estás haciendo una auditoría de Red Team y los empleados no saben que la auditoría se está haciendo no queremos ser detectados y lanzar un montón de exploits genera mucho ruido.

Para dar solución a este problema existen aplicaciones que se encargan de escanear puertos y aplicaciones y lanzar tests que están pensados no para comprometer un sistema sino para detectar las vulnerabilidades que tenga. Tampoco podemos fiarnos al 100% de lo que digan un scanner. Un scanner nos da lo que el cree que es una vulnerabilidad basado en los tests que ha lanzado pero SIEMPRE debemos comprobarlo a mano. Es decir, un scanner es una herramienta y no el fín.

Cuando un scanner nos da vulnerabilidades se puede producir los siguientes casos:

* Falso positivo: un scanner nos da una vulnerabilidad pero después de investigarlo a mano vemos que realmente no lo es.
* Falso negativo: un scanner NO nos ha dado una vulnerabilidad que después de una investigación manual nosotros si hemos encontrado.
* Verdadero positivo: un scanner ha encontrado una vulnerabilidad y efectivamente esa vulnerabilidad existe.
* Verdadero negativo: un scanner no ha encontrado una vulnerabilidad y realmente esa vulnerabilidad no existe.

Los scanners más famosos a día de hoy son [OpenVAS](https://www.openvas.org/) y [Nessus](https://www.tenable.com/products/nessus/nessus-professional). Estas herramientas son muy útiles para realizar scans periódicos y para visualizar desde una interfaz gráfica las vulnerabilidades de nuestros sistemas.



[Volver al inicio](./../../README.md)
