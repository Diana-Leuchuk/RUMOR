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

Se empleó CountVectorizer para convertir los textos en representaciones numéricas basadas en la frecuencia de palabras.
Se limitaron a 10.000 características (palabras únicas) para optimizar el rendimiento y evitar sobreajuste.

Se utilizó una Regresión Logística (Logistic Regression) por ser un modelo interpretable, rápido de entrenar y muy adecuado para tareas de clasificación binaria.
El conjunto de entrenamiento se dividió en 80% para entrenamiento y 20% para validación.

El modelo se evaluó mediante:

Accuracy: mide el porcentaje de aciertos globales.

F1-score: evalúa el equilibrio entre precisión y exhaustividad, especialmente útil en clases desbalanceadas.

Ambas métricas permitieron validar la efectividad del modelo antes de aplicarlo al dataset de prueba.

Finalmente, el modelo entrenado se aplicó al dataset_test.csv y se generó la columna etiqueta, con valores 0 o 1 según la predicción.
El archivo se exportó en formato CSV, conservando las columnas ID y etiqueta.

El modelo logró un rendimiento sólido (accuracy y F1-score satisfactorios) y cumple con todos los requerimientos del desafío:
Limpieza de datos y entrenamiento supervisado con regresión logística.

Métricas de desempeño.

Generación del archivo final con predicciones.
