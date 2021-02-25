
# Composición de música basada en imágenes
## Contenidos
* [Acerca del sistema](#acerca-del-sistema)
    * [Reglas](#reglas)
    * 	 [Red neuronal](#red-neuronal)
    * 	 [Salida](#salida)
* [Instalación](#instalacion)
* [Uso](#uso)
* [Futuro](#futuro)
* [Contacto](#contacto)
### Acerca del Sistema
En este repositorio se encuentra la sección del proyecto que trabaja con el reconocimiento de imágenes. También se puede encontrar un Demo que se presentó en la clase de inteligencia artificial en el semestre de primavera 2020, el cual muestra funcionalmente lo que hará el sistema completo (aunque la música generada no sea muy agradable).
El programa es una combinación entre un sistema de reglas y un sistema con una red neuronal convolucional (CNN por sus siglas en inglés). 
#### Reglas
Utilizando un algoritmo de k medias se identifican los 7 colores más dominantes de la foto tomada. Estos colores determinan la frecuencia con la que encontraremos las 8 notas musicales (do, re, mi, fa, sol, la, si). Adicionalmente, se obtiene el promedio del valor de brillo utilizando la propiedad de matiz (hue) en el espacio de color HSV para determinar la velocidad de la música (bpm).










#### Red neuronal
![enter image description here](https://i0.wp.com/www.aprendemachinelearning.com/wp-content/uploads/2018/11/CNN-08.png?resize=943,563)

La red neuronal recibe la imagen de la cámara y determina cuál de las siguientes situaciones identifica en la foto:
 1. Sala
 2. Recamara
 3. Vegetación
 4. Cuerpos de agua
 5. Carreteras
 6. Afuera de un edificio o casa
 7. Rascacielos
#### Salida
Según la situación que detecte el sistema en la foto, le asignará un tipo de música (la lista de tipos aún no está definida).
Correr el archivo ImRecon nos permitirá obtener los valores para brillo, colores más frecuentes y situación, los cuales serán utilizados en la siguiente parte del programa, la de composición musical.
### Instalación
 1. Descarga el repositorio, ya sea clonado con Git  o directo desde GitHub
 2. Sube los archivos a tu [Google Drive](https://drive.google.com) 
El proyecto fue realizado en [Google Colab](https://colab.research.google.com), por lo que es necesario su uso para correr el programa.

#### SI SOLO SE QUIERE USAR EL DEMO PUEDE SALTARSE ESTA SECCIÓN 
Este proyecto requiere el uso de la librería [pyfluidsynth](https://github.com/nwhitehead/pyfluidsynth), la cual no es compilable en windows, por lo que se utiliza Google Colab.
Es necesario tener el [modelo](https://drive.google.com/drive/folders/1tJfhjIgRzItVO2fdiFFnRpYFyeiLEZ6Z?usp=sharing) utilizado en la red neuronal en tu [Google Drive](https://drive.google.com) y cambiar la dirección en el notebook a la que le asignes.
Es importante que la dirección asignada sea para la carpeta "my_model".
Como está escrito en el programa:
```python
model = tf.keras.models.load_model('/content/drive/My Drive/Proyecto IA/Model/saved_model/my_model')
```
Si se extrae el zip en tu drive sin carpetas adicionales:
```python
model = tf.keras.models.load_model('/content/drive/My Drive/Model/saved_model/my_model')
```
### Uso
#### Demo
Para ver el demo solo es necesario tener una cámara conectada a tu PC. Deberás compilar los métodos de arriba a abajo haciendo click en la esquina superior izquierda de cada sección de código (el ícono de reproducir).
Este programa reproducirá la música generada a partir de la foto que se toma. Además, podrás ver en una imagen las notas que se generaron en el archivo MIDI para hacer la pieza musical.
#### ImRecon
Para ver la versión más reciente del reconocimiento de imágenes del sistema utilizaremos el archivo "ImRecon.ipynb".
Seguiremos el mismo proceso de compilar las secciones de código de arriba a abajo, sin embargo, existen pasos adicionales.
En la primer sección de código tendrás que anclar tu Drive al Workspace de Google Colab.
Al correr el código
```python
#Mount Drive

from google.colab import drive

drive.mount('/content/drive')
```
Obtendrás un link para dar acceso a tu Drive. Es necesario que lo ancles para importar el modelo. Después de dar permiso, copia el código que te proporciona y pégalo en el cuadro de texto.

![alt text](https://github.com/josepe43/Images/blob/main/linkImg.jpg?raw=true)


Después de un tiempo corriendo tendrá el análisis de la imagen e imprimirá algunos de los resultados con el siguiente formato:
![alt text](https://github.com/josepe43/Images/blob/main/image.png?raw=true)

Se imprime la imagen tomada, seguido de 7 cuadros con los colores dominantes de la imagen.
Abajo de los cuadros también se imprime el reporte del proceso de la red neuronal y la clase con la que la red asoció la foto.
### Futuro
Este proyecto aún no está completo. Mientras siga avanzando, este repositorio se actualizará con dichos avances.
### Contacto
Cualquier duda puedes contactarme al correo jguti109@itam.mx
