---
title: "Crear shortcuts en WSL a las carpetas de Windows"
slug: "wsl-shortcuts-a-windows"
author: "Bernardo Ayala"
type: "posts"
date: 2020-11-22
draft: false
categories: ["Tutoriales"]
tags: ["WSL","Terminal","Bash","symlinks"]
icon: "/img/icons/symlink.png"
---

Dentro de nuestro Windows Subsystem for Linux (WSL) podemos acceder a los discos de windows a través de `/mnt`. Por lo que si tenemos que acceder a una carpeta dentro de nuestros documentos o descargas, podemos hacerlo utilizando un comando como este:

```bash
cd /mnt/c/Users/<username>/Documents
```

Y eso está bien, ese comando funciona de maravilla. El detalle está en que cuando estamos constantemente entrando en los directorios de Windows, se vuelve un poco tedioso tener que escribir la ruta completa todo el tiempo.

Por suerte podemos crear algo que se conoce como un enlace simbólico (**symlink**), que nos permite tener enlaces a archivos o carpetas que se encuentran en rutas distintas a las que nos encontramos actualmente.

De esta forma, si necesitamos entrar con mucha frecuencia a nuestros documentos en Windows, podemos crear un **symlink** apuntando a esa carpeta de la siguiente forma:

``````bash
ln -s /mnt/c/Users/<username>/Documents ~/Documents
``````

Una vez hecho esto, siempre que te encuentres dentro de la carpeta donde creaste el symlink (en mi caso dentro de `~/`), puedes acceder a los documentos de Windows escribiendo `cd Documents`, en lugar de escribir la ruta completa a través de `/mnt`.