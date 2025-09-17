# Práctica 1 de VC (Visión por Computador)

## Autores
María Cabrera Vérgez
<br>
Leslie Liu Romero Martín

## Tareas realizadas

Durante la primera práctica de la asignatura, se hará uso de OpenCV con sus funciones de dibujo, entre otros, para mostrar una imagen a tiempo real, señalar píxeles, etc. No se ha necesitado ninguna instalación adicional. Las tareas en cuestión son:

1. Crear una imagen con la textura de un juego de ajedrez.
2. Crear una imagen estilo Mondrian.
3. Hacer uso de las funciones de dibujo de OpenCV.
4. Modificar un plano de la imagen.
5. Destacar tanto el píxel con el color más claro como con el color más oscuro de una imagen.
6. Hacer una propuesta pop art con la entrada de la cámara web o vídeos.

## Instalación
Será necesario tener instalados los paquetes cv2, numpy y matplotlib.pylot.

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
## Tareas

### 1. Crear una imagen con la textura de un juego de ajedrez.

Para poder elaborar el tablero, será necesario definir sus dimensiones, es decir, su ancho y alto. Para la tarea, estos datos dan lugar a un rectángulo de 800x800. Para darle un color de fondo al rectángulo, se usará función np.

```
black_img = np.zeros((alto, ancho, 1), dtype= np.uint8)
```

La función usada devuelve un nuevo array con el tamaño y tipo dado. Se le indica uint8 para indicar que es un tipo de dato que puede almacenar entre 0 y 255 (cosa que será usado cuando vayamos dando color a cada imagen). También se indica los canales, siendo en este caso solo 1.

Para el tablero, usaremos dos bucles for para poder movernos entre cuadrados de 100x100, formando cada parte del tablero solicitado. Se cogera la parte entera de las coordenadas y se irá revisando si es par o no para ir alternando entre los dos colores primarios del tablero: blanco y negro. Por ejemplo, el primer cuadrado irá en el eje y de 0 a 100 y así cada vez.

```
if (x//100 + y//100) % 2 == 0:
            black_img[y:y+100, x:x+100] = 255
        else:
            black_img[y:y+100, x:x+100] = 0
```

Al ir alternando entre colores, finalmente da la imagen buscada, mostrándola con la función plt.imshow(). Se trata de una función de matplotlib.pylot que nos permite ver la imagen en cuestión.

<img width="425" height="418" alt="image" src="https://github.com/user-attachments/assets/b061eda4-4bee-4557-a57f-318e53d942ed" />


### 2. Crear una imagen con estilo Mondrian.

La segunda tarea consiste en crear una imagen con el estilo Mondrian. Se trata de un estilo que muestra un cuadro en dos dimensiones, sin mostrar profundidad en este. Se conforma de cuadrados o rectángulos con diferentes colores, separados por líneas rectas. Como las líneas presentan un color negro, se ha optado por crear un fondo de este color e ir pintando encima suyo los píxeles que sean necesarios. Para el primer cuardrado pintado se indicaron las medidas, por ejemplo:

```
black_img[0:600,250:ancho, 0] = 255 #tercer índice especifica un canal (0-2)
```

Lo que se hace es señalar que se pintará de un cuadrado que vaya en el eje y de 0 a 600, en el eje x de 250 al total del ancho. El canal usado será el 0 (RGB), igualando esto a 255 para que se vea el color rojo pedido. Así se irá haciendo con el resto de figuras, indicando los canales que sean necesarios para que cada uno tengo el color solicitado. Para el blanco se pondrá a 255 cada uno de los canales, mientras que en amarillo se podrá dejar el último canal a 0. Para representar el color azul, solo será necesario su canal, el 2.

Se tiene que dejar una pequeña separación entre figuras para dar forma a las líneas que están presente en el cuadro original.

<img width="425" height="418" alt="image" src="https://github.com/user-attachments/assets/58520cf3-3204-4719-a3b4-e34c5dcf25ba" />


