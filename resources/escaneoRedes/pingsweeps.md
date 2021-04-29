# Recursos de Hacking Ético

## Encontrando redes

Para no ir dando palos de ciego es importante ver qué sistemas responden al hacer ping en la red. Esto se llama ping sweeps, que es mandar mensajes de pings a todos los sistemas de una red. Un ping es una ICMP echo request que es un mensaje muy común y que responden los sistemas aunque hay firewalls que bloquean este tipo de mensajes.

### fping

Hay muchas herramientas para hacer esto, pero una de las más famosas es **fping**. Viene incluida con Kali Linux y para utilizarla simplemente tenemos que abrir una terminal y escribir:

```
fping -aeg 10.0.2.0/24
```

En este caso estoy analizando la red virtual que he creado con VirtualBox. El parámetro `e` significa que queremos que nos de el tiempo que ha pasado en devolvernos un paquete. El parámetro `a` que queremos nos muestra los sistemas que están vivos y el parametro `g` que queremos nos genera una lista con los sistemas.
La salida que me da este comando es:

```sh
$ fping -aeg 10.0.2.0/24
10.0.2.1 (0.218 ms)
10.0.2.2 (0.499 ms)
10.0.2.3 (0.394 ms)
10.0.2.5 (0.051 ms)
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.4
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.4
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.4
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.4
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.8
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.8
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.8
ICMP Host Unreachable from 10.0.2.5 for ICMP Echo sent to 10.0.2.8
```

Hay que recordar que si no obtenemos respuesta de un sistema no quiere decir que no esté ahí ya que un firewall podría bloquear la respuesta.

[Volver al inicio](./../../README.md)
