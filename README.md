# Ejercicios Procesamiento de Lenguaje Natural
**Especialización en Inteligencia Artificial (CEIA) - UBA - Cohorte 16 (2024)**

![LogoFIUBA](./logoFIUBA.pdf)


En este repositorio se encuentran las soluciones implementadas para los desafíos prácticos de la asignatura de Procesamiento de Lenguaje Natural, como parte del Posgrado en Inteligencia Artificial (CEIA) de la Facultad de Ingeniería de la UBA.

**Alumno:**  Santiago Jose Olaciregui- N° SIU: a1611

## Desafío 1: Comparación de Similaridad entre Documentos
En este ejercicio, se desarrolló un enfoque para analizar la similitud entre diversos documentos del conjunto de datos *20 Newsgroups*, utilizando varias técnicas:

- **Transformación de documentos en vectores y cálculo de similaridad:** Mediante el método TF-IDF, se representaron los documentos como vectores numéricos en un espacio de características. Luego, se calculó la similaridad entre un documento de referencia y los cinco documentos más cercanos usando la métrica de coseno, con el fin de explorar si los documentos similares provienen de la misma categoría.
  
- **Modelos de clasificación con Machine Learning:** Para abordar la clasificación de los documentos, se emplearon modelos de Naive Bayes (Multinomial y ComplementNB). La optimización de los hiperparámetros se realizó mediante una búsqueda aleatoria para obtener la mejor puntuación en la métrica F1 macro en el conjunto de prueba.
  
- **Medición de similitudes entre palabras:** Se seleccionaron cinco palabras para analizar sus similitudes semánticas, utilizando el mismo proceso de vectorización para encontrar las palabras más cercanas en el espacio vectorial.

El código para este desafío está disponible en:  
[GitHub - Desafío 1](https://github.com/santiolaciregui/NLP/blob/main/Desafio%201%20/Desafio_1.ipynb)

## Desafío 2: Estudio de Similaridad con Word2Vec
Este desafío se centró en el análisis de sentimientos utilizando el conjunto de datos *Stanford Sentiment Treebank 2* (SST-2), que contiene frases cortas extraídas de reseñas de películas. Las tareas que se realizaron son las siguientes:

- **Análisis de la relación entre palabras:** Se eligieron cinco palabras clave y se utilizó el modelo Word2Vec para examinar la similaridad semántica entre ellas y otras palabras en el espacio de vectores, con el objetivo de obtener una comprensión más profunda de sus relaciones contextuales.

El código para este desafío está disponible en:  
[GitHub - Desafío 2](https://github.com/santiolaciregui/NLP/blob/main/Desafio%202/TP2_NLP.ipynb)

## Desafío 3: Creación de Texto Automático con LSTM a partir del libro *Economia comestible - HaJoon Chang*
Para este desafío, se diseñó un modelo LSTM para generar texto automáticamente, entrenado con el contenido del libro *Economia comestible*. Los pasos clave en este proceso fueron:

- **Preprocesamiento de datos:** Se extrajo el texto del archivo *Economia comestible - HaJoon Chang.pdf*, segmentando el contenido en palabras y convirtiéndolas en índices numéricos utilizando un Tokenizer. Luego, el conjunto de datos fue dividido en dos partes: una para entrenamiento y otra para validación, aplicando *padding* para que todas las secuencias tuviesen la misma longitud.
  
- **Entrenamiento del modelo LSTM:** El modelo desarrollado emplea una arquitectura secuencial que incluye capas de embeddings y LSTM. Los embeddings de 16 dimensiones convierten las palabras en vectores densos. A continuación, se utilizaron dos capas LSTM de 32 unidades cada una para aprender las relaciones temporales entre las palabras. Se implementó también una capa de *dropout* para reducir el sobreajuste. Finalmente, se añadió una capa densa con activación *softmax* para predecir la siguiente palabra en una secuencia, permitiendo así la generación de texto.

El código para este desafío está disponible en:  
[GitHub - Desafío 3](https://github.com/santiolaciregui/NLP/blob/main/Desafio%203/TP3_NLP.ipynb)


## Desafío 4 : Bot de Preguntas y Respuestas (QA) con LSTM
Este desafío se centra en la construcción de un modelo de **Pregunta y Respuesta** (*Question Answering*, QA) utilizando un enfoque de **encoder-decoder** basado en LSTM, con el objetivo de desarrollar un **ChatBot** que responda preguntas en función de un dataset específico.
Pasos principales del desarrollo:

- **Preparación del dataset:**  
  Se descargó y procesó el dataset `data_volunteers.json`, que contiene pares de preguntas y respuestas. Los datos fueron preprocesados convirtiendo las oraciones en secuencias numéricas con un **tokenizador** para las entradas y salidas del modelo.

- **Diseño del modelo QA:**  
  El modelo sigue la arquitectura **encoder-decoder**:
  - **Encoder:** Usa una capa LSTM para codificar la secuencia de la pregunta.
  - **Decoder:** Una capa LSTM generó la respuesta palabra por palabra, basada en las salidas del encoder.
  - **Embeddings preentrenados:** Se usaron **embeddings GloVe** para representar las palabras como vectores.

- **Entrenamiento del modelo:**  
  - **Inputs:** Secuencias de preguntas y respuestas procesadas.
  - **Parámetros clave:**  
    - 256 unidades en las capas LSTM.
    - Optimización con el optimizador Adam, tasa de aprendizaje inicial de 0.01.

- **Inferencia:**  
  El modelo se separó en dos componentes:
  - **Encoder para inferencia:** Codifica la pregunta y genera un estado interno.
  - **Decoder para inferencia:** Genera la respuesta utilizando el estado generado por el encoder y las palabras anteriores producidas por el decoder.

- **Resultados:**  
  - El modelo entrenado genera respuestas a preguntas utilizando el estado codificado por el encoder y el decoder.

El código para este desafío está disponible en:  
[GitHub - Desafío QA](https://github.com/santiolaciregui/NLP/blob/main/Desafio%204/Desafio_4.ipynb)

