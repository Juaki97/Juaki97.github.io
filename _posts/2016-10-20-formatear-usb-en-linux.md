---
layout: post
title: Formatear USB en Linux
---

Últimamente he escuchado y leído mucho acerca de gente que no sabe cómo formatear sus memorias usb en un Linux; ya que no todas las distros incluyen una herramienta gráfica. También he leído acerca de gente que se compra y le regalan un USB particionado, y por alguna razón, su ordenador solo le daja acceder a la partición menor.

Otro problema con el que me encontré fue con los formateos de USB’s dañados en Windows: tenemos una memoria (de por ejemplo 8GB) y al montarla para formatearla nos dice que solo tiene (por ejemplo) 200MB.

Aquí os voy a enseñar cómo hacer formatear un usb y quitarle las particiones que tenga, para dejarlo cómo si estuviera recién sacado de su caja original.

 
Para el tema de unidades de almacenamiento en Linux, tenemos una herramienta muy buena y útil llamada **“fdisk”** que nos dice, mediante consola, qué unidades de almacenamiento tenemos conectadas a nuestro sistema; ya sean discos duros extraibles, discos duros internos, usb, tarjetas de memoria, etc etc. Pero es una herramienta que requiere los permisos de administrador; así que, o iniciamos sesión como root o pasamos a usarla con sudo: **“sudo fdisk”**

Una vez utilizado dicho comando, nos aparecerá una lista de los dispositivos conectados, solo tendremos que buscar el que queremos en concreto. Por ejemplo, un usb podría ser perfectamente sdb mientras que tenemos nuestro disco duro como sda. Según el tipo de dispositivo que sea, cambian las dos primeras letras, por ejemplo, para discos duros sata y usb se utiliza **sd** y para los ide hd. Y seguido del ordén en el que se hayan leído en el sistema: a, b, c…

Una vez localizado ya nuestro dispositivo, para poder manipularlo habrá que desmontarlo; ya que Linux los monta siempre por defecto para poder leerlos y tener acceso a ellos de inmediado: **sudo umount sdb**. Aquí, por ejemplo, estamos trabajando con la unidad **“sdb”**

Ya desmontado podremos manipularlo a nuestro gusto:

1. Volveremos a usar la herramienta **“fdisk”**, pero esta vez con usaremos como parámetro la unidad que queremos manipular, en este caso: sdb. -> **sudo fdisk /dev/sdb.**
2. En el menú que se nos desplega, podemos seleccionar la letra **“m”** para ver todas las opciones. Aunque en este caso, como tenemos claro qué queremos hacer, pulsaremos directamte la **“p”** para obtener una tabla de las particiones de nuestro dispotivo. 
3. Si queremos ir borrando particiones; bien porque la memoria las traiga por defecto y no las querramos, porque no nos deja acceder a todas, o simplemente por un formateo limpio y queramos todo de 0, vamos pulsando la **“d”** (de delete).
4. Ya borradas todas, deberemos de crear una nueva para que nuestro dispositivo pueda montarse y usarse (en bruto no permite el sistema usarlo). Y para ello usaremos la letra **“n”** (de new).
5. Cuando tengamos ya todo seleccionado, quedará mandarlo a escribir; ya que lo que hemos hecho previamente ha sido la origanización, pero realmente no ha realizado ningún cambio. Para que todo lo anterior se efectúe, deberemos de usar la tecla **“w”** (de write)

Y ya está! Ya tenemos nuestro dispositivo de nuevo listo para usarse con toda su capacidad disponible y limpio. En el caso de que no te lo detecte, habrá que volverlo a montar con **“sudo mount sdb”**
