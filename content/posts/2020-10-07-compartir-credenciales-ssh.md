---
title: "WSL: copiar llaves ssh de Windows"
slug: "copiar-ssh-widnows-wsl"
author: "Bernardo Ayala"
type: "posts"
date: 2020-10-07
draft: false
categories: ["Tutoriales"]
tags: ["bash","ssh", "wsl"]
icon: "/img/icons/bash.png"
---

Una vez tengas configurado tu distribución de [Linux dentro de Windows 10](/instalar-wsl/) a través de WSL, te vas a conseguir con el problema de que al momento de querer conectarte a GitHub para hacer push o pull de alguno de tus repositorios, no vas a tener los permisos para hacerlo.

![Screenshot de error en termianl](/img/screenshots/ssh-sharing-1.webp)

Esto es debido a que las configuraciones que tenías en tu ambiente de desarrollo con Windows para tener una conexión con llaves ssh no se conservará para tu entorno de desarrollo con Linux.

Para este problema tendrías dos soluciones:

- Crear una nueva conexión segura generando otro par de llaves.
- Copiar las mismas llaves que usas en Windows.

En este tutorial voy a explicar como hacer la segunda opción.

### Copiar llaves SSH a WSL

Las llaves ssh en Windows están usualmente guardadas en una carpeta oculta llamada .ssh dentro de la ruta `c:\Users\<username>\`. Nuestro objetivo es copiar esa carpeta completa de Windows hacia nuestro subsistema de Linux.

Para hacer esto debes abrir tu terminal (la que configuraste para correr Linux) y verificar si la carpeta `.ssh` existe en tu root. Para chequearlo debes usar el siguiente comando:

```bash
ls -a ~
```

Si no ves la carpeta .ssh por ninguna parte entonces puedes utilizar el siguiente comando:

```bash
cp -r /mnt/c/Users/<username>/.ssh ~/.ssh
```

Recuerda que debes sustituir "username" por tu nombre de usuario en Windows.

En caso de que la carpeta exista, tienes que verificar su contenido, si dentro ves algún arhcivo llamado `id_rsa` o `id_rsa.pub`, significa que ya tienes un par de llaves generadas para su WSL, por lo que tendrías es que configurar tu conexión segura a GitHub usando esas llaves que ya tienes disponible.

**Nota imortante**: Si ya tienes un par de llaves creadas no copies las de Windows. Esto las sobreescribirá y a menos que estés seguro para qué generaste esas llaves esto puede ser problemático.

En caso de que la carpeta esté vacía, puedes ejecutar el siguiente comando para copiar tus llaves de Windows a tu subsistema Linux:

```bash
cp -r /mnt/c/Users/<username>/.ssh/. ~/.ssh
```
Ya completados estos pasos tendrás listas tus credenciales para usarlas en tu terminal configurado para trabajar con Linux. Pero aún queda un paso más y es arreglar los permisos en el archivo de las llaves.

![Screenshot de error en termianl](/img/screenshots/ssh-sharing-2.webp)

### Arreglando permisos

Para arreglar estos permisos lo que tendrías que hacer es correr el siguiente comando:

```bash
chmod 600 ~/.ssh/id_rsa
```

Una vez arreglado este detalle, ya tendrás listo todo para conectarte a GitHub utilizando las mismas llaves ssh que utilizas en Windows.