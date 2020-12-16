---
title: "Cómo usar un gestor de contraseñas"
slug: "gestor-de-contrasena"
author: "Bernardo Ayala"
type: "posts"
date: 2020-06-23
draft: false
categories: ["Tutoriales"]
tags: ["contraseñas", "seguridad"]
icon: "/img/icons/password.png"
---

Anteriormente publiqué una [guía para crear contraseñas más seguras](/crear-una-contrasena-segura) en donde compartí algunas buenas y malas prácticas al momento al momento de crear una contraseña.

Entre los puntos que mencioné existen dos a destacar:

- Las buenas contraseñas son largas y difíciles de recordar.
- Jamás debes usar la misma contraseña dos veces.

Como tenemos cuentas en tantos portales distintos, y nos resulta imposible recordar las claves de todos, los gestores de contraseñas nos ofrecen recordarlas por nosotros a cambio de que recordemos una sola contraseña maestra que desbloqueará a todas las demás.

En esta guía te explicaré cómo instalar y configurar Bitwarden, que es el gestor que estoy utilizando actualmente, pero los pasos no son muy distintos en los otros programas que existen, así que si quieres probar otro lo que aprendas aquí te servirá.

Lo primero es ir a la página de [Bitwarden](https://bitwarden.com/) y antes de instalar nada lo primero que debes hacer es crear una cuenta seleccionando donde dice "Create account".

![bitwarden-homepage](/img/screenshots/bitwarden-homepage.webp)

Eso te llevará a un formulario que tendrás que rellenar. Es muy importante que la contraseña que utilices en el campo "Master Password" sea bastante fuerte pero que a la vez puedas recordarla con facilidad.

Un consejo que puedo darte es que escribas alguna oración, por ejemplo: "La empanada de queso es sagrada".

![bitwarden-login](/img/screenshots/bitwarden-singup.webp)

Completado este paso ya tendrás una cuenta y puedes empezar a almacenar tus contraseñas en tu "vault", que es el depósito donde estarán guardadas. Imagínatelo como una caja fuerte virtual donde estarán todas tus credenciales.

![bitwarden-login](/img/screenshots/bitwarden-login.webp)

A pesar de que ya puedes empezar a usar Bitwarden desde su versión web, resulta mucho más útil y práctico instalar la extensión de navegador para poder guardarlas automáticamente una vez inicies sesión así como también tener acceso a tus credenciales desde cualquier sitio web. Para esto debes volver a la página principal de Bitwarden y darle click al botón que dice "Install Now".

![bitwarden-homepage2](/img/screenshots/bitwarden-homepage2.webp)

Esto te va a llevar a la sección de descargas. Puedes instalar Bitwarden en windows pero a mi me resulta más útil instalar la extensión del navegador. Así que en la sección donde dice "Web browser" elige el navegador que usas. En este ejemplo elegiremos Google Ghrome.

![bitwarden-download](/img/screenshots/bitwarden-download.webp)

Una vez instalada la extensión te va a aparecer el símbolo de Bitwarden a la derecha de la barra de direcciones. Al darle click te va a desplegar una ventana en la cual deberás ingresar tu correo y contraseña maestra.

![bitwarden-plugin-extension](/img/screenshots/bitwarden-extension-login.webp)

¡Listo!, ya puedes empezar a guardar tus contraseñas en Bitwarden. Lo mejor es que no tienes que hacerlo a mano. Cada vez inicies sesión en un portal, la extensión te preguntará si quieres guardar tus credenciales en tu vault.

Cuando cierres el navegador, también se cerrará la sesión del gestor. Esto es una medida de seguridad extra para que nunca lo dejes abierto sin querer. Para volver a iniciar sesión lo único que tienes que hacer es darle click a la extensión y escribir tu contraseña.

### Cómo almacenar y utilizar tus passwords

Una vez que inicias sesión se abre una ventana donde tendrás acceso a todas tus credenciales. En esa pantalla inicial, en la esquina superior derecha, hay un símbolo de más (+).

Dándo click ahí puedes agregar tus credenciales. Lo recomendable es hacerlo cuando estés en la página web de la cual quieras guardar tus datos (twitter por ejemplo), para que Bitwarden automaticamente asocie esa página web con tu usuario y contraseña.

![bitwarden-save-password](/img/screenshots/bitwarden-add-password.webp)

Ahí lo único que tendrías que hacer es rellenar el formulario con tu nombre de usuario y contraseña, y después darle "Save". La idea de que hagas esto en la página que corresponde a tus credenciales es que Bitwarden rellena automáticamente la sección "url" del formulario y esto más adelante va a permitir que puedas utilizar la función de auto-rellenar.

Otra opción más sencilla para guardar tus credenciales es ingresar a algún portal como lo harías normalmente, si tu vault está abierto la extensión te preguntará "deseas que Bitwarden guarde tus datos" a lo que puedes responder "hell yeah, that's why I'm paying you".

![bitwarden-save-credntials](/img/screenshots/bitwarden-extension-save-credentials.webp)

Ahora la próxima vez que entres al portal Bitwarden detectará que tienes un password guardado para el sitio. Al darle click a la extensión te mostrará las credenciales correspondientes, a las cuales tendrás que darle click para que se auto rellenen.

Quien me conoce sabe que amo los shortcuts, y todo este proceso de auto rellenado puede hacerse con una combinación de teclas, lo único es que tienes que darle click al primer campo del formulario y luego presionar "control + shitf + L".

![bitwarden-autofill](/img/screenshots/bitwarden-autofill.gif)

### Cómo utilizar el generador de contraseñas

Otra de las ventajas de usar gestores es que vienen con un generador de contraseñas seguras que suele ser bastante bueno. Uno puede ajustar la complejidad al nivel que quiera y como el gestor se encarga de recordar cualquier locura que genere no tenemos que preocuparnos por memorizarlo.

Para utilizar este generador nuevamente tienes que hacer click a la extensión y en la ventana que se abre debese ir a la parte inferior y darle click a la opción que dice "Generator".

![bitwarden-password-generator](/img/screenshots/bitwarden-password-generator.webp)

Esto nos generará un password aleatorio bastante fuerte al cual podremos agregar o restar complejidad moviendo las opciones disponibles. Una vez estés conforme con el resultado puedes copiar el password y utilizarlo para lo que lo necesites. Si necesitas almacenarlo puedes hacerlo de cualquiera de las dos formas que te expliqué arriba.

![bitwarden-password-generator2](/img/screenshots/bitwarden-password-generator2.webp)

### Conclusiones

Con esta guía espero que te resulte más sencillo animarte a utilizar un gestor de contraseñas. Para mi son imprescindibles. Además de [Bitwarden](https://bitwarden.com/), existen múltiples opciones que podrías probar para ver cual se adapta mejor a tus necesidades.

Algunos otros de los más conocidos son:

+ [LastPass](https://www.lastpass.com/es)
+ [1Password](https://1password.com/es/)
+ [KeePass](https://keepass.info/)

El primer paso para proteger tu vida digital es utilizar una buena contraseña y como estas son tan difíciles de recordar, un buen gestor de contraseñas será tu mejor amigo.