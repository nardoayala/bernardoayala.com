---
title: "Cómo instalar última versión de Node en Ubuntu"
slug: "instalar-ultima-version-node"
author: "Bernardo Ayala"
type: "posts"
date: 2020-08-19
draft: false
categories: ["Tutoriales"]
tags: ["linux","node"]
icon: "/img/icons/nodejs.png"
---
Cuando tratas de instalar la última versión de node en Ubuntu utilizando el apt-package manager te consigues con que la versión que se instala es la 10.x.x. Esa es la última versión disponible en los repositorios de Ubuntu, pero no es la última versión de Node.

En este tutorial mostraré cómo podemos instalar la última versión disponible ya, sea actualizando el repositorio donde apt-get obtiene node o a través de Node Version Manager (NVM).

## Actualizando repositorio (Instalar Nodesource)

Para lograr esto tienes que ejecutar el siguiente comando en la consola:

```bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```

Puedes remplazar el `14` por la versión que prefieras instalar. Al momento de escribir este post la `14` es la última versión estable.

### Instalar nodejs con apt-get package

Una vez configurada la nueva Nodesoruce, puedes instalar node con el siguiente comando:

```bash
apt-get install -y nodejs
```

Si ya tenías una versión previa instalada, se actualizará.

Una vez finalizada la instalación, para chequear que todo haya salido bien puedes chequear la versión de node instalada utilizando el comando `nodejs -v` .

Automáticamente deberías tener también la última versión de npm, para chequearlo puedes usar el comando `npm version` , en caso de que no tengas la última versión puedes actualizarla utilizando el comando `npm install -g npm@latest`.

Si por cualquier motivo no se instaló npm y no te corre el comando para revisar la versión, puedes instalarlo manualmente ejecutando:

```bash
sudo apt-get install -y npm
```

## Utilizando NVM

Este método tiene la ventaja de que puedes tener varias versiones de node instaladas y utilizar la que necesites para cada proyecto. Es una forma de tener más control

Lo primero que tienes que hacer es instalar NVM, para eso utiliza el siguiente comando:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

Para chequear que NVM se instaló correctamente ejecuta el comando `nvm --version`y deberías ver la versión instalada. Si esto falla, es posible que no se haya agregado nvm al perfil de tu terminal de forma automática. Puedes agregarlo manualmente con el siguiente comando:

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

Si todo está correcto, reinicia tu terminal.

### Instalar nodejs con NVM

Lo único que tendrías que hacer es ejecutar el siguiente comando con la versión de node que quieras instalar:

```bash
nvm install 12.18.3
```

Si alguna vez necesitas utilizar alguna otra versión de node que tengas instalada puedes hacerlo utilizando el siguiente comando: `nvm use <version-number>`

Para listar todas las versiones que tengas instaladas puedes utilizar el siguiente comando: `nvm ls`

Independientemente de cual método elijas utilizar, a este punto ya tendrás instalada la última versión de nodjs así como de npm.
