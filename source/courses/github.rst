GitHub
======

En este curso se abordarán temas relacionados al gestor de versiones `git` y la integración con la plataforma github_.

Requisitos previos
------------------
- Cliente `git`
- Cuenta en github_

Temario
-------
Qué es un repositorio?
______________________
Un repositorio es una carpeta o directorio en la cual se lleva el control y seguimiento de algún proyecto.

Con los gestores de versiones (como `git`) podemos llevar un control detallado de los cambios que han sufrido los archivos dentro del repositorio y con esto revisar versiones anteriores de los mismos (esto es muy útil para detectar la inyección de nuevos errores en el código).

Además de esto, el uso de control de versiones nos facilitan el trabajo colaborativo puesto que podemos realizar un `merge` del código, es decir, podemos mezclar las distintas partes de un mismo archivo facilitando la integración de los cambios realizados por distintas personas.

Lo que se hace con los repositorios es tomar "fotografías" del estado actual de los archivos, después podemos comparar distintas fotografías para ver las diferencias entre ellas. A estas fotografía la llamamos "commit", dichos `commits` suelen ser enviados a un servidor remoto para el tema de la colaboración y para mantener copias a prueba de fallos en una computadora local (en esta guía utilizaremos github_); para hacer esto se realiza el `push` de las fotografías hacía el servidor.
Las personas que estén "conectadas" a ese repositorio (realmente solo realizan copias o un `clone` del mismo) pueden obtener los nuevos `commits` haciendo `pull` desde el servidor.

Otro aspecto a mencionar es la existencia de las ramas o `branch` dentro de un repositorio, estas `branches` son versiones paralelas del mismo repositorio, las cuales podemos visualizar como ramificaciones del repositorio original en un momento en especifico y que podemos, si queremos, volver a integrar en un futuro. Estas ramas suelen utilizarse para diferenciar versiones y para llevar el control de características que se quieran añadir al proyecto (para hacer pruebas sin poner en riesgo al código principal, generalmente en la rama `master`).

Comandos
--------
Ahora que sabemos la teoría de como funciona un repositorio, veremos como crear y manejar uno. Para ello es necesario que nos posicionemos en la carpeta que queremos controla e indicar a `git` que queremos monitorearla.

.. code-block:: console

  [moy@AfroPC ~/repo]$ git init
  Initialized empty Git repository in /home/moy/repo/.git/

Nota: El repositorio no tiene por que estar vacío

No solamente podemos crear repositorios desde cero, con frecuencia nos interesará trabajar sobre repositorios ya creados por la comunidad o por algún colega.

.. code-block:: console

  [moy@AfroPC ~/repo]$ git clone https://github.com/humanytek-team/doc
  Cloning into 'doc'...
  remote: Enumerating objects: 31, done.
  remote: Counting objects: 100% (31/31), done.
  remote: Compressing objects: 100% (27/27), done.
  remote: Total 31 (delta 6), reused 26 (delta 3), pack-reused 0
  Unpacking objects: 100% (31/31), done.

Si se trata de un repositorio del que no tenemos permisos de escritura (como los proporcionados por la comunidad), se puede utilizar la URL del mismo (`HTTPS`); sin embargo, se recomienda que si se desea hacer el `clone` de un repositorio al cual haremos `push` se haga mediante el uso de su identificador de `SSH`, esto con la finalidad de hacer más segura la transferencia y evitar tener que colocar las credenciales de la plataforma cada vez que queramos hacer alguna transacción.
Para todo esto es necesario haber configurado inicialmente nuestro cliente de `git` con nuestro nombre, correo y, en caso de ser necesario, nuestras llaves `SSH`.

Nota: Se recomienda que los repositorios dentro de un servidor no sean clonados mediante SSH, al menos no sin una contraseña para autorizar las transacciones.

.. TODO Configurar git

Una vez generado o clonado el repositorio

Podemos llevar el rastreo del estado de nuestros archivos, para ello se utiliza el comando `git status`, el cual nos indicará que archivos han sufrido modificaciones desde el ultimo commit del que se tenga registro.

Para añadir un archivo a nuestra fotografía (`commit`) usamos el comando `git add FILE`, donde `FILE` es el archivo (o archivos) que queremos añadir (también podemos usar `.` para añadir todo).
Una vez añadidos a la escena (`stage`) podemos realizar la fotografía con `git commit -m 'MESSAGE'`, la parte de `-m 'MESSAGE'` (donde `MESSAGE` es el mensaje que queramos) es opcional, de no colocarla se nos abrirá un editor de texto en el cual debemos introducir la descripción del commit (se recomienda que sea breve y se suelen utilizar etiquetas como `[IMP]`, `[ADD]`, `[REM]`, `[REF]`, etc para indicar rápidamente la naturaleza del mismo).

Después de realizar varios `commits` (puede ser solo uno) podemos mandar nuestros `commits` al servidor con `git push`, si realizamos la conexión mediante `HTTPS` nos solicitará las credenciales de la plataforma, si fue con `SSH` solo nos pedirá la contraseña para hacer uso de la llave (en caso de que lo hayamos indicado).

Si queremos revertir los cambios realizados en un archivo (antes de hacer el `commit`) podemos hacer uso del comando `git checkout FILE`, con esto regresaremos el archivo a como estaba en el ultimo `commit`. Este comando también nos sirve para la creación y manejo de las ramas con la siguiente estructura: `git checkout -b BRANCH`, esto nos moverá (o creará) a la rama que indiquemos.

.. _github: https://github.com
