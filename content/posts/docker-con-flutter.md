---
author: "Yulianny Betancourt"
title: "Docker Con Flutter"
date: 2020-12-23T00:17:32-04:00
description: "Contenedor de Docker para Flutter"
tags: ["Docker", "Flutter", "Flutter Web", "Emulador para Flutter"]
---

## Contenedor de Docker para Flutter

Recientemente estaba con la urgencia de hacer un proyecto con Flutter, pero los recursos de la PC no me dejaban, por lo cual empece a buscar alternativas y di con este contenedor, e intentando usarlo no podía hacer que funcionara el emulador, solo en web y era tardío el proceso, entonces empece a investigar y eran cosas sencillas que tenía que hacer para que todo funcionara que para otros pueden ser más sencillas o complejas, y por lo mucho que me ha ayudado, se los dejo aquí para que puedan solventar cualquier problema solamente teniendo Docker en su pc/laptop, VSCode, y una extensión en este.

Gracias a la maravilla de Docker, con este contenedor podrás hacer tus prácticas y proyectos de Flutter sin preocuparte de las configuraciones en tu PC/Laptop.

### Este contenedor incluye:

- SDK Flutter.
- SDK Android.
- Emulador para Android.
- Configuración para Flutter Web en el puerto 8090.
- Varias versiones de Flutter.


### Ahora sí, empecemos con la instalación.

Clonamos el repositorio desde la Terminal. Es importante no cerrar la terminal con la que estaremos trabajando desde afuera de VSCode, que la estaremos utilizando más adelante

` $ git clone https://github.com/yuliannydev/docker-flutter-multiplatform.git `

Entramos al repo clonado, desde la misma terminal

` $ code . `

Para instalar la extensión que dije que se necesita en VSCode, [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack). Una vez instalada:

` Ctrl + Shift + P `

![RemoteDevelopmen1t](docs/assets/img/vsc-remote.png)

Le damos en **Remote-Containers: Rebuild and Reopen in Container**

Para que se descargue todo el contenido que necesitaremos para trabajar con Flutter en nuestra PC, esto puede demorar un tiempo dependiendo de tu conexión a internet, ya que como dije estará descargando todo.

Y una vez esté descargado en la **terminal de VSCode** aparecerá algo así:

![FlutterApp](docs/assets/img/app.png)

Donde flutter_docker_compose es el nombre que le hayas dado inicialmente al repo clonado, o como tú quieras llamarle. Lo siguiente será crear nuestra Aplicación:


![FlutterCreate](docs/assets/img/app1.png)


Ahora para poner andar el emulador Android necesitas tener soporte para [KVM](https://www.linux-kvm.org/page/Main_Page), en Linux puedes buscar en tu tienda de descarga.

En la terminal externa, que dije que no cerráramos, vamos a colocar este comando, para que inicie el emulador:

` $ xhost local:$USER && docker run --rm -ti -e UID=$(id -u) -e GID=$(id -g) -p 42000:42000 --workdir /project --device /dev/kvm --device /dev/dri:/dev/dri -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY -v "$PWD":/project --entrypoint flutter-android-emulator  matspfeiffer/flutter `

Ahora en la **terminal de VSCode**

` $ flutter emulators --launch flutter_emulator `

Para trabajar en un Navegador Web con Chrome se debe tener esta extensión para depurar Dart:

[Extension-Dart](https://chrome.google.com/webstore/detail/dart-debug-extension/eljbmlghnomdjgdjmbdekegdkbabckhm)

Y igualmente correr un comando en la Terminal externa:

` $ docker run --rm -ti -e UID=$(id -u) -e GID=$(id -g) -p 42000:42000 -p 8090:8090  --workdir /project -v "$PWD":/project --entrypoint flutter-web matspfeiffer/flutter:beta `

Y empezará a trabajar en el puerto 0.0.0.0:8090

**Gracias por visitar mi Blog, y espero haberte ayudado. Para cualquier duda puedes contactarme a mi Twitter y con gusto te ayudaré**
