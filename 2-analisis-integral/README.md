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
| `SurveyResponses_DigitalSecurityAroundTheWorld.csv` | **Dataset oficial de la cohorte.** ~12.000 filas × ~200 columnas. |
| [`diccionario-variables.md`](diccionario-variables.md) | Diccionario de variables: bloques, escalas, códigos de valor y variables clave para el análisis. |
| [`problema-analitico-rector.md`](problema-analitico-rector.md) | Problema analítico rector que orienta los análisis **sin prescribir métodos**. |
| `DataMap_DigitalSecurityAroundTheWorld.pdf` | Data map oficial de los autores (redacción literal de cada pregunta). *(Opcional, de los autores.)* |

## Fuente y contexto de recolección

- **Autoría:** Franziska Herbert, Steffen Becker, Jonas Hielscher, Collins W. Munyendo, Yixin Zou y colaboradores — Ruhr-Universität Bochum y Max Planck Institute for Security and Privacy (Alemania).
- **Repositorio (FAIR):** ReSeeD, Ruhr-Universität Bochum. ID `zw12z533j`. https://rdms.rd.ruhr-uni-bochum.de/concern/datasets/zw12z533j
- **Recolección:** encuesta en línea, finales de **2021**. Objetivo de **1.000 participantes por país** en **12 países** de cuatro continentes: China, Alemania, India, Israel, Italia, México, Polonia, Arabia Saudita, Sudáfrica, Suecia, Reino Unido y EE. UU. (n total ≈ 12.000; el estudio reporta N = 12.351 antes de depuración).
- **Diseño del estudio original:** encuesta transversal de una sola ola. Los autores **buscaron** cuotas representativas por país en edad, género y educación; según reportan en CHI 2023, las cuotas de **educación no se alcanzaron en varios países**, y la cuota de etnia solo fue representativa para EE. UU. Trata la muestra como *aproximadamente* representativa y documenta esta limitación en tu reporte. Corte analítico **WEIRD vs. no-WEIRD** (7 países occidentales vs. 5 no occidentales) usado en la publicación de USENIX 2025.

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

# 1) Carga (el CSV suele venir en UTF-8; si falla, prueba encoding="latin-1")
df = pd.read_csv("SurveyResponses_DigitalSecurityAroundTheWorld.csv")
print(df.shape)          # ~ (12000, ~200)
print(df.columns[:15])

# 2) Códigos de valor perdido / no-respuesta  ⚠️ IMPORTANTE
#    9999 = "prefiero no responder" (demografía, Q7, Q25, Q26)
#         = "no entiendo la afirmación" (baterías Likert Q9–Q19)
#    NO es un valor válido de la escala: conviértelo a NaN antes de analizar.
df = df.replace(9999, np.nan)

# 3) Pregunta de control de calidad
#    Q13r11 pide marcar una opción específica ("segunda opción desde la derecha/abajo").
#    Úsala para detectar respuestas de baja calidad y documenta tu criterio de exclusión.
#    (Revisa en el diccionario el valor esperado antes de filtrar.)

# 4) Etiquetas útiles (ejemplo de país)
paises = {1:"China",2:"Alemania",3:"India",4:"Israel",5:"Italia",6:"México",
          7:"Polonia",8:"Arabia Saudita",9:"Sudáfrica",10:"Suecia",11:"Reino Unido",12:"EE.UU."}
df["Country_name"] = df["Country"].map(paises)

# 5) Recuerda: [Ethnicity] solo tiene datos para la submuestra de EE. UU.

# 6) Confía en los encabezados reales del CSV, no en la numeración impresa del data map
#    (ver advertencia sobre Q6r8 / Q6r18 en el diccionario).
print([c for c in df.columns if c.startswith("Q6")])
```

**Advertencias de análisis (leer antes de empezar):**

- **Muchas variables son escalas Likert 1–5**, no continuas puras. Justifica en tu notebook si las tratas como intervalares (media/SD, paramétrico) u ordinales (mediana, no paramétrico).
- **Hay ítems con redacción invertida** (afirmaciones que son *misconceptions*): un "muy de acuerdo" puede significar *menos* conocimiento. Revisa el diccionario e **invierte la codificación** donde corresponda antes de sumar constructos.
- **n muy grande (~12.000):** casi cualquier prueba saldrá "significativa". A nivel doctoral, **reporta tamaños del efecto e intervalos de confianza como información primaria** — el valor p es secundario (ver el problema analítico rector).
- **`[Ethnicity]` solo aplica a EE. UU.**; tratar como faltante estructural en el resto.
- **El dataset es transversal (una sola ola de recolección):** no tiene componente temporal. Tenlo en cuenta al elegir la técnica avanzada de la Parte 2.

---

*Diccionario completo en [`diccionario-variables.md`](diccionario-variables.md) · problema rector en
[`problema-analitico-rector.md`](problema-analitico-rector.md). Referencias del entorno en
[`../../docs/bibliografia.md`](../../docs/bibliografia.md).*
