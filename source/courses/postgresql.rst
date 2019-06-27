PostgreSQL
==========
**Duración: 30 min.**

Durante este curso se verán temas relacionados a PostgreSQL y SQL en general. Cabe mencionar que es muy rara la ocasión en la que se requiere acceder al gestor de PostgreSQL dentro del mundo del desarrollo de módulos de Odoo.

Requisitos previos
------------------
- Cliente PostgreSQL 9.4 o superior

Temario
-------

.. TODO explicar creación de roles

Como empezar
____________
Lo primero que debemos hacer para trabajar con las BD de PostgreSQL es entrar a la interfaz del mismo, para ello utilizamos el siguiente comando.

.. code-block:: bash

  [moy@AfroPC ~]$ psql -d DATABASE
  psql (9.6.11)
  Type "help" for help.

  grqz=#

Nota: Si no tenemos una BD, podemos crearla con `createdb DATABSE`.

Tablas
______
Dentro de la BD se encuentran las tablas de nuestra aplicación (más adelante veremos que suelen representar a un objeto con todas sus propiedades y, en ocasiones, las relaciones que guardan con otros objetos).
Para listar las tablas de una BD dentro de PostgreSQL usamos el comando `\dt`, esto nos listara las tablas de dicha BD.

Interactuar con la BD
_____________________
Una vez que estemos dentro de la BD hay varías cosas que podemos hacer con los registros dentro de las tablas, las mas comunes son realizar consultas (`SELECT`), actualizar registros existentes (`UPDATE`), añadir nuevos registros (`INSERT`) y eliminar los mismos (`DELETE`).

Para cerrar la interfaz podemos utilizar el comando `\q` o la combinación de teclas `Ctrl-D`

Apéndices
---------
- http://www.postgresqltutorial.com/
