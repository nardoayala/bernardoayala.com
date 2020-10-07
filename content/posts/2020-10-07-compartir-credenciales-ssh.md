---
title: "Compartir Credenciales SSH de Windows a WSL"
slug: "compartir-ssh-widnows-wsl"
author: "Bernardo Ayala"
type: "posts"
date: 2020-10-07
draft: true
categories: ["Programación"]
tags: ["terminal","configuraciones","wsl","ssh"]
icon: "/img/icons/terminal.png"
---

Una vez tengas configurado tu distribución de Linux dentro de Windows 10 a través de WSL te vas a conseguir con el problema de que al momento de querer conectarte a GitHub para hacer push o pull de alguno de tus repositorios no vas a tener los permisos para hacerlo.

Esto es debido a que las configuraciones que tenías en tu ambiente de desarrollo con Windows no se conservarán para tu entorno de desarrollo con Linux.

En el caso de las credenciales SSH tendrías dos alternativas, una sería la de crear nuevas credenciales para este nuevo ambiente de desarrollo, y la otra alternativa sería la de compartir las credenciales que usas en Windows a tu subsistema de Linux. En este tutorial explicaré como hacer la segunda opción.

### Copiar llaves SSH a WSL

Las credenciales ssh en Windows están usualmente guardadas en una carpeta oculta llamada .ssh dentro de la ruta `c:\Users\<username>\`. Nuestro objetivo es copiar esa carpeta completa de Windows hacia nuestro subsistema de Linux.

Para hacer esto debes abrir tu terminal (la que configuraste para correr Linux) y ejecutar el siguiente comando:

```bash
cp -r /mnt/c/Users/<username>/.ssh ~/.ssh
```

Recuerda que debes sustituir "username" por tu nombre de usuario en Windows. Ya hecho esto tendrás listas tus credenciales para usarlas en tu terminal configurado para trabajar con Linux. Pero aún queda un paso más y es arreglar los permisos en el archivo de las llaves.

### Arreglando permisos

Para arreglar estos permisos lo que tendrías que hacer es correr el siguiente comando:

```bash
chmod 600 ~/.ssh/id_rsa
```

Una vez arreglado este detalle ya tendrás tus credenciales funcionando dentro de tu WSL.