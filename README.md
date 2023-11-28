# Project_7_ML

![tendencias-sector-inmobiliario](https://github.com/luisgh87/Project_7_ML/assets/116723919/ad336873-8f48-453c-982b-27c34a926d4f)


# Introducción

Este proyecto tiene como objetivo abordar una pregunta clave para viajeros y anfitriones por igual: ¿cuánto debería costar una estancia en una ubicación específica en los EE. UU.? Al aprovechar técnicas avanzadas de análisis de datos y machine learning, nos sumergiremos en un océano de variables, desde la ubicación geográfica y las comodidades del alojamiento hasta las tendencias del mercado y eventos locales.

La capacidad de predecir con precisión los precios no solo beneficia a los viajeros al planificar su presupuesto, sino que también brinda a los anfitriones una visión estratégica para establecer tarifas competitivas y atractivas. Este proyecto no solo es una exploración de datos, sino una puerta abierta a la optimización de experiencias de viaje y a un mercado de alojamientos más transparente y eficiente.

Acompáñanos en este viaje analítico mientras desentrañamos patrones, identificamos factores clave y creamos un modelo predictivo robusto que ilumine el fascinante universo de los precios de Airbnb en los Estados Unidos. ¡Bienvenidos a un futuro donde cada viaje es una experiencia aún más personalizada y accesible! 🌍🏡✨

# Data Cleansing

1. Examinamos los dataframes de train y test.
2. Buscamos una alta correlación entre las variables numéricas para evitar problemas de multicolinealidad y overfitting, pero no se aprecian en el heatmap. Sólo entre la "latitud" y la "longitud", pero ambas serán necesarias y complementarias.
3. Covertimos a valores numéricos todas las columnas de valor para nuestro modelo predictivo con la ayuda de LabelEncoder y One Hot Encoding. Desechamos las que no aportan nada.
4. Tratamos de clusterizar en agrupaciones de un máximo 10 valores distintos los datos de las columnas numéricas, sirviendo esto para reducir el ruido centrándonos en las características principales y simplificar el modelo.
5. Descomponemos la columna "amenities" en otras nuevas en proporción a su numero y las integramos a los dataframes para facilitar su posterior interpretación.
6. Aunque carecemos de un gran número de missing values, los rellenaremos con la moda de los valores de sus respectivas series.
7. Para finalizar el proceso de limpieza de datos, daremos el mismo orden y número de columnas al train y al test, necesario esto para un correcto entrenamiento de los datos.

# Entrenamiento y predicción

Para el relizamiento de estas tareas hicimos uso de tres modelos de entrenamiento:

1. LinearRegression
2. Decision Tree Regressor
3. Random Forest Regressor

Éste último fue el que mejores resultados predictivos para los precios de los establecimientos ofrecidos por Airbnb nos ofreció. Puede que por los siguientes motivos:

- Random Forest puede ser más adecuado para capturar patrones complejos o relaciones no lineales en los datos.
- Mitiga mejor el problema de overfiting al promediar las predicciones de varios árboles, lo que puede resultar en un modelo más robusto y generalizable que Decision Tree.
- Random Forest tiene la capacidad inherente de manejar características relevantes al construir árboles con subconjuntos aleatorios de características. Esto puede ser beneficioso cuando tienes un conjunto de datos con muchas características, algunas de las cuales pueden no ser informativas para la tarea de regresión.
- Es un algoritmo más robusto frente a outliers en comparación con Linear Regression. Los árboles de decisión no se ven tan afectados por valores atípicos y pueden adaptarse mejor a la variabilidad en los datos.
- No hace suposiciones estrictas sobre la distribución de los datos, a diferencia de Linear Regression, que asume una relación lineal entre las variables independientes y dependientes.
- Random Forest tiende a ser más fácil de usar y generalmente requiere menos ajuste de hiperparámetros, simplificando el proceso de modelado y aumentar la probabilidad de obtener buenos resultados sin mucha afinación.

# Observaciones

- Decidimos no normalizar el dato con Standard Scaler o MinMaxScaler porque no daba los resultados esperados, empeorando el modelo.
- Conseguimos mejorar el resultado a posterioiri eliminando la columna "id". A pesar de ser numérica, tenía un efecto categórico que empobrecía la predicción,
