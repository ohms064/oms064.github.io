---
layout: post
title:  "Trabajo con Magic Leap"
date:   2019-05-04
desc: "Primer proyecto con Magic Leap"
keywords: "Magic Leap, Unity, C#"
categories: [Unity, C#]
tags: [Unity, C#]
icon: icon-unity
---
# Magic Leap -- May 4, 2019


# Trabajo con Magic Leap

Ahora me tocó trabajar un proyecto de unos minijuegos para Magic Leap. Realmente no he usado el dispositivo físico pero afortunadamente existe el simulador con el cual he podido trabajar, aunque no he la mejor manera. Espero poder probar con el dispositivo pronto. 

Voy a escribir un mini-tutorial de cómo lo he utilizado hasta ahora y cómo hice el setup además de compartir algunas ligas de interés.

Todo lo que mencione se puede consultar en la documentación oficial [aquí](https://creator.magicleap.com/learn/guides/get-started-developing-in-unity).


## Instalación de Magic Leap

Para poder instalar el SDK, hay que instalar el **Magic Leap Package Manager** desde [aquí](https://creator.magicleap.com/downloads/lumin-sdk/overview) o [aquí](https://forum.magicleap.com/hc/en-us/community/posts/360042443051-Getting-Started-With-Lumin-SDK-0-20-0-and-Unity-2019-1?flash_digest=26179e9fab1d87f98ce73778e6f86c97d5dff396&flash_digest=26e75ae8e101281cacbc18aa7d88938a6704454d), se te pide crear una cuenta para poder ocuparlo. Una vez hecho ésto, iniciamos sesión en el programa y descargamos el Lumin SDK y el paquete de Unity. Desde aquí podemos seleccionar el Lumin SDK y abrir la carpeta donde se realizó la instalación, esto será importante más adelante.


## Instalación de Unity

Para usar Magic Leap necesitamos forzosamente descargar **Unity 2019.1** o posterior. Existe una versión de Unity 2018 con el preview técnico de Lumin pero este es una versión aparte de Unity y se ocupaba una versión anterior del SDK. Sólo mencionaré que existe más no diré cómo ocuparlo.


## Creación del proyecto de Unity

Abrimos un proyecto de Unity y primero debemos indicar la ubicación del Lumin SDK (similar a Android), podemos buscarla o podemos abrirla desde el Magic Leap Package Manager y copiar la dirección que nos abra. En Unity abrimos **(Windows) Edit/Preferences/External Tools (Mac) Unity/Preferences/External Tools **y habrá una nueva sección que nos pide la ubicación del SDK de Lumin, pegamos la dirección que obtuvimos anteriormente y listo.

En Build Settings veremos un nuevo target llamado Lumin, cambiamos nuestro Build Target a éste.

También desde el **Package Manager** debemos instalar_ “XR Legacy Input Helpers”_,esto es un paquete legacy así que tal vez en el futuro no se ocupe pero para esta versión sí se ocupa.

Ahora nos pasamos a **Edit/Project Settings** y en **Other Settings** en la pestaña de **Lumin** cambiamos el** Color Space **a _“Linear”_, verificamos que estemos ocupando en **Scripting Runtime Version **la versión _.Net 4.x_ y en **XR Settings** debemos activar** Virtual Reality Supported**, checar que se esté ocupando Lumin como SDK y verificar que** Stereo Rendering Mode **está puesto a _“Single Pass Instanced”_. 

Del **Magic Leap Package Manager** abrimos el paquete de Unity y lo importamos a nuestro proyecto. En este paquete vienen varias escenas de prueba donde podemos ver cómo se ocupan los diferentes Inputs y sensores del Magic Leap.

Desde nuestro proyecto debemos copiar el archivo **manifest.xml** ubicado en **Assets/MagicLeap/Examples/Plugins/Lumin** y pegarlo a **Assets/Plugins/Lumin**, hay que crear esa ubicación si no existe.

Finalmente, desde la raiz de nuestro proyecto abrimos **Package/manifest.json **desde el explorador de archivos (nótese que no es el mismo que el del paso anterior) y agregamos 

> "registry": "https://packages.unity.com"

Esto debe ir a la raiz del json.


## Simulador y correr el juego desde el editor

Para ocupar el simulador de Magic Leap hay que hacer unas configuraciones adicionales como indica [aquí](https://creator.magicleap.com/learn/guides/sdk-play-mode-in-unity-with-ml-remote).

Para **Mac** hay que tener instalado** Apple XCode command line tools**. Ejecutamos en la terminal lo siguiente:

> _xcode-select --install_

De vuelta de **Project Settigns/Other Settings** en la pestaña de **Standalone**, desactivamos _Autographics API _ y en la lista agregamos OpenGLCore si no está y lo penmos como primer elemento.

Luego abrimos **Magic Leap/ML Remote/Import Support Libraries**, esto es un proceso independiente entre los diferentes sistemas operativos así que si por ejemplo lo tenemos en un repositorio compartido de **git** y alguno tiene Windows y otro Mac cada quien deberá hacer este paso. 

Una vez terminado el procesos anterior abrimos **Magic Leap/ML Remote/Launch MLRemote**, esto abrirá otra ventana donde podemos seleccionar **Start Simulator **o **Start Device**, si tenemos el dispositivo conectado podemos seleccionar el segundo pero podemos ocupar el simulador con el primero, esperamos a que inicie y ¡listo! podemos correr nuestro juego en el simulador y así probar el **Magic Leap**.


## Datos adicionales

Podemos cargar cuartos de prueba desde el minimapa con el botón azul de la esquina superior izquierda.

Si Unity no detecta el simulador, cerramos Unity y lo volvemos abrir. A veces es necesario tener corriendo el simulador antes de Unity.

