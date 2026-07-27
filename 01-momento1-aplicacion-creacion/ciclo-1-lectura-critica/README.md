# Ciclo 1 · Fase 1 — Lectura crítica de investigación cuantitativa en TI

**Semanas 1–4 · Individual · 100 puntos · RAP 1 y RAP 2**

Objetivo: que el doctorando desarrolle criterio metodológico doctoral mediante el análisis
crítico de artículos de investigación cuantitativa publicados en TI. Sigue una lógica de
andamiaje cognitivo: estudiar los fundamentos (Sem. 1), observar al tutor aplicarlos en
vivo (Sem. 2), replicar el proceso de forma autónoma (Sem. 3) y enriquecerlo con la
discusión entre pares (Sem. 4).

## Semanas

- **Semana 0 — Preparación del entorno técnico (sin puntaje).** Configurar Python/Jupyter con Anaconda (o Google Colab) y ejecutar el `entorno_verificacion.ipynb`. Ver [`recursos-transversales/software`](../../recursos-transversales/software/).
- **Semana 1 — Fundamentos metodológicos.** Tipologías de estudios cuantitativos en TI, variables y operacionalización, amenazas a la validez (marco de Wohlin et al., 2012), muestreo y potencia, ética (Ley 1581 de 2012, preregistro, FAIR). Lectura obligatoria: Wohlin cap. 1–2.
- **Semana 2 — Modelamiento y selección de artículo.** Webconferencia donde el tutor analiza un artículo en vivo; luego el estudiante elige **1** artículo del banco (preferiblemente de una línea DTI distinta a la propia) y descarga la plantilla de análisis.
- **Semana 3 — Análisis metodológico individual.** Completar la plantilla, ejecutar la verificación de potencia en Python y publicar un resumen ejecutivo (≤300 palabras) en el foro.
- **Semana 4 — Discusión entre pares e integración.** Comentar mínimo dos publicaciones de compañeros y compilar el reporte final.

## Evidencia

Reporte de Análisis Metodológico (**6–8 páginas, APA 7**) con cuatro secciones: (1) análisis
estructurado del artículo, (2) verificación de potencia con Python, (3) reflexión crítica,
(4) reflexión integrativa; más el Jupyter Notebook de potencia reproducible adjunto.

## Contenido de las carpetas

| Carpeta | Qué va aquí |
|---|---|
| [`lecturas/`](lecturas/) | Wohlin cap. 1–2 y lecturas complementarias del ciclo. |
| [`banco-articulos/`](banco-articulos/) | Los **5 artículos** cuantitativos del banco del tutor, con al menos uno por línea DTI (CRIC, IASC, IoTCI, ADVTD). |
| [`plantillas/`](plantillas/) | `plantilla-analisis-metodologico` y `potencia_plantilla.ipynb` (código base de `statsmodels.stats.power`). |
