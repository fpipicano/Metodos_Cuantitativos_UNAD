# Métodos Cuantitativos en Investigación · Repositorio Oficial del Entorno

![Programa](https://img.shields.io/badge/Programa-Doctorado%20en%20Tecnolog%C3%ADas%20de%20Informaci%C3%B3n-0b5394)
![Código](https://img.shields.io/badge/C%C3%B3digo%20del%20entorno-203538899-1c4587)
![Créditos](https://img.shields.io/badge/Cr%C3%A9ditos-3-274e13)
![Duración](https://img.shields.io/badge/Duraci%C3%B3n-16%20semanas-7f6000)
![Herramienta](https://img.shields.io/badge/Herramienta-Python%20%2B%20Jupyter-3776ab)
![Ciencia abierta](https://img.shields.io/badge/Ciencia%20abierta-FAIR-660000)

Repositorio oficial del entorno **Métodos Cuantitativos en Investigación** del
**Doctorado en Tecnologías de Información (DTI)** — Escuela de Ciencias Básicas, Tecnología
e Ingeniería (ECBTI), Universidad Nacional Abierta y a Distancia (UNAD).

Este es el **Repositorio Oficial del Entorno** al que remiten las guías de cada ciclo
(el "Anexo 1"). Aquí encontrarás el notebook de verificación, las plantillas, el banco de
artículos, el dataset compartido de la cohorte y las guías de instalación.

> Registro calificado: Resolución No. 016094 del 29 de julio de 2025.

---

## Descripción general

El entorno es el espacio de formación metodológica que dota al futuro doctor de los marcos
conceptuales, los criterios epistemológicos y las herramientas computacionales para
diseñar, ejecutar e interpretar investigaciones empíricas cuantitativas de alto rigor en
Tecnologías de Información. La estrategia es **Aprendizaje Basado en Investigación**, con
una progresión deliberada en tres fases: primero **criticar** investigación publicada,
luego **hacer** análisis propios sobre un dataset real, y finalmente **implementar** el
diseño metodológico de la propia tesis.

**Resultados de Aprendizaje del Programa asociados:** RAP 1, RAP 2 y RAP 3.

## Estructura del entorno

Dos momentos, tres ciclos, 16 semanas. La calificación total es de 500 puntos.

| Momento | Ciclo (Fase) | Semanas | Evidencia central | Puntos |
|---|---|---|---|---|
| **1. Aplicación y Creación** (60%) | Ciclo 1 · Fase 1 — Lectura crítica de investigación cuantitativa en TI | 1–4 | Reporte de Análisis Metodológico (6–8 pág, APA 7) + notebook de potencia | 100 |
| **1. Aplicación y Creación** (60%) | Ciclo 2 · Fase 2 — Análisis cuantitativo integral | 5–12 | Reporte científico (8–10 pág) + notebook reproducible + repo FAIR + code review | 200 |
| **2. Consolidación y Transferencia** (40%) | Ciclo 3 · Fase 3 — Protocolo Metodológico Cuantitativo y Coloquio Doctoral | 13–16 | Protocolo (10–12 pág, 10 secciones) + defensa oral en Coloquio | 200 |
| | | **16 semanas** | | **500 (100%)** |

Las tres fases de la estrategia: **Fase 1 — Criticar** (Ciclo 1) · **Fase 2 — Hacer**
(Ciclo 2) · **Fase 3 — Implementar** (Ciclo 3).

## Cómo navegar este repositorio

```
metodos-cuantitativos-dti/
├── 00-cronograma/                              → calendario 16 semanas con fechas e hitos
│
├── 01-momento1-aplicacion-creacion/            → Momento 1 (60%)
│   ├── ciclo-1-lectura-critica/                → Fase 1 · Semanas 1–4 · 100 pts
│   │   ├── lecturas/                            → Wohlin cap. 1–2 y complementarias
│   │   ├── banco-articulos/                     → 8 artículos (2 por línea DTI)
│   │   ├── articulo-modelo-webconferencia/      → artículo que el tutor analiza en vivo (Sem. 2)
│   │   └── plantillas/                          → análisis metodológico (8 operaciones) · potencia · rúbrica
│   └── ciclo-2-analisis-integral/              → Fase 2 · Semanas 5–12 · 200 pts
│       ├── lecturas/
│       ├── dataset/                             → dataset compartido + diccionario + problema rector
│       ├── plantillas/                          → diagnostico_regresion_plantilla.ipynb
│       └── notebooks-ejemplo/                   → notebooks del tutor para las técnicas avanzadas
│
├── 02-momento2-consolidacion-transferencia/    → Momento 2 (40%)
│   └── ciclo-3-protocolo-coloquio/             → Fase 3 · Semanas 13–16 · 200 pts
│       ├── lecturas/
│       └── plantillas/                          → plantilla de Protocolo (10 secciones) · coloquio
│
├── recursos-transversales/
│   ├── software/                                → instalación (Anaconda/Python/Colab) + entorno_verificacion.ipynb
│   └── bibliografia/                            → referencias completas del entorno (APA 7)
│
├── gestion-docente/                            → ⚠️ interno (auditoría del banco, inventario) — NO publicar a estudiantes
├── requirements.txt                            → dependencias de Python del entorno
└── matriz-documental.md                        → índice de los 22 documentos auxiliares
```

> **Nota sobre `gestion-docente/`:** contiene la auditoría del banco (con las debilidades
> *intencionales* de algunos artículos) y la comparación de candidatos. Publicarla donde los
> estudiantes la vean arruinaría el ejercicio del Ciclo 1; consérvala en un repositorio
> privado o una rama protegida.

Cada carpeta de ciclo tiene su propio `README.md` con objetivos, semanas, contenidos y
evidencias. Empieza por [`00-cronograma`](00-cronograma/) y, antes de la Semana 1,
configura tu entorno con
[`recursos-transversales/software`](recursos-transversales/software/).

## Herramientas del entorno

El entorno adopta **Python con Jupyter Notebooks** como herramienta principal, instaurando
la replicabilidad científica como práctica transversal (principios FAIR). Ver guías en
[`recursos-transversales/software`](recursos-transversales/software/) y dependencias en
[`requirements.txt`](requirements.txt).

- **Python (Anaconda)** — pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib, seaborn, pingouin; y según la técnica avanzada: PyMC + arviz (bayesiana), semopy + factor_analyzer (SEM/AFC), mlxtend (comparación de modelos).
- **Jupyter Notebooks / Google Colab** — entorno de análisis reproducible (alternativa sin instalación local).
- **GitHub** — publicación de código y notebooks bajo principios FAIR.
- **G\*Power** — cálculo de potencia estadística (junto a `statsmodels.stats.power`).
- **Institucionales UNAD:** SPSS y Turnitin, disponibles en el campus virtual como apoyo.

## Líneas de investigación del DTI

Varias actividades piden contextualizar el trabajo en una de las cuatro líneas del
programa: **CRIC** (Ciberseguridad y Resiliencia de Infraestructuras Críticas), **IASC**
(Inteligencia Artificial y Sistemas Cognitivos), **IoTCI** (Internet de las Cosas y
Ciudades Inteligentes) y **ADVTD** (Analítica de Datos y Visualización para la Toma de
Decisiones).

## Referencias principales

Lista completa en [`recursos-transversales/bibliografia`](recursos-transversales/bibliografia/).
Núcleo del entorno:

- Wohlin, C., Runeson, P., Höst, M., Ohlsson, M. C., Regnell, B., & Wesslén, A. (2024). *Experimentation in Software Engineering*. Springer.
- Cohen, J. (1988). *Statistical Power Analysis for the Behavioral Sciences* (2.ª ed.). Lawrence Erlbaum.
- Wasserstein, R. L., & Lazar, N. A. (2016). The ASA's statement on p-values. *The American Statistician, 70*(2), 129–133.
- McKinney, W. (2022). *Python for Data Analysis* (3.ª ed.). O'Reilly.
- Wilkinson, M. D., et al. (2016). The FAIR Guiding Principles for scientific data management and stewardship. *Scientific Data, 3*, 160018.

## Créditos

Diseño del entorno: **Felipe Alexander Pipicano Guzmán**. Visto bueno (Líder de Programa):
**Edna Rocío Bernal Monroy**. Versión 1 (2026). Doctorado en Tecnologías de Información —
ECBTI, UNAD.

---

*Verifica siempre la versión vigente de los formatos institucionales en el SIG de la UNAD.*
