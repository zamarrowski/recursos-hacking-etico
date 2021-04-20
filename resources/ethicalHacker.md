# Recursos de Hacking Ético

## 1. ¿De qué va eso de Ethical Hacker?

Antes de empezar a hablar de hacking ético deberíamos hablar sobre que se considera ético ya que es algo que para unas personas pueden significar una cosa y para otras personas otra cosa totalmente distinta. Al fin y al cabo, trabajando vamos a tener acceso a información sensible y a sistemas críticos por lo que es importante trabajar de una manera ética.
Básicamente se trata de mantener la información que obtenemos durante el trabajo de manera privada y prestando mucha atención a la información del cliente. Se espera de nosotros que no revelemos a ninguna fuente externa ningún dato que podamos sacar del cliente y que a su vez revelemos todos los fallos de seguridad que encontremos a nuestro cliente.

Esto también se aplica cuando encontramos, por ejemplo, un bug que puede afectar a muchísima gente. Imaginemos que hemos encontrado una vulnerabilidad en una versión de Apache. ¿Sería correcto publicarlo en un foro de Internet sin avisar a Apache Software Foundation primero? Lo que haría un ethical hacker es avisar a Apache, trabajar con ellos y una vez que esté solucionado se podría publicar el fallo encontrado.
Se espera de un ethical hacker que no dañe ningún sistema al que se le ha dado acceso y si esto ocurriese sin querer debería informarse de manera inmediata al cliente que nos ha contratado.

Seguramente hayas oído hablar de los hackers black hat, gray hat and white hat. Podría decirse que son:

* black hat: personas que utilizan sus conocimientos para hacer el mal. Normalmente acciones que son ilegales.
* gray hat: estos están en medio pero a veces usan técnicas de los black hat.
* white hat: personas que siempre usan sus conocimientos para hacer el bien.

Para que no caigamos en malentendidos cada vez que hacemos un pentesting deberíamos acordar con nuestro cliente un ámbito de acción (sistemas, redes, servicios...) y tener muy definidos los pasos que se van a realizar. Todo lo que se salga de ese ámbito no sería una acción ética.

### Metodología del Ethical Hacking

Básicamente la podemos dividir en 5 pasos que iremos viendo en los apuntes más adelante

#### 1. Reconocimiento

Es la parte en la que intentamos obtener toda la información de nuestro objetivo. Quizás puedas saber más o menos quien es tu objetivo pero si tenemos toda la información posible nos facilitará el pentesting más adelante. De hecho, en este paso puede ser que encontremos información sensible que está expuesta a Internet y que podamos usar para realizar un ataque de ingeniería social.
Se trata de saber el tamaño y el alcance de nuestro objetivo.

#### 2. Escaneo y enumeración

Una vez que tenemos las redes identificadas podemos proceder al escaneo de las mísmas y aquí obtendremos no solo un listado de puertos abiertos sino que probablemente obtengas que servicios y versiones están corriendo en los mismos. Esto nos servirá más adelante como punto de entrada ya que quizás alguno de esos servicios tenga alguna vulnerabilidad que podamos explotar para obtener acceso a la máquina.

#### 3. Obteniendo acceso

Quizás este sea el paso más llamativo y para mi el más divertido ya que se trata de explotar una vulnerabilidad para poder acceder a un sistema. Lo más importante a tener en cuenta es que hay que documentar en todo momento como se obtuvo acceso a la máquina para poder replicarlo y poder reportar el fallo de seguridad. La realidad es que un ataque de ingeniería social tiene más probabilidades de éxito que encontrar una vulnerabilidad en un sistema y poder explotarla.

#### 4. Mantener el acceso

Una vez que hemos conseguido obtener acceso a una máquina es muy importante realizar ciertas acciones para poder seguir teniendo acceso en el futuro ya que el usuario puede apagar la máquina o simplemente arreglar la vulnerabilidad que hemos podido explotar y no podríamos acceder más. Por ejemplo, podríamos instalar un [rootkit](./terminologia.md) que nos permita instalar un backdoor para poder entrar cuando queramos.

#### 5. Ocultar nuestras pistas

Se trata de que una vez que tenemos acceso ocultemos las acciones que realizamos en la máquina para no llamar la atención y no ser detectados y así poder mantener el acceso a la misma.

[Volver al inicio](./../README.md)
