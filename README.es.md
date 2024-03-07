# Análisis y clasificación de textos ilícitos como apoyo para la gestión de espionaje policial

Todos los archivos presentes en este repositorio fueron creados y publicados por Franco Parra para optar al título de Ingeniero Civil en Informática, en la Universidad Técnica Federico Santa María, 2023.

## Objetivo general

Considerando entonces todos los peligros asociados a la falta de herramientas y control parte de los tutores sumados a la exposición desmesurada de los menores en Internet, el propósito de esta memoria será desarrollar un sistema de procesamiento de texto capaz de discriminar sentencias con fines perversos (manipulación, explotación o abuso sexual) hacia menores utilizando un modelo de inteligencia artificial BERT.

## Objetivos específicos

1. Determinar los riesgos existentes en Internet, y así, entender cómo pueden gatillar escenarios de manipulación, explotación o abuso sexual infantil. 
1. Analizar el estado del arte en cuanto a la detección y prevención de *grooming* en Internet para establecer qué fuentes de datos son utilizadas, qué estrategias se emplean durante el procesamiento de los datos y cuáles modelos resultan tener mejores desempeños.
1. Implementar un modelo de inteligencia artificial BERT y ajustar parámetros para adecuarlo al contexto del problema y mejorar la capacidad de generalización.
1. Aplicar solución en casos reales y comentar resultados para corroborar eficacia y futuras mejoras.

## Descripción

En la carpeta `notebooks_with_results` se encuentran los *notebooks* que dieron origen a los resultados descritos en la memoria. Se organizan de manera jerárquica de acuerdo a la fase, así, `notebooks_with_results/phase_1` alude a la primera fase, mientras que `notebooks_with_results/phase_2`, la segunda. 

En `notebooks_with_results/phase_1` encontramos un único directorio: `notebooks_with_results/training`. Existen 12 archivos en total, cada uno, encargado de afinar BERT. Están nombrados a través del siguiente formato: `<batching_size>BS_<message_batching_size>MBS_<learning_rate>LR_<epochs>E`. Sus significados son los siguientes:

1. `<batching_size>` es el tamaño del lote a usar durante el entrenamiento de BERT.
1. `<message_batching_size>` es el tamaño del agrupamiento de los mensajes. 
1. `<learning_rate>` es la tasa de aprendizaje inicial.
1. `<epochs>` es el número de *epochs* (iteraciones) a realizar durante el entrenamiento.

En `notebooks_with_results/phase_2` encontramos dos directorios: `preprocessing` y `hypertuning_training`. En `notebooks_with_results/phase_2/preprocessing` existe un único *notebook* que utiliza los resultados de la primera fase para obtener las atenciones de BERT. El nombrado utiliza las mismas convenciones anteriores. 

Por otro lado, en `notebooks_with_results/phase_2/hypertuning_training` existen 4 archivos en total, cada uno, encargado de hiperafinar y entrenar la arquitectura encargada de detectar conversaciones sospechosas. Están nombrados a través del siguiente formato: `<batching_size>BS_<message_batching_size>MBS_<learning_rate>LR_<epochs>E_<seed>S`. Sus significados son los siguientes:

1. `<batching_size>` es el tamaño del lote a usar durante el entrenamiento de BERT.
1. `<message_batching_size>` es el tamaño del agrupamiento de los mensajes. 
1. `<learning_rate>` es la tasa de aprendizaje inicial.
1. `<epochs>` es el número de *epochs* (iteraciones) a realizar durante el entrenamiento.
1. `<seed>` es la semilla para controlar la aleatoriedad.

## Continuación del trabajo

Con el fin de recrear estos modelos localmente para continuar con la investigación, se define la carpeta `notebooks_as_templates`, la cual contiene 3 *notebooks*:

1. `phase_1_training.ipynb`: Afina el modelo BERT.
1. `phase_2_preprocessing.ipynb`: Obtiene las atenciones del modelo entrenado en `phase_1_training.ipynb` y genera un nuevo conjunto de datos.
1. `phase_2_hypertuning_training.ipynb`: Afina y entrena la arquitectura encargada de detectar conversaciones sospechosas.

La carpeta `inputs` contiene una plantilla de todas las entradas en los 3 *notebooks*, mientras que `outputs`, sus salidas. Es importante notar que **no se adjunta el conjunto de datos `PAN2012`**. Esto se debe a que es de carácter privado, sin embargo, a través de [este](https://zenodo.org/record/3713280) hipervínculo, se puede enviar un correo para solicitar su obtención.

> Todos los *notebooks* fueron modificados para aceptar archivos locales, pues muchos de ellos estaban en la nube de Kaggle.