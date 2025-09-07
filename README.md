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

En este apartado probamos qué tan robusta es la red de Hopfield cuando le damos imágenes modificadas en lugar de las originales. La idea es ver si la red puede "recordar" y reconstruir correctamente la versión aprendida, incluso cuando la entrada tiene errores o está incompleta.
Realicé tres tipos de pruebas:
### 1. Imágenes parcialmente tapadas:
  * Tapamos la mitad de abajo de las 3 respectivas imágenes.

![Imagenes](imagen_2025-09-06_231030043.png)
  * Al reconstruirlas, la red fue capaz de recuperar bastante bien la forma original, demostrando que “rellena” la información faltante a partir de lo que aprendió. Excepto por la última imagen:

![Imagenes](imagen_2025-09-06_231714290.png)
![Imagenes](imagen_2025-09-06_232722530.png)

La conclusión de este punto es que incluso con un 50% de los píxeles tapados, mas de la mitad de las imágenes seguían siendo reconocibles.

### 2. Imágenes con ruido:
  * Introdujimos ruido aleatorio, invirtiendo valores de algunos píxeles.
  * Con niveles bajos de ruido (10% o 30%), la red reconstruyó casi perfectamente las imágenes.
  * Con ruido muy alto (50% o 90%), los resultados fueron mucho peores, porque la entrada ya no se parece a lo aprendido.
    
  Imágenes con 10% de ruido:
  
![Imagenes](imagenes_con_10_de_ruido.png)

  Este es el resultado de la reconstrucción que le aplicó la red a las imagenes que tenían 10% de ruido:

![Imagenes](imagenes_reconstruidas_por_la_red_con_10_de_ruido.png)

  Imágenes con 50% de ruido:

![Imagenes](imagenes_con_50_de_ruido.png)

  Este es el resultado de la reconstrucción que le aplicó la red a las imágenes que tenían 50% de ruido:

![Imagenes](imagenes_reconstruidas_por_la_red_con_50_de_ruido.png)

  Imágenes con 90% de ruido:

![Imagenes](imagenes_con_90_de_ruido.png)

  Este es el resultado de la reconstrucción que le aplicó la red a las imágenes que teniían 90% de ruido:

![Imagenes](imagenes_reconstruidas_por_la_red_con_90_de_ruido.jpg)

  Esto muestra el límite de memoria de la red: puede corregir errores hasta cierto punto, pero no recuperar una imagen que está casi destruida.
