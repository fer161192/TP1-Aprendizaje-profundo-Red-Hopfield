# TP1-Aprendizaje-profundo-Red-Hopfield
Pequeña pero breve introducción: Este proyecto implementa una red neuronal de Hopfield, un tipo de red recurrente que se utiliza como memoria asociativa. Básicamente, la red puede ‘recordar’ patrones a partir de ejemplos, incluso cuando los recibe incompletos o con ruido.

![Enunciado TP 1](imagen_2025-09-06_014827567.png)

Resolución:
## 1 - a) Verificación del aprendizaje. La red recuerda lo que aprendió?
En esta sección, cargamos 3 imágenes simples (paloma, perro y panda):

![Imagenes](imagen_2025-09-06_023525787.png)

A cada imagen la transformamos en blanco y negro y la convertimos a un formato que la red puede procesar (una secuencia de valores -1 y 1, en lugar de pixeles comunes).

Luego, entrenamos la red de Hopfield con estas imágenes: Básicamente construimos una matriz de conexiones entre las neuronas que guarda la “memoria” de cada patrón.

La prueba fue la siguiente:

* Le volvimos a mostrar a la red exactamente las imágenes que había aprendido.
  
* Si la red había memorizado correctamente, al procesarlas no debía modificarlas.
  
* En otras palabras, debía devolver la misma imagen que se le dio como entrada.
  
Resultado: Todas las imágenes fueron recordadas correctamente: la red devolvió la misma que se le había enseñado.
Esto significa que la red realmente aprendió esos patrones y puede almacenarlos en su “memoria asociativa”.

## 1 - b) Evaluación de la red con imágenes alteradas
