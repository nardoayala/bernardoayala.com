---
title: "NPM: actualizar todos los paquetes a su última versión"
slug: "npm-actualizar-paquetes"
description: "¿Cómo instalas todas las dependencias de npm guardadas en el archivo package.json a su última versión disponible?"
author: "Bernardo Ayala"
type: "posts"
date: 2020-12-16
draft: false
categories: ["Tutoriales"]
tags: ["npm"]
icon: "/img/icons/npm.png"
---

Cuando instalas un nuevo paquete en tu proyecto a través del comando `npm install <nombre-del-paquete>` la última versión del paquete se descarga dentro de la carpeta `node_modules` y se agrega una nueva entrada dentro de los archivos `package.json` y `pacakge-lock.json`.

Así, si instalas por ejemplo el paquete `static-server`, esta entrada se agregaría a tu archivo `package.json`:

````json
{ 
  "dependencies": {
    "static-server": "^2.2.1"
  }
}
````

Y esta entrada a tu archivo `package-lock.json` :

```json
{
  "lockfileVersion": 1,
  "requires": true,
  "dependencies": {
    "static-server": {
      "version": "2.2.1",
      "resolved": "https://registry.npmjs.org/static-server/-/static-server-2.2.1.tgz",
      "integrity": "sha512-j5eeW6higxYNmXMIT8iHjsdiViTpQDthg7o+SHsRtqdbxscdHqBHXwrXjHC8hL3F0Tsu34ApUpDkwzMBPBsrLw==",
      "requires": {
        "chalk": "^0.5.1",
        "commander": "^2.3.0",
        "file-size": "0.0.5",
        "mime": "^1.2.11",
        "opn": "^5.2.0"
      }
    }
  }
}
```

Estos archivos nos dicen que la versión que tenemos instalada es la `2.2.1` así como también nos establecen las reglas para actualizar el paquete son `^2.2.1`, que según el [sistema de versionado de npm](/npm-versionado/) significa que solo puedes actualizar parches menores y no versiones que rompan compatibilidad.

Es decir, se podría actualizar a la versión `2.2.2` o a la `2.3.0` pero no se podría actualizar a la `3.0.0` ya que esta última son cambios muy grandes que pueden causar problemas de compatibilidad.

Cuando utilizamos el comando `npm update` solamente se actualizarán los cambios menores, si se consigue una versión superior esta será descargada y se modificará el archivo `package-lock.json`, mientras que el archivo `package.json` quedará inalterado.

Para chequear si existen nuevas versiones de las dependencias instaladas, basta con ejecutar el comando `npm outdated`, esto arrojará un resultado similar al siguiente si ha pasado un buen tiempo desde la última vez que actualizaste las dependencias:

![Screenshot de versiones de dependencias](/img/screenshots/npm-packages.webp)

Algunas de esas nuevas versiones tienen cambios mayores, así que ejecutar `npm update` no las actualizará. Este comportamiento es debido a que al ser cambios mayores, actualizar puede llegar a romper tu proyecto y `npm` trata de evitarlo.

Para poder todas estas dependencias a su última versión, deberás instalar un paquete llamado `npm-check-updates` de forma global:

````bash
npm install -g npm-check-updates
````

Una vez instalado deberás correr el siguiente comando:

```bash
ncu -u
```

Esto modificará tu archivo `package.json` para que todas las dependencias estén listadas en sus últimas versiones.

Una vez completado este proceso, basta con ejecutar el siguiente comando para actualizar todas tus dependencias:

```bash
npm install
```

Recuerda hacer este tipo de actualizaciones con cuidado ya que algunos de los cambios mayores puede llegar a romper tu proyecto.
