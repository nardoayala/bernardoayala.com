---
title: "Configurar los defaults de NPM al inicializar un proyecto"
slug: "npm-defaults"
author: "Bernardo Ayala"
type: "posts"
date: 2020-07-15
draft: false
categories: ["Programación"]
tags: ["npm","configuraciones"]
icon: "/img/icons/npm.png"
---

Cuando iniciamos un proyecto nuevo en NPM `(npm init)` nos aparecerá un pequeño formulario en la terminal para rellenar los valores que serán la base de nuestro archivo package.json

![Gif de terminal corriendo comando npm init](/img/gifs/npm-init-1.gif)

Este comando lo usaremos con bastante frecuencia, y hay algunos campos, como tu nombre, que serán siempre los mismos, por lo que escribirlos a cada rato, a pesar de no consumir mucho tiempo, puede llegar a ser molesto. Y a fin de cuentas ¿para qué estamos aprendiendo a programar sino para dejar que la computadora haga sola este tipo de cosas repetitivas?

Existen muchas opciones de configuración, pero en este caso creo que las tres a las que más vale la pena cambiarles el default son al nombre del autor, su correo y el tipo de licencia. Si quieres ver la cantidad de configuraciones distintas que puedes modificar puedes usar el comando `npm config ls -l`, pero no te recomiendo cambiar nada que no entiendas del todo.

En este tutorial nos concentraremos en estos tres comandos:

- `npm config set init-author-name "Nombre del autor"`
- `npm config set init-author-email "correodelautor@correo.com"`
- `npm config set init-license "Tipo de licencia"`

Usa vez tengas modificados estos valores, ya estarán por defecto cuando utilices el comando npm init

![Gif de terminal corriendo comando npm init](/img/gifs/npm-init-2.gif)

La mejor parte es que estos mismos valores son los que aparecerán por defecto cuando uses el comando `npm init -y` para crear el archivo package.json sin tener que rellenar ningún formulario en la terminal.

![Gif de terminal corriendo comando npm init](/img/gifs/npm-init-y.gif)

Es una configuración bastante sencilla que nos ahorrará tener que escribir una y otra vez los mismos datos en el formulario. Sé que se un ahorro pequeño de tiempo, pero por este tipo de cosas sencillas es que amo programar, incentivemos que las computadoras hagan todas las cosas aburridas y repetitivas por nosotros.
