---
layout: post
title:  "Primera entrada"
date:   2019-04-01
desc: "Primera entrada"
keywords: "Jekyll, Ruby"
categories: [Personal, Youtube, Web]
tags: [Jekyll, Ruby]
icon: icon-html
---

En éstos días he decidido tener mayor presencia en red de alguna forma u otra. Había pensado en crear un canal de Youtube y todavía pienso hacerlo pero por lo mientras creo es más fácil ahorita tener un blog.

Quiero escribir sobre las cosas que hago que tal vez a otra persona le pueda servir que puede ser de Unity, C#, Python, git, etc.

Para todo ésto, tuve que ver como es ésto del Jekyll y [Github Pages](https://pages.github.com). Me pareció perfecto para lo que necesitaba por que solo ocupo Git para hacer actualizaciones a la página web. Fue un poco difiícil la instalación eso sí. 

Ocupo una Mac y para la página se requires Ruby y Jekyll. Para instalar Ruby ocupé Homebrew que es un Package Manager para Mac, pero al parecer el Ruby instalado de aquí es un poco diferente. Al final lo más fácil fue instalar los entornos virtuales de Ruby con rbvenv.

> `brew install rbenv`

> `curl -fsSL [github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor](https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor) | bash`

> `rbenv install 2.6.2`

> `rbenv global 2.6.2`

Y seguir el [tutorial](https://jekyllrb.com/docs/installation/) dado por Jekyll.

Antes de ejecutar rbenv install tuve que modificar el archivo /Users/<nombre>/.bash_profile y agregar

> `eval "$(rbenv init -)"`

> `export PATH="$HOME/.rbenv/bin:$PATH" `

Ésto lo que hace es que se inicialize el entorno virtual de ruby cuando se inicia la terminal y se obtenga las gemas de Ruby para llamarlas directo.

Y bueno, encontré esta [página](http://jekyllthemes.org) con temas de Jekyll, escogí uno, hice un fork del repositorio y lo modifiqué para crear este blog.

Para escribir esta primera publicación, estoy ocupando Agenda para Mac. Esperemos que funcione bien.





