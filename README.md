# Clasificador de tipos de carnes

TÉCNICA DE PROCESAMIENTO

En el código proporcionado, se utilizó una técnica básica de procesamiento de imágenes llamada "normalización". Esta técnica se implementa utilizando el generador de datos ImageDataGenerator de la biblioteca Keras. La normalización es un paso común en el preprocesamiento de imágenes, y su objetivo es escalar los valores de los píxeles de la imagen a un rango específico. En este caso, se utilizó la normalización dividiendo cada valor de píxel por 255.0, lo que lleva a que todos los valores de píxeles estén en el rango de 0 a 1. En ambos generadores de datos (entrenamiento y test), se utiliza el parámetro rescale=1./255. Esto divide cada valor de píxel por 255.0 para normalizar los valores de píxeles en el rango de 0 a 1. Esta normalización ayuda a que el modelo converja más rápidamente durante el entrenamiento y a que las imágenes sean comparables en términos de intensidad de píxeles. Además de la normalización, también se aplicó el redimensionamiento de las imágenes al tamaño especificado utilizando el parámetro target_size en los generadores de datos.


MODELO
El clasificador utilizado en el código proporcionado usa un modelo de red neuronal convolucional (CNN). A continuación se describe el modelo:

Capa de entrada: La primera capa de la red define la forma de entrada de los datos. En este caso, se especifica input_shape=(image_size[0], image_size[1], 3), lo que indica que se esperan imágenes en formato RGB con las dimensiones especificadas.

Capas convolucionales: A continuación, se agregan capas convolucionales Conv2D que extraen características de las imágenes mediante la aplicación de filtros convolucionales. En el código, se utiliza una capa convolucional con 32 filtros y una función de activación ReLU.

Capas de agrupamiento (pooling): Después de las capas convolucionales, se agregan capas de agrupamiento MaxPooling2D que reducen la dimensionalidad espacial de las características extraídas, conservando las características más relevantes.

Capa de aplanamiento: Se añade una capa Flatten para transformar la salida de las capas anteriores en un vector unidimensional, preparándolo para las capas densamente conectadas.

Capas densamente conectadas: A continuación, se agregan capas densamente conectadas Dense que aprenden a mapear las características extraídas a las clases de salida. En el código, se utiliza una capa densa con 128 unidades y una función de activación ReLU.

Capa de salida: La última capa Dense tiene un número de unidades igual al número de clases en el conjunto de datos (que se obtiene de train_data.num_classes). Utiliza una función de activación softmax para producir una distribución de probabilidad sobre las clases de salida.

Compilación del modelo: Antes de entrenar el modelo, se compila utilizando el optimizador Adam, la función de pérdida categorical_crossentropy (adecuada para problemas de clasificación multiclase) y se especifica la métrica de precisión.

Entrenamiento del modelo: Se entrena el modelo utilizando el método fit en los datos de entrenamiento generados por el generador train_data.

En resumen, este clasificador utiliza una arquitectura CNN para aprender características y patrones en las imágenes de entrenamiento y clasificarlas en las diferentes clases. La combinación de capas convolucionales, capas de agrupamiento y capas densamente conectadas permite que el modelo aprenda de manera jerárquica y capture características discriminativas en las imágenes para la clasificación.


