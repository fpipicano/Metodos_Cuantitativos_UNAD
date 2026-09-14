# 2 · Análisis cuantitativo integral: de la exploración a las técnicas avanzadas

**Ciclo 2 · Fase 2 · Semanas 5–12 · Individual · 200 puntos · RAP 1, 2 y 3 · Competencias CDTI 1 y 2**

> Momento 1 — Aplicación y Creación · 48 h de trabajo independiente · 24 h de acompañamiento.
> Fechas cohorte 2026: **14 sep → 8 nov 2026**.

El doctorando ejecuta de principio a fin un análisis cuantitativo riguroso sobre un
**dataset real compartido por toda la cohorte** y produce un reporte científico reproducible
de calidad publicable. Todos trabajan el mismo dataset y problema analítico rector, lo que
habilita la comparación de decisiones y la revisión entre pares (fase **Hacer**).

## Parte 1 — Análisis fundamental (Semanas 5–8)

Organizada por lo que el investigador *hace con los datos*: conocer → comparar → modelar → extender.

- **Sem. 5 — Conocer los datos.** Exploración, diagnóstico de calidad, estadística descriptiva robusta, detección de outliers, visualización científica (pandas, scipy.stats, matplotlib, seaborn).
- **Sem. 6 — Comparar grupos.** Árbol de decisión de pruebas (t-test / Welch / Mann-Whitney; ANOVA / Kruskal-Wallis + post-hoc Tukey). Reportar tamaño del efecto e IC 95 % como información primaria (scipy.stats, pingouin).
- **Sem. 7 — Modelar relaciones.** Regresión lineal múltiple con `statsmodels` (no scikit-learn) y diagnóstico completo de supuestos (VIF, Breusch-Pagan, Cook, Q-Q). Recurso: `diagnostico_regresion_plantilla.ipynb`.
- **Sem. 8 — Extender el modelo + punto de control.** Regresión logística (odds ratios, pseudo-R²). Entrega **obligatoria** del notebook de la Parte 1 (sin puntaje independiente) y webconferencia de retroalimentación; se comunica la técnica avanzada elegida.

## Parte 2 — Profundización avanzada (Semanas 9–12)

Seleccionar **exactamente una** técnica del menú, según la línea DTI:

| Opción | Técnica | Librerías | Recomendada para |
|---|---|---|---|
| 1 | Multivariante y SEM (PCA, AFE/AFC, SEM/PLS) | scikit-learn, factor_analyzer, semopy | IASC, ADVTD, CRIC |
| 2 | Series temporales (descomposición, ADF, ARIMA) | statsmodels.tsa | IoTCI, CRIC |
| 3 | Inferencia bayesiana (MCMC/NUTS, HDI, Bayes) | PyMC, arviz | CRIC, IASC |
| 4 | Evaluación estadística de modelos de ML (CV anidada, McNemar/Demšar) | scikit-learn, mlxtend | IASC, ADVTD |

- **Sem. 9–10 — Aplicación de la técnica avanzada** (usando el notebook de ejemplo como andamiaje, no como copia).
- **Sem. 11 — Reproducibilidad, publicación FAIR y code review entre pares** (requirements/environment, README, publicación en GitHub, opcional Zenodo/OSF con DOI).
- **Sem. 12 — Reporte científico de resultados** (formato paper).

## Evidencia

Reporte científico (**8–10 páginas, APA 7 o IEEE**) con implicaciones para la tesis en la
Discusión; Jupyter Notebook reproducible (Partes 1 y 2); enlace al repositorio con código
publicado bajo principios FAIR; y reporte de code review del notebook de un compañero.

## Contenido de las carpetas

| Carpeta | Qué va aquí |
|---|---|
| [`dataset/`](dataset/) | Dataset compartido de la cohorte + diccionario de variables + descripción del problema analítico rector + guía de inicio rápido. |
| [`plantillas/`](plantillas/) | `diagnostico_regresion_plantilla.ipynb` y plantilla de reporte científico (paper). |
| [`ejemplos/`](ejemplos/) | Un notebook de ejemplo del tutor por cada técnica avanzada del menú. |
| [`lecturas/`](lecturas/) | Wasserstein & Lazar (2016), Cohen (1988), McKinney (2022), Demšar (2006), etc. |
