# Métodos Cuantitativos en Investigación · Repositorio Oficial del Entorno

![Programa](https://img.shields.io/badge/Programa-Doctorado%20en%20Tecnolog%C3%ADas%20de%20Informaci%C3%B3n-0b5394)
![Código](https://img.shields.io/badge/C%C3%B3digo-203538899-1c4587)
![Créditos](https://img.shields.io/badge/Cr%C3%A9ditos-3-274e13)
![Duración](https://img.shields.io/badge/Duraci%C3%B3n-16%20semanas-7f6000)
![Herramienta](https://img.shields.io/badge/Python%20%2B%20Jupyter-3776ab)
![Ciencia abierta](https://img.shields.io/badge/FAIR-660000)
![Licencia](https://img.shields.io/badge/Licencia-CC%20BY%204.0-a64d79)

Repositorio oficial del entorno **Métodos Cuantitativos en Investigación** del **Doctorado
en Tecnologías de Información (DTI)** — Escuela de Ciencias Básicas, Tecnología e Ingeniería
(ECBTI), Universidad Nacional Abierta y a Distancia (UNAD).

Este es el **Repositorio Oficial del Entorno** al que remiten las guías de cada ciclo (el
"Anexo 1"): aquí viven el notebook de verificación, las plantillas, el banco de artículos,
el dataset compartido de la cohorte y las guías de instalación.

---

## Descripción general

El entorno dota al futuro doctor de los marcos conceptuales, los criterios epistemológicos
y las herramientas computacionales para diseñar, ejecutar e interpretar investigaciones
empíricas cuantitativas de alto rigor en Tecnologías de Información. La estrategia es
**Aprendizaje Basado en Investigación**, con una progresión deliberada en tres fases:
primero **criticar** investigación publicada, luego **hacer** análisis propios sobre un
dataset real, y finalmente **implementar** el diseño metodológico de la propia tesis.

**Prerrequisitos recomendados:** conocimientos generales de estadística descriptiva y
familiaridad básica con Python o algún lenguaje de programación.

**Resultados de Aprendizaje del Programa:** RAP 1 (analizar), RAP 2 (evaluar), RAP 3
(integrar). **Competencias:** CDTI 1 y CDTI 2.

## Estructura del entorno

Dos momentos, tres ciclos, 16 semanas. Calificación total: **500 puntos**.

| Momento | Ciclo (Fase) | Semanas | Evidencia central | Puntos |
|---|---|---|---|---|
| **1 · Aplicación y Creación** (60%) | [Ciclo 1 · Fase 1 — Lectura crítica](1-lectura-critica/) | 1–4 | Reporte de Análisis Metodológico (6–8 pág, APA 7) + notebook de potencia | 100 |
| **1 · Aplicación y Creación** (60%) | [Ciclo 2 · Fase 2 — Análisis integral](2-analisis-integral/) | 5–12 | Reporte científico (8–10 pág) + notebook reproducible + repo FAIR + code review | 200 |
| **2 · Consolidación y Transferencia** (40%) | [Ciclo 3 · Fase 3 — Protocolo y Coloquio](3-protocolo-coloquio/) | 13–16 | Protocolo (10–12 pág, 10 secciones) + defensa oral en Coloquio | 200 |

Las tres fases de la estrategia: **Criticar** (Ciclo 1) · **Hacer** (Ciclo 2) ·
**Implementar** (Ciclo 3).

## Cómo empezar

1. **Antes de la Semana 1**, configura tu entorno: abre [`0-preparacion/`](0-preparacion/) y ejecuta `entorno_verificacion.ipynb` (Kernel → *Restart & Run All*). Debe terminar en ✅ **ENTORNO LISTO**.
2. Instala las dependencias con [`requirements.txt`](requirements.txt) (pip) o [`environment.yml`](environment.yml) (conda).
3. Revisa el calendario en [`docs/cronograma.md`](docs/cronograma.md) y arranca por el [Ciclo 1](1-lectura-critica/).

## Mapa del repositorio

```
metodos-cuantitativos-dti/
├── 0-preparacion/          Semana 0 · verificación e instalación del entorno (sin puntaje)
├── 1-lectura-critica/      Ciclo 1 · Sem 1–4 · 100 pts · articulos · plantillas · lecturas
├── 2-analisis-integral/    Ciclo 2 · Sem 5–12 · 200 pts · dataset · plantillas · ejemplos · lecturas
├── 3-protocolo-coloquio/   Ciclo 3 · Sem 13–16 · 200 pts · plantillas · lecturas
├── docs/                   cronograma · bibliografía · plan de formación · guías de ciclo
├── requirements.txt        dependencias pip (núcleo + técnicas avanzadas)
├── environment.yml         entorno conda equivalente
├── LICENSE · CHANGELOG.md · .gitignore
```

Cada carpeta de ciclo tiene su propio `README.md` con objetivos, semanas, evidencia y
contenido de las subcarpetas.

## Herramientas

**Python con Jupyter Notebooks** es la herramienta principal, instaurando la replicabilidad
científica como práctica transversal (principios FAIR).

- **Python (Anaconda)** — pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib, seaborn, pingouin.
- **Técnicas avanzadas del Ciclo 2** (según la opción): PyMC + arviz (bayesiana), semopy + factor_analyzer (SEM/AFC), mlxtend (comparación de modelos de ML).
- **Jupyter / Google Colab** · **GitHub** (publicación FAIR) · **G\*Power** (potencia, junto a `statsmodels.stats.power`).
- **Apoyo institucional UNAD:** SPSS y Turnitin, disponibles en el campus virtual.

## Líneas de investigación del DTI

Varias actividades piden contextualizar el trabajo en una de las cuatro líneas: **CRIC**
(Ciberseguridad y Resiliencia de Infraestructuras Críticas), **IASC** (Inteligencia
Artificial y Sistemas Cognitivos), **IoTCI** (Internet de las Cosas y Ciudades
Inteligentes) y **ADVTD** (Analítica de Datos y Visualización para la Toma de Decisiones).

## Integridad académica

Todos los productos son de elaboración individual y deben cumplir normas APA 7. Aplica el
Acuerdo 029 de 2013 (art. 99) sobre fraude y plagio. El uso de herramientas de IA debe ser
ético y **declararse explícitamente** al inicio de cada entregable, indicando en qué
aspectos se empleó y de qué manera.

## Créditos

Diseño del entorno: **Felipe Alexander Pipicano Guzmán**. Visto bueno (Líder de Programa):
**Edna Rocío Bernal Monroy**. Versión 1 (2026) — ver [`CHANGELOG.md`](CHANGELOG.md).
Doctorado en Tecnologías de Información, ECBTI, UNAD.

Material distribuido bajo licencia **CC BY 4.0** (ver [`LICENSE`](LICENSE)).

---

*Verifica siempre la versión vigente de los formatos institucionales en el SIG de la UNAD.*
