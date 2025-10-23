# RUMOR
El propósito de este proyecto fue construir un modelo de Machine Learning capaz de determinar si una publicación corresponde a un rumor (1) o no rumor (0), utilizando como base el texto de la publicación y atributos asociados al usuario y al tema.

El modelo final debía generar un archivo dataset_test.csv con una nueva columna llamada etiqueta, que contuviera las predicciones sobre el conjunto de prueba.
El archivo resultante fue luego subido a la plataforma Ranking de modelos para evaluar su rendimiento.

Se trabajó con dos archivos CSV provistos:

dataset_train_val.csv → Datos con etiqueta (is_rumor), usados para entrenamiento y validación.

dataset_test.csv → Datos sin etiqueta, sobre los cuales se generaron las predicciones finales.

Luego se eliminó y descató todas las filas del DataFrame df que tienen valores vacíos o nulos (NaN) en la columna topic.
Se decidió usar exclusivamente la columna text como entrada del modelo.
Esto se debe a que el objetivo principal es identificar rumores a partir del contenido semántico del mensaje, sin depender del usuario o del tema, que podrían introducir sesgos.

El conjunto de datos se divide en: 75% entrenamiento (x_train, y_train) y 25% prueba (x_test, y_test)

random_state=42 se usa para mantener resultados reproducibles.
La variable text representa las entradas (lo que el modelo lee).
La variable topic representa las salidas (lo que el modelo debe aprender a predecir).

Como los algoritmos de Machine Learning no pueden procesar texto directamente, se utiliza CountVectorizer para convertir las palabras en valores numéricos (frecuencias de aparición).
Este proceso genera una matriz de características que representa cada publicación como un conjunto de números.
Se entrena un modelo de Regresión Logística, una técnica clásica y efectiva para problemas de clasificación.
El modelo aprende a asociar los patrones de palabras (vectorizadas) con los distintos temas (topic).
El modelo se evaluó mediante: Accuracy: mide el porcentaje de aciertos globales y F1-score: evalúa el equilibrio entre precisión y exhaustividad, especialmente útil en clases desbalanceadas.

Ambas métricas permitieron validar la efectividad del modelo antes de aplicarlo al dataset de prueba.

Finalmente, el modelo entrenado se aplicó al dataset_test.csv y se generó la columna etiqueta, con valores 0 o 1 según la predicción.
El archivo se exportó en formato CSV, conservando las columnas ID y etiqueta.

El modelo logró un rendimiento sólido (accuracy y F1-score satisfactorios) y cumple con todos los requerimientos del desafío:
Limpieza de datos y entrenamiento supervisado con regresión logística.

Métricas de desempeño.

Generación del archivo final con predicciones.
