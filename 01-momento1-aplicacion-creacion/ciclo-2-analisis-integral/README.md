# Ciclo 2 · Fase 2 — Análisis cuantitativo integral: de la exploración a las técnicas avanzadas

**Semanas 5–12 · Individual · 200 puntos · RAP 1, RAP 2 y RAP 3**

Objetivo: que el doctorando ejecute de principio a fin un análisis cuantitativo riguroso
sobre un **dataset real compartido por toda la cohorte** y produzca un reporte científico
reproducible de calidad publicable. Todos trabajan el mismo dataset y problema analítico
rector, lo que habilita la comparación de decisiones y la revisión entre pares.

## Parte 1 — Análisis fundamental (Semanas 5–8)

Organizada por lo que el investigador *hace con los datos*: conocer → comparar → modelar → extender.

- **Semana 5 — Conocer los datos.** Exploración, diagnóstico de calidad, estadística descriptiva robusta, detección de outliers y visualización científica (pandas, scipy.stats, matplotlib, seaborn).
- **Semana 6 — Comparar grupos.** Árbol de decisión de pruebas (t-test/Welch/Mann-Whitney; ANOVA/Kruskal-Wallis + post-hoc Tukey). Reportar tamaño del efecto e IC 95% como información primaria (scipy.stats, pingouin).
- **Semana 7 — Modelar relaciones.** Regresión lineal múltiple con `statsmodels` (no scikit-learn) y diagnóstico completo de supuestos (VIF, Breusch-Pagan, Cook, Q-Q). Recurso: `diagnostico_regresion_plantilla.ipynb`.
- **Semana 8 — Extender el modelo + punto de control.** Regresión logística (odds ratios, pseudo-R²). Entrega **obligatoria** del notebook de la Parte 1 y webconferencia de retroalimentación; se comunica la técnica avanzada elegida.

## Parte 2 — Profundización avanzada (Semanas 9–12)

Seleccionar **exactamente una** técnica del menú, según la línea DTI:

1. **Multivariante y SEM** (IASC, ADVTD, CRIC): PCA, AFE/AFC (factor_analyzer), SEM/PLS (semopy).
2. **Series temporales** (IoTCI, CRIC): descomposición, ADF, ARIMA (statsmodels.tsa).
3. **Inferencia bayesiana** (CRIC, IASC): PyMC + arviz (MCMC/NUTS, HDI, factores de Bayes).
4. **Evaluación estadística de modelos de ML** (IASC, ADVTD): validación cruzada anidada, McNemar/Demšar (scikit-learn, mlxtend).

- **Semanas 9–10 — Aplicación de la técnica avanzada** (usando el notebook de ejemplo como andamiaje, no como copia).
- **Semana 11 — Reproducibilidad, publicación FAIR y code review entre pares** (requirements/environment, README, publicación en GitHub, opcional Zenodo/OSF con DOI).
- **Semana 12 — Reporte científico de resultados** (formato paper).

## Evidencia

Reporte científico (**8–10 páginas, APA 7 o IEEE**) con implicaciones para la tesis en la
Discusión; Jupyter Notebook reproducible (Partes 1 y 2); enlace al repositorio con código
publicado bajo principios FAIR; y reporte de code review del notebook de un compañero.

## Contenido de las carpetas

| Carpeta | Qué va aquí |
|---|---|
| [`lecturas/`](lecturas/) | Lecturas del ciclo (Wasserstein & Lazar 2016, Cohen 1988, McKinney 2022, etc.). |
| [`dataset/`](dataset/) | Dataset compartido de la cohorte + diccionario de variables + descripción del problema analítico rector + guía de inicio rápido. |
| [`plantillas/`](plantillas/) | `diagnostico_regresion_plantilla.ipynb` y plantillas de reporte científico. |
| [`notebooks-ejemplo/`](notebooks-ejemplo/) | Notebooks de ejemplo del tutor para cada técnica avanzada del menú. |
