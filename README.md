# AURORA SCORE 2.0

### Dataset sintético y modelamiento de riesgo crediticio alternativo

Proyecto académico desarrollado para la asignatura **Gestión de Proyectos de Datos (SCY1102)**. AURORA SCORE propone un prototipo de scoring crediticio alternativo para **Vertex Financial Group (VFG)**, orientado a explorar señales de comportamiento de pago que puedan complementar la evaluación crediticia tradicional.

> **Aviso importante:** este proyecto utiliza exclusivamente datos sintéticos. Los resultados son experimentales y no representan el desempeño de una entidad financiera real. El score generado es demostrativo y no debe utilizarse para aprobar o rechazar créditos, definir tasas ni tomar decisiones financieras reales.

## Objetivo

Construir y evaluar un prototipo de clasificación que estime la probabilidad de incumplimiento crediticio, utilizando variables sintéticas provenientes de fuentes alternativas de información y comparando distintos algoritmos de Machine Learning.

## Contenido del repositorio

- `AURORA_SCORE_2_0_12pct_GB_revisado_ejecutado.ipynb`: notebook principal con generación de datos, análisis exploratorio, preparación de variables, entrenamiento, evaluación y conclusiones.

## Datos y alcance experimental

- **10.000 solicitudes sintéticas**, distribuidas equitativamente entre Chile, Perú, Colombia y México. Esta distribución es un supuesto experimental, no una estimación de la población real de VFG.
- **Fuentes simuladas:** telecomunicaciones, servicios básicos, billeteras digitales, comercio electrónico y metadatos de la aplicación móvil.
- **Variable objetivo:** `incumplimiento_90d_12m`, que representa un incumplimiento de 90 días o más durante los 12 meses posteriores al otorgamiento.
- **Prevalencia objetivo:** 12%. Es un supuesto de simulación; la proporción observada puede variar ligeramente y no equivale al 11% de pérdida monetaria esperada de la cartera mencionado en el caso de estudio.
- Las variables demográficas, geográficas y laborales se reservan para auditoría de subgrupos y no se utilizan como predictores del score inicial.
- Las redes sociales y la biometría no se utilizan como predictores. La biometría queda fuera del modelo de riesgo y se reserva, según el alcance del proyecto, para verificación de identidad y prevención de fraude.

## Metodología

El notebook contempla las siguientes etapas:

1. Diseño del diccionario de variables y generación del conjunto de datos sintético.
2. Generación probabilística de la variable objetivo e introducción controlada de valores faltantes.
3. Análisis exploratorio de datos (EDA).
4. Selección de variables y división estratificada en entrenamiento, validación y prueba (60% / 20% / 20%).
5. Preprocesamiento y comparación de Regresión Logística, Random Forest y Gradient Boosting.
6. Selección del umbral de clasificación utilizando el conjunto de validación y evaluación final con métricas como Precision, Recall, F1, ROC-AUC y Brier score.
7. Prueba de ablación de variables exploratorias, auditoría de desempeño por subgrupos y prueba de estrés ante cobertura desigual de datos.
8. Interpretabilidad del candidato oficial y construcción de un score demostrativo.

**Gradient Boosting se define como candidato oficial** por coherencia con el caso de estudio. Regresión Logística y Random Forest se mantienen como modelos de comparación. Esta decisión no implica que Gradient Boosting deba obtener la mejor métrica en todos los conjuntos de evaluación.

## Tecnologías utilizadas

- Python
- Jupyter Notebook
- NumPy
- pandas
- Matplotlib y Seaborn
- scikit-learn

## Cómo ejecutar el notebook

1. Clona o descarga este repositorio.
2. Abre una terminal en la carpeta del proyecto.
3. Instala las dependencias necesarias:

   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn
   ```

4. Abre Jupyter Notebook o JupyterLab:

   ```bash
   jupyter notebook
   ```

5. Abre `AURORA_SCORE_2_0_12pct_GB_revisado_ejecutado.ipynb` y ejecuta las celdas en orden.

## Limitaciones

- Los datos, las relaciones entre variables y las etiquetas fueron generados artificialmente; no son registros reales de clientes.
- El 12% corresponde a la prevalencia objetivo del experimento y no a una tasa real de incumplimiento.
- El desempeño obtenido depende de los supuestos definidos en el generador sintético y no garantiza resultados equivalentes con datos reales.
- La auditoría por subgrupos con datos sintéticos no demuestra ausencia de sesgo ni sustituye una evaluación legal, estadística y ética con datos reales y representativos.
- Una implementación real requeriría validación temporal, calibración, explicabilidad, revisión independiente, supervisión humana, consentimiento y cumplimiento regulatorio en cada país.

## Contexto de arquitectura

El proyecto mantiene la decisión de diseño definida por el equipo: **Alternativa A, plataforma cloud-nativa gestionada**. Este repositorio se concentra en el componente de datos, modelamiento y evaluación del riesgo; no implementa por sí solo la arquitectura productiva completa.

---

**Proyecto académico AURORA SCORE 2.0.**
