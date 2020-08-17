---
title: "Cómo utilizar la terminal de Linux en Windows 10"
slug: "instalar-wsl"
author: "Bernardo Ayala"
type: "posts"
date: 2020-08-04
draft: false
categories: ["Programación"]
tags: ["linux", "wsl", "terminal"]
icon: "/img/icons/linux.png"
---

Uno de los puntos débiles de Windows respecto a Linux o Mac es que no cuenta con una buena línea de comandos (aunque han hecho muy buenos esfuerzos con PoweShell).

Sin embargo, existe una forma de poder utilizar la terminal de Linux dentro de Windows. Esto podemos lograrlo a través del <abbr title="Windows Subsystem for Linux">WSL</abbr>, que básicamente nos permite instalar una distribución de Linux dentro de Windows.

En esta guía voy a listar los pasos para instalar el WSL y configurarlo; explicaré como instalar ZSH y voy a mostrar como instalar la nueva Windows Terminal para utilizarla como nuestra nueva línea de comandos.

### Habilitar el modo desarrollador

Abre el menú de configuración de Windows 10, bien sea haciendo click en inicio y seleccionando la opción que dice “configuración” o también puedes presionar la combinación de teclas <kbd>Win</kbd> + <kbd>i</kbd>.

![Captura de pantalla](/img/screenshots/windows-settings.webp)

Una vez dentro selecciona la opción que dice “Actualización y seguridad”

![Menú de configuración de Windows](/img/screenshots/windows-settings2.webp)

Luego tienes que seleccionar la opción para desarrolladores y entre las opciones que se muestran debes seleccionar la que dice “activar modo desarrollador”. Te saldrá una advertencia a la cual tendrás que darle si para continuar y luego deberás reiniciar para que se apliquen los cambios.

![Activar modo desarrollador en Windows](/img/screenshots/windows-settings3.webp)

Finalizado este paso deberás reiniciar la computadora.

### Habilitar Windows Subsytem for Linux

Para hacer esto debes seguir los siguientes pasos:
- Abrir el panel de control.
- Seleccionar la opción "Programas".
- Dentro de la opción "Programas y caracteríticas" selecciona la opción que dice "Activar o desactivar características de Windows".

Seguido estos pasos te saldrá la siguiente ventana, donde tendrás que buscar la opción que dice "Subsistema de Windows para Linux" y activarla.

![Activar WSL](/img/screenshots/widnows-features-wsl.webp)

### Instalar y configurar Ubuntu

Puedes elegir entre varias distribuciones, pero en esta guía instalaré Ubuntu. Para ello debes ingresar a la Windows Store y buscarlo. Hay varias versiones, en este caso elegí la que se llama "Ubuntu" sin más. Te recomiendo escoger la misma.

![Windows Store Ubuntu](/img/screenshots/windows-store-ubuntu.webp)

Finalizada la instalación, búsca "Ubuntu" dentro de tus programas instalados e inícialo. Esto abrirá una consola donde se completará la instalación y te pedirá que ingreses un usuario y contraseña para usar dentro de Linux.

![WSL Terminal](/img/screenshots/wsl-terminal.webp)

### Instalar ZSH y Oh-My-Zsh

Para instalar ZSH debes ejecutar el siguiente comando en la terminal:

```bash
sudo apt-get install zsh
```
Al usar el comando `sudo` te pedirá la contraseña que elegiste cuando configuraste tu usurio, debes introducirla para continuar con la instalación.

Para instalar Oh-My-Zsh deberás ingresar el siguiente comando:

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Terminada la instalación te saldrá un mensaje en la terminal pidiendo que confirmes si quieres usar "zsh" como tu terminal por defecto. Deberás confirmarlo escribiendo **Y** y presionando la tecla enter. Seguido de esto te pedirá nuevamente la constraseña de superusuario.

![Usar ZSH por defecto](/img/screenshots/wsl-terminal-oh-my-zsh.webp)

### Instalar y configurar Windows Terminal

