# Recursos de Hacking Ético

## Ingeniería social: ataques web y wireless social engineering

Al igual que existen los emails de phishing existen los sitios web de phishing, es decir, sitios web en donde el dominio se parece mucho al real y donde la web se parece bastante a la original. Para ello hay muchas técnicas y herramientas que nos facilitan esta tarea.

Por ejemplo, una de las maneras para que un dominio se parezca al original de Apple (https://www.apple.com) sería conseguir un dominio https://www.apple.com.rogue.com y descargarnos la página web de Apple y hacer los cambios necesarios para que su Login nos envíe la información a nuestro servidor. Muchas veces los usuarios no ven la URL entera o no tienen los conocimientos suficientes como para darse cuenta de que esa URL no pertenece a Apple.

### Clonando sitios web

Hay varias herramientas para ello, en Windows tenemos WinHTTrack y en Linux tenemos wget.
Con linux solo tendríamos que acceder a una terminal y ejecutar, por ejemplo, `wget -m https://www.apple.com`. El parámetro `-m` sirve para hacer un clon del sitio web que le pasamos. Una vez que tenemos el sitio web en nuestro local podemos hacer los cambios que sean necesarios para añadir código malicioso o por ejemplo cambiar la página del Login para que envíe los datos a nuestro servidor.

### Wireless social engineering

Desde que las redes WiFi las conoce todo el mundo es un vector de ataque muy importante. Es muy común que cuando estamos en hoteles, cafeterías o restaurantes haya una red WiFi para el cliente en la que cuando nos conectamos se nos abre un portal de acceso donde nos pide que nos autentiquemos con Facebook o alguna otra red social.
Los atacantes pueden crear un punto de red WiFi falso donde todo parezca real y nos pidan que iniciemos sesión con Facebook. Si ese formulario realmente manda las credenciales a su servidor el atacante habría conseguido el email y la contraseña de tu Facebook de una manera en la que ni te has enterado.

Para esto también existen herramientas de automatización como el Social Engineer Toolkit de Metasploit y que podemos usar con Kali Linux. Podemos acceder a él a través de la terminal ejecutando `setoolkit` y nos imprimirá un menú como éste donde seleccionaremos la opción 1:

```sh
 Select from the menu:

   1) Social-Engineering Attacks
   2) Penetration Testing (Fast-Track)
   3) Third Party Modules
   4) Update the Social-Engineer Toolkit
   5) Update SET configuration
   6) Help, Credits, and About

  99) Exit the Social-Engineer Toolkit

set> 1
```

Una vez seleccionada la opción 1 nos mostrará lo siguiente donde lo que nos interesa es la opción 7:

```sh
 Select from the menu:

   1) Spear-Phishing Attack Vectors
   2) Website Attack Vectors
   3) Infectious Media Generator
   4) Create a Payload and Listener
   5) Mass Mailer Attack
   6) Arduino-Based Attack Vector
   7) Wireless Access Point Attack Vector
   8) QRCode Generator Attack Vector
   9) Powershell Attack Vectors
  10) Third Party Modules

  99) Return back to the main menu.

set> 7
```

A partir de ahí nos irá guiando según lo que nosotros necesitemos, ya sea hacer un ARP Spoofing para cargar algún malware o simplemente ver las peticiones que hace o dejar que se conecte y haga login con su usuario de Facebook para después obtener las credenciales.

[Volver al inicio](./../../README.md)
