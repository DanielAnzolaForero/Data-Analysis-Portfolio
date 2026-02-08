  # 💻 Laptop Price Predictor: Análisis y Modelado de Regresión

Este proyecto utiliza técnicas de **Data Mining** y **Machine Learning** para predecir el precio de laptops en función de sus especificaciones técnicas. El objetivo es identificar qué componentes de hardware tienen un mayor impacto en el valor de mercado.

---

## 🎯 Objetivo y Pregunta Central
**¿Cuáles son los factores de hardware que más influyen en la determinación del precio de una laptop en el mercado actual?**

El objetivo principal es construir un modelo de regresión capaz de estimar el precio de un equipo con un margen de error mínimo, permitiendo a consumidores y vendedores entender si un dispositivo está "sobrevalorado" o en "oferta".

## 📊 Fuente de los Datos
Los datos fueron obtenidos de [Kaggle](https://www.kaggle.com/datasets/muhammetvarl/laptop-price), un dataset que contiene información detallada de más de 1,300 modelos de laptops, incluyendo marca, tipo, procesador, RAM, almacenamiento, sistema operativo y peso.

## 🧹 Proceso de Limpieza y Preparación (Data Wrangling)
Para que el modelo pudiera procesar la información, se realizó un pipeline de limpieza profunda:
* **Normalización de Unidades:** Se eliminaron las etiquetas "GB" de la columna `Ram` y "kg" de `Weight`, convirtiéndolas a tipos numéricos (`int` y `float`).
* **Feature Engineering (Ingeniería de Características):**
    * **Pantalla:** Se extrajo la resolución (X e Y) para calcular los **PPI (Píxeles por Pulgada)**, una métrica más precisa de la calidad de imagen.
    * **CPU:** Se separó la marca del procesador y se extrajo la frecuencia nominal en **GHz**.
    * **Almacenamiento:** Se crearon columnas binarias y cuantitativas para diferenciar entre **SSD** y **HDD**, permitiendo identificar configuraciones híbridas.
  
## 🛠️ Técnicas de Minería de Datos Aplicadas
Se optó por un enfoque de **Aprendizaje Supervisado**:
1.  **Transformación Logarítmica:** Se aplicó `log` al precio para normalizar la distribución y reducir el impacto de los valores atípicos (laptops de lujo).
2.  **Algoritmo de Regresión:** Se implementó **Random Forest Regressor**, seleccionado por su capacidad para manejar relaciones no lineales y su robustez frente al sobreajuste.
3.  **Evaluación:** Se utilizaron las métricas **R2 Score** y **MAE (Mean Absolute Error)**.
<img width="1314" height="781" alt="image" src="https://github.com/user-attachments/assets/46eb7d8f-1c70-4ac2-a6ef-42fc3fb8293f" />


## 📈 Resultados Obtenidos
* **Precisión (R2 Score):** ~0.88 (El modelo explica el 88% de la varianza de los precios).
* **Variables Críticas:** El análisis de importancia reveló que la **RAM**, es el factor que más dispara el precio.
  <img width="1566" height="715" alt="image" src="https://github.com/user-attachments/assets/0d8df1ff-38bd-4834-9587-cab0a9143e20" />

* **Visualización:** Se generaron gráficos de importancia de variables y de dispersión (Real vs. Predicho) que validan la consistencia del modelo.
  <img width="1554" height="420" alt="image" src="https://github.com/user-attachments/assets/0c747cee-eefe-4a0c-a9f6-47bedd828769" />



## 💡 Conclusiones
1.  **El hardware manda:** La potencia bruta (RAM/CPU) sigue siendo el principal motor de precio, por encima de la marca en muchos casos.
2.  **La portabilidad cuesta:** Equipos con alta densidad de píxeles (PPI) y bajo peso tienden a tener un "premium" de precio independiente de su potencia.
3.  **Eficiencia del Almacenamiento:** La transición a SSD ha hecho que el tamaño del disco sea menos relevante para el precio que la tecnología del mismo.

## ⚠️ Limitaciones y Recomendaciones Futuras
* **Limitaciones:** El dataset no incluye el año de lanzamiento, lo cual es crítico dado que el hardware se deprecia rápidamente.
* **Recomendaciones:** * Incluir variables de "Sentimiento de Marca" o valor de reventa.
    * Implementar modelos de *Boosting* (como XGBoost o LightGBM) para intentar superar el R2 actual.
    * Desarrollar una interfaz sencilla (Streamlit) para que los usuarios ingresen specs y obtengan un precio estimado.
