---
layout: post
title: Conexion SSH
---

Te preguntarás que para qué te hace falta a ti, un usuario normal de PC, un acceso SSH a otra máquina. Pues bien, un acceso SSH es muy importante a la hora de cambiar de equipo de trabajo/estudio. Es la manera ideal, fácil y rápida de acceder a tus documentos almacenados en otro lado, aunque esté en otra área geográfica. De hecho, tendrías acceso a todo el ordenados.

Lo primero y principal será instalar un servidor SSH (muchas distros Linux ya lo traen en la consola por defecto) en la máquina a la que quieras acceder. Si estás usando otro SO o no te gusta el que trae tu Linux, te recomiendo descargar a instalar **Putty** (es el que yo usaba cuando tenía Windows). Y después un cliente en la máquina desde la que vayas a acceder. (También existen para dispositivos móviles).

Una vez instalado el cliente, estaremos totalmente preparados para nuestra primera conexión remota. Solo haría falta, en modo consola, escribir **"ssh usuario@IP"** donde **"usuario"** es el nombre del usuario LOCAL (obligatorio que sea un usuario válido) de la máquina a la que queremos acceder e **"IP"** es su correspondiente dirección IP. En modo gráfico, con algún cliente que hayamos instalado (como Putty), es muy sencillo; ya que te lo va indicando todo paso a paso.

Pero no vamos a dejarlo todo en una simple conexión, vamos a profundizar un poco más:


# Intercambio de datos

Ahora, aprenderemos a copiar elementos de y en la máquina remota. Para copiarte a ti, archivos de la otra máquina, bastará con el comando **"scp usuario@IP:dirección/archivo lugar/donde/copiar"**. En el caso de que lo que queramos sea copiar de la nuestra a esta, bastará con cambiar los parámetros de orden. (Quedaría algo así: **"scp lugar/del/archivo usuario@IP:sitio/a/copiar"***.

Otro punto a tener en cuenta, es que cada vez que nosotros accedemos a una nueva máquina, se nos guarda su clave pública para próximas conexiones. Esto nos garantiza que la próxima vez que queramos acceder a la misma máquina, será esa y no estamos siendo víctimas de un ataque; ya que entonces, la otra máquina tendrá otra clave y no coincidirá con la nuestra, indicándonos una alerta y que podemos estar en peligro. Estas claves se encuentran en **"/home/usuario/.ssh/known_hosts"**

Una buena práctica es **no acceder a nuestro servidor remoto mediante contraseña**; ya que si nos exponemos a un atacante o nuestra seguridad es baja, podría verse afectada la integridad de nuestros datos. Por su parte, el servidor podría negar los accesos por contraseña y permitirlos solo **mediante clave pública** (ya mencionamos algo antes, ¿te acuerdas?), pero eso es cosa del servidor, y nosotros por ahora tan solo somos clientes. Pero igualmente, podemos dejar de introducir contraseña y acceder con nuestra clave privada (mucho más seguro y fiable).


# Cómo acceder mediante comprobación de claves

Lo primero, será crear nuestra **pareja de claves (pública y privada)** con el comando **"ssh-keygen -t rsa"**. Nota: **"rsa"** es el tipo de la clave, también podría ser **"dsa"**. Explicaremos diferencias más adelante.

Ahora ya solo nos faltaría **exportar la clave PÚBLICA** al servidor remoto con **"ssh-copy-id -i id_rsa.pub usuario@IP"**. El nombre "id_rsa.pub" es el que dejamos por defecto al crearla, pero podemos hacerlo bajo otro nombre.

A partir de ese instante, ya podremos acceder remotamente sin indicar la contraseña; ya que el servidor validará la clave pública que tiene nuestra con la privada que seguimos manteniendo en nuestra máquina local y nos dejará acceder.
