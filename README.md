# Segmentación de pólipos mediante UNET 

## ¿Qué son los pólipos?

Los pólipos son crecimientos anormales de tejidos que con mayor frecuencia parecen pequeños protuberancias planas o pequeños tallos similares a hongos. La mayoría de los pólipos son pequeños y de menos de media pulgada de ancho.

Los pólipos en el [colon](https://www.healthline.com/health/colorectal-polyps) son los más comunes, pero también es posible desarrollar pólipos en lugares que incluyen:

- canal auditivo
- [Cuello uterino](https://www.healthline.com/health/cervical-polyps)
- [Estómago](https://www.healthline.com/health/gastric-cancer)
- [Nariz](https://www.healthline.com/health/nasal-polyps)
- Útero
- Garganta

La mayoría de los pólipos son [benignos,](https://www.healthline.com/health/benign)lo que significa que son no cancerosos. Pero debido a que se deben al crecimiento anormal de las células, con el tiempo pueden volverse malignos, o [cancerosos.](https://www.healthline.com/health/cancer) El médico puede ayudar a determinar si el crecimiento es un pólipo mediante la realización de una [biopsia.](https://www.healthline.com/health/biopsy-polyps) Esto implica tomar una pequeña muestra de tejido y probarlo para la presencia de células cancerosas.



## **La segmentación de pólipos**

Las imágenes con pólipo se dan a un modelo entrenado y nos dará una imagen binaria o máscara. Esta imagen binaria consta de píxeles en blanco y negro, donde el blanco denota el pólipo en la imagen y el negro denota el fondo.

![Sin SS](https://user-images.githubusercontent.com/34296084/110796091-94754600-8245-11eb-8a44-d03820478892.png)

## Qué es la segmentación semántica

**La segmentación semántica** es uno de los desafíos en la investigación de la visión computarizada. Se puede considerar como un problema de clasificación, pero a nivel de píxel porque necesita predecir la etiqueta o clase de cada píxel de una imagen.
La segmentación semántica es una tarea que avanza hacia la comprensión completa de la escena aprendiendo a predecir lo que hay en la imagen. La importancia de la comprensión de la escena radica en sus aplicaciones en el campo de la visión por ordenador, tales como vehículos autónomos, interacción humano-ordenador, robots autónomos, realidad aumentada, sistemas de reconocimiento facial, etc.


## Qué es UNet

La **UNet** es una red neuronal totalmente convolucional que fue desarrollada por **Olaf Ronneberger** en el Departamento de Ciencias de la Computación de la Universidad de Friburgo, Alemania. Fue especialmente desarrollado para la segmentación de imágenes biomédicas.


La segmentación semántica es una tarea que avanza hacia la comprensión completa de la escena aprendiendo a predecir lo que hay en la imagen. La importancia de la comprensión de la escena radica en sus aplicaciones en el campo de la visión por ordenador, tales como vehículos autónomos, interacción humano-ordenador, robots autónomos, realidad aumentada, sistemas de reconocimiento facial, etc.

![unet](https://user-images.githubusercontent.com/34296084/110797935-a657e880-8247-11eb-9e69-abf36a15bfcf.png)

La UNet sigue una arquitectura simétrica con forma de la letra inglesa "U". Es una mejora con respecto a [las redes totalmente convolucionales para la segmentación semántica](https://arxiv.org/pdf/1605.06211.pdf) por Evan Shelhamer, Jonathan Long, Trevor Darrell.

## Estructura de proyecto

El proyecto tiene tres carpetas:

- **CVC-612/:** Consta del conjunto de datos que vamos a usar para este proyecto. Contiene dos subcarpetas: imágenes y máscaras. Como su nombre indica, estas subcarpeta contienen las imágenes y máscaras.
-  **files/:** Esta carpeta se utiliza para almacenar el archivo CSV que contiene toda la información mientras el modelo está entrenando. También almacena el archivo de peso del modelo.
- **results/:** Se utiliza para almacenar los resultados después de realizar predicciones en el conjunto de datos de prueba.

El proyecto también tiene cuatro scripts de python:

- **data.py:** Este archivo contiene el código para cargar el conjunto de datos, leyendo las imágenes y máscaras. También se utiliza para crear una canalización tf.data para el conjunto de datos de entrenamiento, validación y pruebas.
- **model.py:** Este archivo tiene el código de la arquitectura UNet que va a segmentar las imágenes.
- **train.py:** Este archivo ayuda al modelo a entrenar en el conjunto de datos de entrenamiento. También se utiliza guardar el modelo que se utiliza más adelante para realizar predicciones en el dataset de prueba.
- **predict.py:** Una vez finalizado el entrenamiento, este archivo se utiliza para realizar predicciones en el conjunto de datos de prueba.

## Conjunto de datos

CVC-ClinicDB es una base de datos de fotogramas extraídos de videos de colonoscopia. Además de las imágenes, se proporciona la una máscara correspondiente a la región cubierta por el pólipo. Las imágenes contienen diferentes tipos de pólipos y puede ser descargada desde [aquí](https://polyp.grand-challenge.org/CVCClinicDB/).

![gtcvc1](https://user-images.githubusercontent.com/34296084/110801290-1320b200-824b-11eb-8b65-e4512b27b631.png)
