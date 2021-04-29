# Recursos de Hacking Ético

## 7.4 Cambiando la MAC

Aunque la Mac solo es conocida por la red interna en la que estamos es importante saber cambiarla ya que podemos estar realizando una intrusión interna y no queremos que se nos identifique.

Para ver la MAC que tenemos, con ejecutar en la terminal `ifconfig` la veríamos:

```sh
ether 08:00:27:ab:08:1c  txqueuelen 1000  (Ethernet)
```

Para cambiarla lo primero que tenemos que hacer es deshabilitar la interfaz de red. En mi caso sería:

```sh
ifconfig eth0 down
```

Una vez que la hemos deshabilitado podemos cambiarla usando macchanger:

```sh
macchanger -m 00:11:22:33:44:55 eth0
```

Si ejecutamos otra vez `ifconfig` veremos que nuestra MAC ha cambiado a la que le hemos especificado.
Es importante recordar que esta dirección no es permanente sino que cuando se reinicie volverá a la MAC original.

[Volver al inicio](./../../README.md)
