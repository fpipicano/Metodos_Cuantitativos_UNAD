# Dataset compartido de la cohorte — Ciclo 2

**Digital Security Perceptions & Practices in 12 Countries**
Encuesta internacional sobre conocimiento, percepciones y prácticas de seguridad digital.

Este es el **dataset único para toda la cohorte** del Ciclo 2 (Fase 2). Todos los análisis
de las Semanas 5–12 se realizan sobre este mismo archivo, lo que permite la comparación de
decisiones analíticas entre compañeros y la revisión científica entre pares.

> **Línea DTI:** Ciberseguridad y Resiliencia de Infraestructuras Críticas (**CRIC**),
> desde la perspectiva del factor humano en seguridad. Conecta con los artículos de
> seguridad del banco del Ciclo 1 (Hasani et al., 2023; Lain et al., 2022).

## Contenido de esta carpeta

| Archivo | Qué es |
|---|---|
| `SurveyResponses_DigitalSecurityAroundTheWorld.csv` | **Dataset oficial de la cohorte.** 12.351 filas × 248 columnas. |
| [`diccionario-variables.md`](diccionario-variables.md) | Diccionario de variables: bloques, escalas, códigos de valor y variables clave para el análisis. |
| [`problema-analitico-rector.md`](problema-analitico-rector.md) | Problema analítico rector que orienta los análisis **sin prescribir métodos**. |
| `DataMap_DigitalSecurityAroundTheWorld.pdf` | Data map oficial de los autores (redacción literal de cada pregunta). *(De los autores.)* |

## Fuente y contexto de recolección

- **Autoría:** Franziska Herbert, Steffen Becker, Jonas Hielscher, Collins W. Munyendo, Yixin Zou y colaboradores — Ruhr-Universität Bochum y Max Planck Institute for Security and Privacy (Alemania).
- **Repositorio (FAIR):** ReSeeD, Ruhr-Universität Bochum. ID `zw12z533j`. https://rdms.rd.ruhr-uni-bochum.de/concern/datasets/zw12z533j
- **Recolección:** encuesta en línea, finales de **2021**. Objetivo de **1.000 participantes por país** en **12 países** de cuatro continentes: China, Alemania, India, Israel, Italia, México, Polonia, Arabia Saudita, Sudáfrica, Suecia, Reino Unido y EE. UU. El archivo contiene **N = 12.351** respuestas (entre 1.008 y 1.054 por país).
- **Diseño del estudio original:** encuesta transversal de una sola ola. Los autores **buscaron** cuotas representativas por país en edad, género y educación; según reportan en CHI 2023, las cuotas de **educación no se alcanzaron en varios países**, y la cuota de etnia solo fue representativa para EE. UU. Trata la muestra como *aproximadamente* representativa y documenta esta limitación en tu reporte. Corte analítico **WEIRD vs. no-WEIRD** (países occidentales vs. no occidentales) usado en la publicación de USENIX 2025.

## Licencia y citación obligatoria

> **Antes de distribuir a la cohorte:** confirma la **licencia exacta** en la ficha de ReSeeD
> (campo *License* de la página del dataset). No se asume una licencia concreta en este
> documento. Los datos son de acceso público en el repositorio, pero la licencia define qué
> usos y redistribución están permitidos.

El uso del dataset —según indican los autores— **obliga a citar ambas publicaciones**:

