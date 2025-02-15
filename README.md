# Customer-Churn-Records
Diseñar un modelo basado en Redes Neuronales Bayesianas para determinar que clientes tienen mayor probabilidad de abandonar, utilizando la base de datos de kaggle [Customer-Churn-Records](https://www.kaggle.com/datasets/nihelghennani/customer-churn-records/data)

Base de datos que usamos para la primer presentación: [Binary Classification with a Bank Churn Dataset](https://www.kaggle.com/competitions/playground-series-s4e1)


## Introducción al Proyecto
### 1.	Definición del Problema:
*	Determinar qué clientes tienen mayor probabilidad de abandonar (Exited) y qué factores influyen en esta decisión.
*	Incorporar análisis causal para evaluar cómo intervenciones específicas (e.g., mejora de la satisfacción) afectan el abandono.
*	Explorar elementos conductuales como aversión a la pérdida o sesgo de inercia en decisiones de retención.
### 2.	Objetivo General:
*	Diseñar un modelo basado en redes neuronales bayesianas para capturar la incertidumbre en las predicciones.
*	Usar un enfoque causal para entender relaciones clave y proponer estrategias que mitiguen el abandono.
### 3.	Objetivo Behavioral Economics:
*	Incorporar principios de economía conductual como:
    * Framing: Evaluar cómo cambios en la comunicación influyen en el abandono.
    * Loss Aversion: Modelar la importancia de mantener un beneficio percibido (e.g., puntos de lealtad).
________________________________________
## Exploración y Preparación de Datos
### 1.	Exploración de Datos:
*	Visualizar distribuciones clave: Balance, Satisfaction Score, y EstimatedSalary.
*	Analizar correlaciones con Exited para identificar patrones iniciales.
*	Identificar clases desbalanceadas para ajustar la arquitectura del modelo.
### 2.	Transformaciones de Datos:
*	Normalización y Escalamiento: Variables numéricas (CreditScore, Balance, etc.).
*	Codificación: Variables categóricas (Geography, Gender, Card Type).
*	Creación de Variables:
    *	Indicadores conductuales, e.g., clientes que aumentaron significativamente su saldo antes de abandonar.
    *	Variables interactivas, e.g., interacción entre Satisfaction Score y IsActiveMember.
________________________________________
## Análisis Causal
### 1.	Definición del Gráfico Causal:
*	Usar literatura o hipótesis basada en economía conductual para construir el gráfico causal.
*	Ejemplo de relaciones:
    *	Satisfaction Score → Exited.
    *	Balance → Satisfaction Score.
    *	Complain → Exited.
    *	IsActiveMember → Exited.
### 2.	Herramientas y Métodos:
*	Gráficos Causales: Construir con causalnex o DoWhy.
*	Identificación de Efectos Directos e Indirectos:
    *	Calcular el efecto causal promedio (ATE) y los efectos mediadores (e.g., Balance como mediador entre Satisfaction Score y Exited).
### 3.	Simulación de Intervenciones:
*	Simular escenarios como:
    *	Incrementar Satisfaction Score en 10%.
    *	Ofrecer beneficios adicionales a clientes con altos saldos (Balance).
*	Evaluar impacto en la probabilidad de abandono.
________________________________________
## Modelos Probabilísticos y Redes Neuronales Bayesianas
### 1.	Selección de Modelos:
*	Modelo Base:
    * Red Neuronal Densa (DNN) con capas ocultas, activación ReLU, y regularización (Dropout).
*	Red Neuronal Bayesiana:
    *	Usar TensorFlow Probability para introducir incertidumbre en los pesos y bias.
    *	Inferencia Variacional (VI) o MC Dropout para aproximaciones bayesianas.
*	Modelo Comparativo:
    *	Modelo no probabilístico (e.g., una red neural tradicional) para contrastar resultados.
### 2.	Arquitectura de la Red:
*	Entrada: Variables transformadas (e.g., Satisfaction Score, Balance).
*	Capas Ocultas:
    *	Varias capas densas con distribuciones probabilísticas para pesos y sesgos.
*	Salida:
    *	Distribución de probabilidad sobre Exited (e.g., distribución Bernoulli).
### 3.	Pérdida y Optimización:
*	Función de pérdida: Evidencia Negativa Log-Likelihood (NLL).
*	Optimizadores: Adam o variantes específicas para redes probabilísticas.
________________________________________
## Behavioral Economics y Diseño de Intervenciones
### 1.	Principios de Behavioral Economics:
*	Loss Aversion:
    *	Modelar cómo la percepción de pérdida afecta Satisfaction Score y su relación con el abandono.
*	Framing:
    *	Evaluar si la forma en que se presentan las ofertas de retención (e.g., "evite perder sus puntos") afecta la probabilidad de abandono.
*	Inercia:
    *	Estudiar cómo la actividad del cliente (IsActiveMember) afecta el comportamiento de abandono.
### 2.	Diseño de Experimentos:
*	Crear contrafactuales basados en intervenciones hipotéticas:
    *	Cambios en políticas de retención.
    *	Comunicación más personalizada.
________________________________________
## Evaluación del Modelo
### 1.	Métricas de Evaluación:
*	Exactitud, F1-score, curva ROC-AUC.
*	Análisis de incertidumbre en las predicciones:
    *	Visualización de distribuciones predictivas para Exited.
### 2.	Validación Cruzada:
*	Usar k-fold validation para evaluar robustez del modelo.
________________________________________
## Interpretación y Resultados
### 1.	Análisis de Importancia de Variables:
*	Usar SHAP o gráficos causales para identificar las características más relevantes.
*	Evaluar cómo factores conductuales impactan el abandono.
### 2.	Recomendaciones:
*	Proponer estrategias basadas en los hallazgos:
    *	Beneficios dirigidos a clientes con altos valores de Satisfaction Score.
    *	Campañas específicas para retener clientes con altos balances.
________________________________________
## Documentación y Presentación
### 1.	Resultados Visuales:
*	Visualización de distribuciones predictivas y mapas de calor para efectos causales.
*	Comparación de modelos bayesianos y no bayesianos.
### 2.	Informe Final:
*	Resumen detallado de hallazgos, metodología, y recomendaciones basadas en causalidad y economía conductual.

