---
title: "Instalar Linux en Windows 10 con WSL"
slug: "instalar-wsl"
author: "Bernardo Ayala"
type: "posts"
date: 2020-07-15
draft: true
categories: "Programación"
tags: ["linux", "wsl", "terminal"]
icon: "/img/icons/linux.png"
---

Una de las herramientas que más hecho en falta cuando estoy desarrollando en Windows es una buena línea de comandos. Existen buenas alternativas para resolver este problema, una sería instalar un buen emulador de terminal como [cmder]( https://cmder.net/).

Sin embargo, existe una forma de poder utilizar la terminal de Linux dentro de Windows. Esto podemos lograrlo a través del Windows Subsystem for Linux (WSL). Que básicamente nos permite instalar una distribución de Linux dentro de Windows.
En esta guía voy a listar los pasos para instalar el WSL, instalar ZSH y como correr el Shell de Linux dentro de la nueva Windows Terminal, para esto lo primero que tienes que hacer es actualizar Windows 10 hasta su última versión.

### Habilitar el modo desarrollador

Abre el menú de configuración de Windows 10, bien sea haciendo click en inicio y seleccionando la opción que dice “configuración” o también puedes presionar la combinación de teclas **Windows + I**.

![Captura de pantalla](/img/screenshots/windows-settings.png)

Una vez dentro selecciona la opción que dice “Actualización y seguridad”

![Menú de configuración de Windows](/img/screenshots/windows-settings2.png)

Luego tienes que seleccionar la opción para desarrolladores y entre las opciones que se muestran debes seleccionar la que dice “activar modo desarrollador”. Te saldrá una advertencia a la cual tendrás que darle si para continuar y luego deberás reiniciar para que se apliquen los cambios.

![Activar modo desarrollador en Windows](/img/screenshots/windows-settings3.png)