- Herbert, F., Becker, S., Schaewitz, L., Hielscher, J., Kowalewski, M., Sasse, A., Acar, Y., & Dürmuth, M. (2023). *A World Full of Privacy and Security (Mis)conceptions? Findings of a Representative Survey in 12 Countries.* En *Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (CHI '23)*, Artículo 582, 1–23. https://doi.org/10.1145/3544548.3581410
- Herbert, F., Munyendo, C. W., Hielscher, J., Becker, S., & Zou, Y. (2025). *Digital Security Perceptions and Practices Around the World: A WEIRD vs. Non-WEIRD Comparison.* En *Proceedings of the 34th USENIX Security Symposium (USENIX Security 25)*. USENIX Association.

Toda evidencia del Ciclo 2 (reporte, notebook, repositorio FAIR) debe incluir esta doble
citación en APA 7.

## Guía de inicio rápido

```python
import pandas as pd
import numpy as np

# 1) Carga. Usa low_memory=False: una columna (q4r8) trae texto incrustado
#    y sin este parámetro pandas la lee como "tipo mixto" y lanza una advertencia.
df = pd.read_csv("SurveyResponses_DigitalSecurityAroundTheWorld.csv", low_memory=False)
print(df.shape)          # (12351, 248)
print(df.columns[:15])

# 2) Nombres de columna  ⚠️ IMPORTANTE
#    Los bloques de preguntas están en MINÚSCULA: q6r1, q7r3, q20r5 ...
#    Solo estas 7 van con mayúscula/capitalización:
#    ID, Country, Gender, Age, Education, Ethnicity, Gender_SelfDescription
#    Q18 y Q19 llevan letra de sub-batería: q18ar1..q18ar8, q18br9..q18br19,
#    q19ar1..q19ar8, q19br9..q19br19.

# 3) Valores faltantes / no-respuesta  ⚠️ LEER
#    En ESTE CSV la no-respuesta ya viene como celda vacía (NaN); el código 9999
#    del cuestionario NO está en los datos (solo aparece como número en la columna ID).
#    No hay que convertir 9999 a NaN. Verifícalo tú mismo:
assert (df.drop(columns=["ID"]) == 9999).sum().sum() == 0
#    Diagnostica el faltante real por variable:
faltante = df.isna().mean().mul(100).round(1).sort_values(ascending=False)
print(faltante.head(15))   # Ethnicity ~91.5%, Age ~24.9%, q9* ~7% ...

# 4) Limpieza de la celda de texto en una columna numérica
#    q4r8 tiene una respuesta de texto ("getting my information") entre códigos 1–8.
df["q4r8"] = pd.to_numeric(df["q4r8"], errors="coerce")

# 5) Etiquetas útiles (país)
paises = {1:"China",2:"Alemania",3:"India",4:"Israel",5:"Italia",6:"México",
          7:"Polonia",8:"Arabia Saudita",9:"Sudáfrica",10:"Suecia",11:"Reino Unido",12:"EE.UU."}
df["Country_name"] = df["Country"].map(paises)

# 6) Ethnicity solo tiene datos para EE. UU. (Country == 12): ~1.051 válidos, 0 en el resto.
```

**Advertencias de análisis (leer antes de empezar):**

- **Nombres en minúscula.** `df["Q6r1"]` da `KeyError`; la columna es `df["q6r1"]`. Copia los nombres desde `df.columns`, no desde el data map.
- **La no-respuesta es NaN, no 9999.** El export ya la dejó vacía. Trata los NaN con criterio (imputar, excluir por listas, etc.) y documenta la decisión; no busques 9999.
- **Una celda de texto en `q4r8`** ("getting my information") obliga a `pd.to_numeric(..., errors="coerce")`. Es el único caso de texto en columnas numéricas — un ejemplo real de suciedad de datos para la Semana 5.
- **Muchas variables son escalas Likert 1–5**, no continuas puras. Justifica si las tratas como intervalares (media/SD, paramétrico) u ordinales (mediana, no paramétrico).
- **Hay ítems con redacción invertida** (afirmaciones que son *misconceptions*): un "muy de acuerdo" puede significar *menos* conocimiento. Invierte la codificación donde corresponda antes de sumar constructos (ver diccionario).
- **n muy grande (12.351):** casi cualquier prueba saldrá "significativa". A nivel doctoral, **reporta tamaños del efecto e intervalos de confianza como información primaria** — el valor p es secundario (ver el problema analítico rector).
- **`Ethnicity` solo aplica a EE. UU.** (91.5% NaN global); trátala como faltante estructural fuera de EE. UU.
- **El dataset es transversal (una sola ola):** no tiene componente temporal. Tenlo en cuenta al elegir la técnica avanzada de la Parte 2 (la Opción 2, series temporales, no es aplicable).

---

*Diccionario completo en [`diccionario-variables.md`](diccionario-variables.md) · problema rector en
[`problema-analitico-rector.md`](problema-analitico-rector.md). Referencias del entorno en
[`../../docs/bibliografia.md`](../../docs/bibliografia.md).*
