# APM Tool: Application Performance Monitoring Dashboard 🚀

## 🎥 Video de Presentación
https://youtu.be/4YXbVk742p4

## 📋 Descripción del Proyecto
El objetivo principal es el análisis de rendimiento de una arquitectura de microservicios (*Auth-Service*, *Payment-Gateway* e *Inventory-API*) mediante el procesamiento de logs de infraestructura. Se busca identificar la causa raíz de la latencia elevada y los fallos de estado 500 correlacionando métricas de CPU y RAM.


## 🛠️ Stack Tecnológico
* **Microsoft Excel:** Análisis de datos y motor de visualización.
* **IA (Ideas & Copilot):** Generación de insights automáticos y detección de patrones de error.

## 📊 Hallazgos Técnicos Principales
Basado en el análisis de los datos en `ProjectoFinalEANX.xlsx`, se concluyó lo siguiente:

* **Saturación de Memoria:** El servicio **Payment-Gateway** es el punto crítico de la infraestructura, operando con un promedio de **1,338.44 MB** de RAM (aproximadamente 300% más que los servicios auxiliares).
* **Impacto de Errores 500:** Se identificó que durante los fallos de estado 500, el **Auth-Service** experimenta una elevación en el consumo de recursos llegando a los **462.16 MB**, lo que sugiere fugas de memoria o reintentos infinitos ante fallos.
* **Diagnóstico de Latencia:** Mediante el uso de IA, se detectó una correlación directa entre el uso de CPU > 85% y latencias superiores a los 2,000ms en el Gateway de pagos.

## ⚙️ Implementación Técnica
Para la construcción del Dashboard se utilizaron:
1. **Fórmulas Lógicas:** Segmentación de severidad de logs mediante funciones SI anidadas.
2. **Tablas Dinámicas:** Resumen de métricas de rendimiento por servicio y código de estado.

