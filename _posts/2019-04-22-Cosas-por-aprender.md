---
layout: post
title:  "Nuevas cosas por aprender"
date:   2019-04-22
desc: "Cosas que actualmente estoy aprendiendo"
keywords: "Jekyll, Ruby"
categories: [Personal, Unity]
tags: [Unity, Progrmación]
icon: icon-unity
---

# Cosas por aprender -- Apr 22, 2019

Hace unos días me topé con un tema que me pareció bastante interesante, los llamados Compute Shaders y son shaders que funcionan con tipos de datos más genéricos a diferencia a los que conocemos que solo trabajan con pixeles y con gráficos. Esto nos permite hacer operaciones en paralelo gracias al GPU.


# Compute Shaders

Para poder escribir Compute Shaders es necesario conocer cómo funciona nuestra tarjeta de video  y cómo se organizan los procesos.

No seré muy técnico con los nombres pero lo intentaré explicar.

Un shader como el que conocemos tiene un proceso muy bien definido, cuando este programa llega a la tarjeta de video, éste tiene un componente que categoriza qué proceso se hará y se le asignan los procesadores necesarios. Para un Compute Shader esto no sucede así y nos pasamos directamente al uso de los procesadores y usarlos como nos convenga.

Estos “procesadores” se les llaman hilos (threads) para el Compute Shader y a su vez éstos están organizados en grupos de hilos (thread group), esto hace que se organizen en una matriz de seis dimensiones. Para un Compute Shader podemos tener varios thread groups que tendrán un arreglo de threads.

Cada Compute Shader debe tener al menos un kernel, que básicamente es una función dentro del shader que recibe algunos parámetros especiales y viene acompañado con la definición del thread group como sigue 
```
_numthreads[8,8,1]_
_void Main(uint3 id : SV_DispathThreadId) { … }_
```
Los valores dentro de numthreads dependen mucho de lo que querrámos hacer y no he encontrado mucha información de en qué basarnos para escogerlos, pero en este caso estaríamos definiendo una matriz 2D normal de 8x8. Esto es el arreglo de los hilos para cada threadgroup. La variable que se recibe “id” contiene el thread actual en el que estamos. Hay varios argumentos que podemos recibir pero este es el default.

Para llamar a esta función desde C# se hace declarando la clase ComputeShader, lo asignamos en el editor y en el código ejecutamos 
```c#
_sh ader.Dispatch( kernel, 4,4,1);
```
Lo que se define aquí es la cantidad de threadgroups y en qué configuración, en este caso es una matriz 2D de 4x4. Entonces tenemos una matriz de thread groups de 4x4x1 que a su vez contiene threads ordenados en una matriz de 8x8x1. El primer argumento kernel es el id del kernel que queremos llamar.

Anexo algunas ligas que me parecieron útiles:

[YouTube video (9RHGLZLUuwc)](https://www.youtube.com/watch?v=9RHGLZLUuwc) Video incial donde me interesé por el tema

[YouTube video (0DLOJPSxJEg)](https://www.youtube.com/watch?v=0DLOJPSxJEg&t=2159s) Video más técnico donde explican como funcioan el GPU

[anteru.net/blog/2018/intro-to-compute-shaders/](https://anteru.net/blog/2018/intro-to-compute-shaders/) Aquí igual explican el funcionamiento del GPU

[www.khronos.org/opengl/wiki/Compute_Shader](https://www.khronos.org/opengl/wiki/Compute_Shader) Wiki 

