---
layout: post
title: Google Drive en Linux
---

La comodidad que nos otorga poder trabajar con directorios en la nube es absoluta y totalmente incuestionable. Modificas tus proyectos o creas unos nuevos en una carpeta en cualquier dispositivo, y luego no tienes que preocuparte de pasarlo con un USB o mandarlo por correo; ya que ¡está en la nube! Y gracias a los clientes que disponemos en nuestros ordenadores, teléfonos y tablets, podemos visualizarlo en tiempo real. Pero cuando nos conectamos desde Linux, la cosa se "complica" un poco...

En plataformas como Windows, iOS, Android y Mac OS, hay una sencilla aplicación que abriéndola, dispondremos de todo nuestro directorio como si fuese una carpeta local (y en parte lo es, ya que también se encuentra físicamente en nuestro terminal para poder acceder offline). Pero, ¿y los que trabajamos con Linux? 

Pues bien, aquí traigo una solución fácil y sencilla de disponer de toooodas las ventajas de GDrive en nuestro sistema:

1. Añadimos el repositorio desde el que nos descargaremos el cliente
..* **sudo add-apt-repository ppa:nilarimogard/webupd8**
2. Actualizamos la lista de repositorios
..* **sudo apt-get update**
3. Descargamos la aplicación en sí
..* **sudo apt-get install grive**

Con eso ya tendríamos todo preparado para comenzar a usar nuestro Drive, pero aún queda seleccionar en que directorio local querremos tener Drive:

1. Para ello creamos una carpeta en nuestro directorio personal con el nombre que queramos (en mi caso, le llamé Grive)
..* **mkdir ~/Grive**
2. Y nos ubicamos en el
..* **cd ~/Grive**
3. Grive, a diferencia de otros clientes no se actualiza y se mantiene al día automáticamente. Para ello habrá que hacer una primera petición para ver qué contiene nuestra carpeta en la nube. (Al hacerlo la primera vez, nos proporcionará un link que deberemos de pegar en nuestro navegador e ir a dicha web, allí Google nos pedirá que aceptemos que una aplicación de tercero usará nuestros datos y nos dará un código que tendremos que usar cuando nos lo pida al introducir el comando)
..* **grive -a**

Y voilà! Ya tenemos nuestro GDrive configurado y listo para usar. Cada vez que queramos actualizarlo (ya sea para bajar información del directorio online o para subir algo que hayamos creado o modificado) tendremos que usar el comando **grive** pero sin el **-a**.
