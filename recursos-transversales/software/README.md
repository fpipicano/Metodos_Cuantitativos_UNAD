# Software del entorno

El entorno usa **Python con Jupyter Notebooks** como herramienta principal. Configura tu
entorno en la **Semana 0**, antes de que inicie el Ciclo 1, para que la Semana 1 se dedique
íntegramente a los contenidos metodológicos.

## Herramientas

| Herramienta | Uso | Notas |
|---|---|---|
| **Python + Anaconda** | Análisis estadístico y ciencia de datos | Anaconda incluye los paquetes base. Ver [`requirements.txt`](../../requirements.txt). |
| **Jupyter Notebooks** | Entorno de análisis reproducible | Incluido en Anaconda. |
| **Google Colab** | Alternativa sin instalación local | https://colab.research.google.com/ |
| **GitHub** | Publicación de código y notebooks (FAIR) | Repositorio público del análisis del Ciclo 2. |
| **G\*Power** | Cálculo de potencia estadística | Junto a `statsmodels.stats.power`. |
| **SPSS · Turnitin** | Apoyo institucional UNAD | Disponibles en el campus virtual. |

## Semana 0 — Preparación del entorno técnico (sin puntaje)

1. Instalar **Anaconda** (versión más reciente). Incluye pandas, scipy, statsmodels, scikit-learn, matplotlib, seaborn y pingouin.
2. Ejecutar el `entorno_verificacion.ipynb` (provisto por el tutor) para comprobar que cada paquete carga en la versión correcta. Guardar la captura del resultado.
3. Alternativa: crear una cuenta en **Google Colab** y ejecutar allí el notebook de verificación.

Si hay dificultades de instalación, comunicarlas al tutor por el correo del campus virtual.

## Archivos sugeridos para esta carpeta

- `entorno_verificacion.ipynb` — notebook de verificación de paquetes (Semana 0).
- `instalacion-anaconda.md` — guía paso a paso de instalación.
- `guia-colab.md` — uso de Google Colab como alternativa.

> Para las técnicas avanzadas del Ciclo 2 se requieren paquetes adicionales según la opción
> elegida: `pymc` + `arviz` (bayesiana), `semopy` + `factor_analyzer` (SEM/AFC) o `mlxtend`
> (comparación de modelos de ML). Todos están en `requirements.txt`.
