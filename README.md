# Investigación e implementación de cámara de seguridad en Raspberry Pi 3 B y Jetson Nano 2 GB Developer Kit
### Trabajo de Fin de Grado de Javier Solís García

## Descripción

Este proyecto es un fork en el que se ha mezclado recursos de los proyectos [EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi](https://github.com/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi), [Cartucho/mAP](https://github.com/Cartucho/mAP) y scripts propios para hacerlos compatibles y extenderlos.

Concretamente, durante la realización de mi proyecto se ha buscado encontrar la mejor configuración entre dispositivo y modelo, siendo finalmente esta la combinación del dispositivo Jetson Nano 2 GB Developer Kit y el modelo SSD MobileNet V1. Para llegar a la conclusión mencionada, se han evaluado los modelos sobre el conjunto test del [INRIA person dataset](https://bit.ly/2QYHnkN).

Dentro de este proyecto se encuentra el código y archivos necesarios para ejecutar los modelos SSD MobileNet V1 y  EfficientDet-Lite0; además de los scripts necesarios para que se pueda ejecutar en una Rapberry Pi 3 B, que se encuentran en la rama [master](https://github.com/javsolgar/TFG), y los archivos necesarios para que se pueda ejecutar en una Jetson Nano 2 GB Developer Kit, encontrandose dichos archivos en la rama [jetson](https://github.com/javsolgar/TFG/tree/jetson).

## Resumen de los comandos disponibles

En cuanto a los comandos disponibles y sus funciones, a continuación se encuentran detallados:

1. Ejecutar carga del dataset:
```python3 load_data.py --path=<path>```
   - ruta al directorio que contiene la carpeta test de INRIA person dataset.


2. Realizar inferencia sobre las imágenes de un dataset:
```python3 TFLite_detection_image.py --modeldir=<path_model> --image=<path_images>/* (--evaluate=True)```
   - path_model = ruta al directorio que contiene el modelo que se quiere utilizar.
   - path_images = ruta al directorio con las imágenes que se generaron al ejecutar el script load_data.py.
   - evaluate = argumento opcional, se añade si se desea ejecutar la evaluación au-tomáticamente tras acabar la inferencia.
 
3. Realizar evaluación:
```python3 evaluate.py (-na) (-np)```
   - na = argumento opcional para eliminar animación, donde se muestra en cada imagen la posición del objeto real comparado con la predicción generada.
   - np = argumento opcional para que no se muestren las gráficas generadas al acabar la evaluación.
   
4. Realizar detección en tiempo real con cámara:
```python3 TFLite_detection_webcam.py --modeldir=<path_model>```
   - path_model = ruta al directorio que contiene el modelo que se quiere utilizar.