Para poder tener una mejor experiencia trabajando con la terminal y poder personlaizarla aún más es recomendable instalar algún emulador de terminal para Windows. En este tutorial instalaremos la nueva Windows Terminal.

Para ello debes ingresar a la Windows Store, buscarla e instalarla.

![Windows Terminal Store](/img/screenshots/windows-store-terminal.webp)

Una vez instalada búscala entre tus programas instalados e iniciala. La terminal por defecto con la que trabaja Windows Terminal es PowerShell. Pero puedes iniciar una nueva terminal seleccionando Ubuntu entre las opciones listadas.

![Terminal new tab ubuntu](/img/screenshots/windows-terminal-ubuntu.gif)

Sin embargo lo ideal sería utilizar la terminal de Linux como nuestra terminal por defecto. Para esto deberás presionar <kbd>Control</kbd> + <kbd>,</kbd>, y asumiendo que tengas VSCode instalado (o algún otro editor), se abrirá el archivo .json de configuración de la terminal.

Al principio de este archivo conseguirás una opcion que dice "defaultProfile"

![Windows Terminal Settings](/img/screenshots/windows-terminal-settings1.webp)

Ese código deberás remplazarlo por el que aparece listado dentro de la propiedad "guid" de la terminal que quieras utilizar por defecto dentro de las terminales que aparecen listadas más abajo.

![Windows Terminal Settings](/img/screenshots/windows-terminal-settings2.webp)

Al guardar los cambios la configuarción ya estará aplicada. La próxima vez que inicies Widnows Terminal se iniciará la terminal de Ubuntu por defecto.

![Windows Terminal Ubuntu](/img/screenshots/windows-terminal-ubutnu.webp)

Ya con esto tendrás instalada y configurada la terminal de Linux dentro de Windows 10.

### Bonus: Actualizar a WSL 2

Para poder utilizar la versión 2 de WSL debes tener Windows 10 actualizado hasta la versión 2004 (como mínimo con la build 19041). Para poder verificar esto puedes presionar las teclas <kbd>Win</kbd> + <kbd>r</kbd> y ejecutar el comando `winver`.

![Windows Version](/img/screenshots/windows-version.webp)

De tener instalada una versión inferior deberás actualizar antes de continuar. Para hacer esto puedes descargar el asistente que ofrece Microsoft en su página para actualizar Windows 10: [Windows Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).

Si ya tienes la última verisón instalada el siguiente paso será habilitar la **Plataforma de máquina virtual** dentro de las características de Windows. Para hacerlo los pasos son los mismos que cuando activaste el **Windows Subsystem for Linx**:

- Abrir el panel de control.
- Seleccionar la opción "Programas".
- Dentro de la opción "Programas y caracteríticas" selecciona la opción que dice "Activar o desactivar características de Windows".

Seguido estos pasos te saldrá la siguiente ventana, donde tendrás que buscar la opción que dice "Plataforma de máquina virtual" y activarla.

![Activar WSL](/img/screenshots/windows-features-virtual-machine.webp)

Deberás **reiniciar** windows para continuar.

Posterior a esto deberás ejecutar PowerShell como administrador. Para hacerlo puedes presionar <kbd>Win</kbd> + <kbd>x</kbd>, se desplegará un menú con opciones y ahí podrás seleccinar "PowerShell(Administrador)" ya sea haciendo click sobre la opción o presionando la tecla <kbd>a</kbd>.

![Activar WSL](/img/screenshots/windows-x-menu.webp)

Dentro de PowerShell deberás ejecutar el siguiente comando:

```PowerShell
wsl --set-default-version 2
```
Puede ser que al momento de ejecutar el comando salga un mensaje que diga `WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel.`, en ese caso deberás ir al enlace ([https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)) y seguir las instrucciones para actualizar el Kernel.

La versión 2 de WSL tiene algunas ventajas como ser notablemente más veloz, pero utilizarla es opcional. Todas las configuraciones que hayas hecho para la versión 1 estarán aplicadas, así que no tendrás que volver a instalar ni configurar desde cero.
