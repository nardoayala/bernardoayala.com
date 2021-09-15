---
title: "Cómo borrar todas las carpetas node_modules"
slug: "borrar-node-modules"
description: "Aprende a borrar automáticamente todas las carpeta node_modules que se han ido acumulando en tus proyectos"
author: "Bernardo Ayala"
type: "posts"
date: 2021-09-15
draft: false
categories: ["Tutoriales"]
tags: ["node","modules","npm"]
icon: "/img/icons/bash.png"
images: [/img/memes/npm-meme.webp]
---

A medida que vas desarrollando tus proyectos web todas las librerías que vas instalado, ya sea a través de `npm` o de algún otro gestor de paquetes, se van acumulando en carpetas llamadas `node_modules`.

![Meme de get all things](/img/memes/npm-meme.webp)

Si no estás atento de borrarlas una vez termines, probablemente tengas bastante espacio del disco duro consumido en dependencias que ya no estás utilizando.

Una solución es ir de vez en cuando borrándolas manualmente, pero seamos sinceros Ain't Nobody Got Time for That. Te voy a enseñar cómo puedes borrar todas estas carpetas de forma recursiva a través de la línea de comandos.

> **Nota:** Estos comandos solo funcionan en Linux y Mac, si estás en Windows no te funcionarán a menos que tengas instalado el Windows Subsystem for Linux. Si te interesa saber cómo instalarlo, chequea mi post de [cómo instalar WSL](/instalar-wsl).

## Listar todas las carpetas node_moduels

Lo primero es ir a la carpeta donde tengas todos tus proyectos y listar todos los subdirectorios llamados `node_modules`. Este comando buscará tanto en el directorio actual como en los subdirectorios y te devolverá una lista de todas las carpetas encontradas así como cuánto pesan.

```bash
find . -name "node_modules" -type d -prune | xargs du -chs
```

El output será similar a este:

```bas
269M    ./diseno-para-programadores/4-app/node_modules
32M     ./platzi-games/node_modules
64M     ./webpack/js-portfolio/node_modules
364M    total
```

## Borrar todas las carpetas node_modules

Ya una vez que tienes una idea clara de cuales carpetas vas a borrar y cuánto espacio recuperarás, ya puedes correr el comando para borrarlas.

El comando es bastante parecido pero ahora le agregaremos `rm -rf`. Recuerda siempre tener cuidado al agregar la flag `-rf` ya que todo lo que borres de esa forma será irrecuperable.

```bash
find . -name "node_modules" -type d -prune -exec rm -rf '{}' +
```

Si quieres excluir alguna carpeta en la cual quieras conservar las dependencias, puedes correr el mismo comando con esta modificación:

```bash
find . -not -path "./carpeta-a-excluir/*" -name "node_modules" -type d -prune -exec rm -rf '{}' +
```

¡Listo! Acabas de recuperar espacio valioso en tu disco duro que no estaba siendo utilizado. Recuerda hacer esta limpieza de vez en cuando para no tener acumulados tantas dependencias sin usar.
