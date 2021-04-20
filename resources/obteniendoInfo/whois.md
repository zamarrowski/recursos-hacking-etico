# Recursos de Hacking Ético

## 6.1 Whois y host

Es muy importante obtener información sobre los activos que vamos a hacer un test de intrusión y lo primero que tendríamos que hacer es saber sobre lo que vamos a hacer ese test.
Para ello hay varios comandos que nos van a facilitar la vida. El primero de ellos es whois.

### Whois

Básicamente es un protocolo muy usado para obtener datos de un dominio o una IP. Cuando ejecutamos este comando estamos haciendo una petición sobre los principales registradores de dominios para que nos den cierta información a nivel general sobre de quien es ese dominio.

Es muy fácil de usar y podemos probarlo con cualquier dominio:

```
$ whois www.villanuevadelatorre.com
```

El problema es que por leyes como la GDPR en la actualidad no es fácil sacar gran información usando whois. Pero quizás podamos sacar información útil como el correo electrónico que tienen, rango de IPs, etc...

### Host

Este comando nos sirve para obtener las IPs de un dominio en concreto. Se utiliza igual que whois:

```
$ host villanuevadelatorre.com
```

Y nos daría una salida parecida a esta:

```
villanuevadelatorre.es has address 217.160.230.129
villanuevadelatorre.es has IPv6 address 2001:8d8:1001:41ab:9f6a:bdcd:bee0:501e
villanuevadelatorre.es mail is handled by 5 alt1.aspmx.l.google.com.
villanuevadelatorre.es mail is handled by 5 alt2.aspmx.l.google.com.
villanuevadelatorre.es mail is handled by 1 aspmx.l.google.com.
villanuevadelatorre.es mail is handled by 10 aspmx2.googlemail.com.
```

Aquí ya podemos ver sobre que IP está montando el sitio web. Si hacemos el whois sobre esa IP podremos obtener información adicional e incluso veremos que hosting está utilizando.

[Volver al inicio](./../../README.md)
