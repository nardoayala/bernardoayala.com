---
title: "Cómo crear un blog con Hugo"
slug: "crear-blog-con-hugo"
description: "Tutorial para crear un blog con Hugo y hacerle deploy en Netlify"
author: "Bernardo Ayala"
type: "posts"
date: 2021-05-09
draft: true
categories: ["Tutoriales", "Desarrollo web"]
tags: ["hugo"]
icon: "/img/icons/hugo.png"
---

[Hugo](https://gohugo.io/) es un generador de páginas estáticas construido con GO, un lenguaje de programación que se caracteriza por su velocidad, la cual hace que el mismo Hugo sea bastante veloz.

La ventaja de que tu sitio web sea estático es que puedes alojarlo prácticamente en cualquier parte, incluso en servicios como GitHub pages o Netlify que te permiten hacerlo de forma gratuita, y en todo caso tendrías que invertir en un nombre de dominio nada más si así lo deseas.

## Descargar e Instalar Hugo

![Hugo Logo](/img/hugo-logo-wide.svg)

Dependiendo de tu sistema operativo hay distintas formas de instalar Hugo, puedes descargar los archivos binarios y copiarlos donde quieras utilizarlo, pero yo prefiero instalarlo a través de gestores de paquetes, así que voy a explicarte cómo hacer eso según tu sistema operativo.

### Chocolatey (Windows)

Puedes usar [Chocolatey](https://chocolatey.org/) como tu gestor de paquetes. En el link que te dejé puedes ver las instrucciones para instalarlo en si le das click al botón de **Get Started**.

Una vez tengas Chocolatey, instalar Hugo es tan sencillo como correr este comando en tu powershell:

```bash
choco install hugo -confirm
```

O si quieres la versión extendida de Hugo que, entre otras ventajas, te permite trabajar con SASS puedes correr el siguiente comando:

```bash
choco install hugo-extended -confirm
```

Para verificar que la instalación haya sido correcta puedes correr este comando para ver qué versión de Hugo tienes instalada:

```bash
hugo version
```

### Homebrew (Mac y Linux)

En el caso de Mac y Linux, puedes utilizar [Homebrew](https://brew.sh/). Dentro de la página principal puedes conseguir las instrucciones de instalación, pero es tan sencillo como correr este comando dentro de tu terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Una vez hecho esto, puedes instalar Hugo con el siguiente comando:

```bash
brew install hugo
```

Igual que en Windows, para verificar que la instalación haya sido exitosa, puedes correr el siguiente comando y chequear qué versión de Hugo tienes instalada:

```bash
hugo version
```

## Crear nuevo proyecto

Crea un directorio dónde quieras tener almacenado los archivos de tu proyecto, podría ser una carpeta llamada `projects`, esto depende de cómo prefieras organizar tus archivos.

Una vez creada esta carpeta ejecuta el siguiente comando para crear un nuevo sitio con Hugo:

```shell
hugo new site blog-personal
```

Donde escribí "blog-personal" puedes elegir el nombre que quieras. Una vez que Hugo termine sus procesos, navega dentro de esa carpeta:

```shell
cd blog-personal
```

¡Listo!, ya creaste tu primer proyecto.

## Instalar un tema

Puedes crear temas para tu blog desde cero, pero en principio lo más fácil es escoger alguno de los que estén disponibles en el repositorio oficial de [temas](https://themes.gohugo.io/). Para este tutorial voy a instalar [Hugo Vitae](https://themes.gohugo.io/hugo-vitae/) como ejemplo.

Estos son los pasos para instalar un tema:

1. Dentro de la carpeta de tu proyecto navega hasta la carpeta de los temas: `cd themes`.

2. Clona el repositorio del tema con git: `git clone https://github.com/dataCobra/hugo-vitae.git`

3. Los temas incluyen una carpeta llamada `exampleSite` que trae la configuración básica para los sitios con contenido de prueba. Lo más sencillo para empezar es copiar todo el contenido de esta carpeta dentro de la carpeta raíz de tu proyecto, en este caso `blog-personal`, e ir borrando y editando a partir de ahí.

4. Una vez copies el contenido de `exampleSite` ya puedes correr tu proyecto para ver cómo se ve corriendo el comando `hugo server`.

   ![Example site screenshot](/img/screenshots/hugo_example.webp)

## Crear contenido

Las publicaciones en Hugo se guardan en formato [markdown](https://markdown.es/), que es una forma de escribir html de forma sencilla. Si no sabes cómo utilizarlo te recomiendo que lo aprendas, es bastante sencillo.

Para crear un nuevo post, primero tienes que ver cómo se llama la carpeta donde se guardan los posts dentro de la carpeta `content`. En el caso del exampleSite de Hugo Vitae, la carpeta se llama `post`.

Sabiendo esto, corre el siguiente comando dentro de la carpeta raíz de tu proyecto:

```shell
hugo new post/nuevo-post.md
```

Esto generará un archivo base para que empieces a escribir tu post:

![Example post screenshot](/img/screenshots/hugo_example-post.webp
 )

Esa parte de arriba es dónde escribes la metadata. En este caso solo tenemos título, fecha y un boolean llamado borrador; pero puedes agregar otras.

Yo te recomiendo que en principio, además de esas tres, agregues `categories` y `tags`, de forma que la metadata de tu post quedaría así:

```yaml
---
title: "Nuevo Post"
date: 2021-05-08
categories: ["Tutoriales"]
tags: ["hugo","blog"]
draft: true
---
```

Lo que aparece por defecto como metadata al momento de crear nuevas publicaciones puedes editarlo modificando el archivo `default.md` dentro de la carpeta `archetypes`.

Para ver cómo está quedando tu publicación puedes correr el comando `hugo server -D`, esa `-D` lo que le indica es que quieres que te muestre los posts que están marcados como draft. Al momento de publicar tu artículo recuerda cambiar el parámetro `draft` a `false`.

## Configuraciones extra

Dentro de la carpeta principal de tu blog, existe un archivo `config.toml` que es el que tiene todas las configuraciones de tu proyecto.

![Example config file screenshot](/img/screenshots/hugo_example-config.webp)

En principio te va a parecer un poco complicado de entender pero a medida que te vayas familiarizando con Hugo verás que es bastante intuitivo y gran parte de lo que puedes modificar aquí está bien documentado.

El primer parámetro a modificar es `baseURL`, que debería ser tu nombre dominio. Recuerda incluir el http o https al principio y terminar con un `/`.

Lo siguiente a modificar son los parámetros que personalizan el tema. Como por ejemplo el nombre del blog, la descripción, el autor, alguna imagen que quieras usar como avatar y tus redes sociales.

## Hacer deploy en Netlify

Antes que nada, tu proyecto debe estar subido a GitHub. Así que si no lo has hecho ya, inicia un repositorio en la carpeta raíz de tu proyecto con el comando `git init` haz commit de los cambios y luego haz push a tu repo.

Dentro de tu proyecto deberás crear un archivo llamado `netlify.toml` que servirá para establecer la configuración para hacer deploy en Netlify.

Este archivo puede ser un poco complicado de entender y configurar, pero en principio no te preocupes por eso, simplemente copia y pega el siguiente código:

```toml
[build]
publish = "public"
command = "hugo --gc --minify"

[context.production.environment]
HUGO_VERSION = "0.82.0"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"

[context.split1]
command = "hugo --gc --minify --enableGitInfo"

[context.split1.environment]
HUGO_VERSION = "0.82.0"
HUGO_ENV = "production"

[context.deploy-preview]
command = "hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL"

[context.deploy-preview.environment]
HUGO_VERSION = "0.82.0"

[context.branch-deploy]
command = "hugo --gc --minify -b $DEPLOY_PRIME_URL"

[context.branch-deploy.environment]
HUGO_VERSION = "0.82.0"

[context.next.environment]
HUGO_ENABLEGITINFO = "true"
```

El parámetro que en principio deberás prestar especial atención es `HUGO_VERSION`, verifica que coincida con la versión de Hugo que tienes instalada. Puedes verificarlo corriendo el comando `hugo version`.

Una vez hecho esto, deberás crear una cuenta en Netlify yendo a la siguiente dirección: [app.netlify.com](https://app.netlify.com/). Creada la cuenta te aparecerá un dashboard con un botón que dice "New site from Git" al cual debes darle click.

![Netlify dashboard screenshot](/img/screenshots/netlify-add-new-site.webp)