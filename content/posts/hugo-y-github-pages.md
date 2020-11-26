---
author: "Yulianny Betancourt"
title: "Hugo y Github Pages"
date: 2020-11-25T22:34:08-04:00
description: "Crea una página Web en tiempo récord"
tags: ["Hugo", "Github", "DesarrolloWeb"]
---



#### **Crea tu Página Web o Blog con Hugo + Github Pages en solo minutos.**

Hugo es un Framework de código abierto que te permite crear Sitios estáticos, y actualmente es el más veloz del mercado.

####  **Instala HUGO en tu Sistema Operativo**

Primero es necesario tener instalado en tu PC o Laptop hugo, porque ahí es donde iniciaras tu proyecto. Para eso:

En Windows:

`$ choco install hugo -confirm`

En MAC:

` $ brew install hugo`

Debian y derivados:

` $ sudo apt-get install hugo`

Arch Linux y derivados:

` $ sudo pacman -S hugo`

#### **Crear tu Proyecto con Hugo**

` $ hugo new site MiPagina`

Crea una carpeta llamada **MiPagina** en la cual estará tu Proyecto, y quedará algo así:

![](https://i.imgur.com/d29YHm1.png)

#### **Instala tu tema y configuralo**

Puedes hacerlo desde cero, pero gracias a la comunidad de Hugo, existen diversos temas con los cuales puedes hacer tu página partiendo de otra o si quieres dejarla exactamente igual, acá un link donde puedes conseguir temas:

https://themes.gohugo.io/

El tema que yo he elegido es este:

https://themes.gohugo.io/theme/hugo-refresh/

Ahora adentro de la carpeta **MiPagina** se prepara para poder subir a Github, y clonar el repositorio del tema ahí, esto se hace así:

` $ git init`

Clonamos el tema con un:

` $ git submodule add https://github.com/PippoRJ/hugo-refresh.git themes/hugo-refresh`

Y adentro de la carpeta Themes estará el tema clonado como lo indica el comando anterior.

Y para tener el tema tal cual lo muestra en la demo, removemos la configuración de la carpeta raíz. El archivo config.toml

![](https://i.imgur.com/cyNpVzg.png)

` $ rm config.toml`

y descargamos la configuración del tema clonado, a nuestra carpeta raíz con:

`$ curl -O https://raw.githubusercontent.com/PippoRJ/hugo-refresh/master/exampleSite/config.yaml`

Para esto se requiere tener instalado curl, si no lo tienes puede entrar a la carpeta **themes** luego en el tema clonado, y **exampleSite** copiar el archivo config.toml y pegarlo en la carpeta raíz, es decir en **MiPagina**.

En el archivo config.toml es necesario cambiar el link que trae por defecto que es:

`baseURL = "http://example.com/"` y colocar el link de tu página web, este link lo obtienes en el siguiente paso, recuerda hacerlo una vez lo hayas terminado.


#### **Crea un repositorio en Github para alojar tu proyecto, Página web, Blog**

Para este paso necesitas tener una cuenta en Github, así que si estás aquí es porque ya sabes que puedes alojar tu página web ahí.

En Github, en el inicio a la izquierda superior:

![](https://i.imgur.com/STX32zR.png)

Le das en New y apareceran la ventana para colocar los datos del repositorio:

![](https://i.imgur.com/g832nty.png)

En **Repository name** colocarás el nombre con el que tengas tu cuenta

"tunombre" es eso.

Y **.github.io** para que esto pueda funcionar, y los otros datos son opcionales, pero deberías llenarlo.

#### **Clonar mi repositorio Github a mi PC**

Como ya en tu pc creaste un repositorio al hacer ` $ git init` tienes que utilizar estos comando en la terminal:

` $ git remote add origin https://github.com/yuliannybetancourt/tunombre.github.io.git`

En tu caso será `https://github.com/tunombre/tunombre.github.io.git` la dirección del repo.

` $ git branch -M main`

` $ git push -u origin main`

Recuerda estar posicionado adentro de la carpeta **MiPagina**

Y tu repositorio Github ya estará enlazado a tu proyecto local en la rama **main**

#### **Preparo mi Proyecto para subirlo a Github**

Ahora para que tu proyecto en local esté en tu cuenta de Github, y puedas tener tu Página Web:

Estando en **MiPagina**

` $ hugo new -d docs`

Esto es para que se cree una carpeta docs adentro de la raíz de tu proyecto local, y de ese modo en tu repositorio se haga el deploy en docs.

**Nota:**  Github te permite tener tu página web en la raíz **/root**, pero en este caso la colocaremos en **/docs **, para eso vamos a Settings en Github y bajamos al apartado de **Github Pages** y seleccionamos /docs como lugar para hacer el deploy.

![](https://i.imgur.com/39IsUmd.png)

Ya preparado el proyecto en local, y configurado bien el repositorio, en la terminal:

` $ git add .`
` $ git commit -m "Subo mi proyecto completo a Github"`

Esto es para agregar los cambios realizados "*la carpeta docs y lo que contiene*"

` $ git push origin main`

Sube todo el proyecto a tu respositorio en Github.

Y listo, ya puedes verificar que tu página está en https://tunombre.github.io
