# Diccionario de variables

Diccionario **curado y orientado al análisis** del dataset *Digital Security Perceptions &
Practices in 12 Countries*. Agrupa las 248 columnas por bloque temático, indica escala,
códigos de valor y señala las variables más útiles para cada tipo de análisis del Ciclo 2.

> La **redacción literal** de cada ítem está en el `DataMap` oficial de los autores. Aquí se
> prioriza la estructura analítica: convención de nombres, escalas, faltantes y rol
> potencial de cada bloque. **Los nombres de columna de este diccionario coinciden con los
> encabezados reales del CSV** (verificados sobre el archivo de la cohorte).

## Convenciones

- **Mayúsculas/minúsculas:** solo 7 columnas van capitalizadas — `ID`, `Country`, `Gender`, `Age`, `Education`, `Ethnicity`, `Gender_SelfDescription`. **Todos los bloques de preguntas van en minúscula:** `q1r1`, `q6r3`, `q20r5`, etc.
- **Patrón de nombres:** `q{n}r{m}` (p. ej. `q6r3` = bloque Q6, ítem 3). Excepción: `q18` y `q19` incluyen la letra de sub-batería → `q18ar1`–`q18ar8`, `q18br9`–`q18br19`, `q19ar1`–`q19ar8`, `q19br9`–`q19br19`.
- **Faltantes / no-respuesta:** vienen como **celda vacía (NaN)**. El código `9999` del cuestionario **no** está en los datos exportados (solo aparece como número en `ID`). No hay que convertir 9999 a NaN.
- **Binarias de selección múltiple:** `0` = no marcado, `1` = marcado.
- **`Ethnicity`** solo tiene datos válidos para la submuestra de **EE. UU.** (`Country == 12`); ~1.051 válidos, 0 en el resto (91.5% NaN global).
- **Orden de columnas:** en algunos bloques el ítem `r1` aparece **al final** del bloque en el CSV (p. ej. `q8r1` va tras `q8r10`; `q20r1` va tras `q20r14`). No selecciones por posición: usa el nombre de la columna.

> ⚠️ **Errata en el data map (no en el CSV).** El PDF del data map etiqueta el ítem "Tor
> network" como `q6r8`, cuando por posición corresponde a `q6r18` (el ítem real `q6r8` es
> "Data leak / data theft"). **El CSV está correcto**: trae las 22 columnas `q6r1`…`q6r22`
> consecutivas y bien ubicadas. Verifica el contenido de cada ítem en el data map con
> cuidado, pero confía en los encabezados del CSV.

## Identificadores y demografía

| Variable | Descripción | Escala / códigos | Rol analítico |
|---|---|---|---|
| `ID` | Numeración consecutiva del participante | entero | identificador |
| `Country` | País | 1=China, 2=Alemania, 3=India, 4=Israel, 5=Italia, 6=México, 7=Polonia, 8=Arabia Saudita, 9=Sudáfrica, 10=Suecia, 11=Reino Unido, 12=EE.UU. | **factor clave** (12 grupos; base del corte WEIRD/no-WEIRD) |
| `Gender` | Género | 1=Masc., 2=Fem., 3=No binario, 4=autodescripción (NaN si NR) | factor |
| `Gender_SelfDescription` | Autodescripción de género | texto libre (283 no nulos) | cualitativa |
| `Age` | Rango de edad | 1=18–24, 2=25–39, 3=40–54, 4=55+ (≈24.9% NaN) | ordinal |
| `Education` | Nivel educativo | 1=Bajo, 2=Medio, 3=Alto, 4=Otro | ordinal |
| `Ethnicity` | Raza (**solo EE. UU.**) | 1=Blanca, 2=Afroamericana, 3=Hispana/Latina, 4=Asiática, 5=Otra | factor (US) |

## Uso de tecnología (contexto)

| Bloque | Tema | Ítems | Escala |
|---|---|---|---|
| `q1r1`–`q1r7` | Dispositivos usados a diario (smartphone, PC, laptop, tablet, altavoz, wearable, ninguno) | 7 | binaria 0/1 |
| `q2r1`–`q2r3` | Dispositivos de hogar inteligente (energía, seguridad, hogar/jardín) | 3 | 1=Sí, 2=No, 3=No estoy seguro |
| `q3r1`–`q3r13` | Frecuencia de uso de internet por propósito (compras, banca, salud, etc.) | 13 | 1=Nunca … 8=Varias veces al día |
| `q4r1`–`q4r8` | Frecuencia de canales de comunicación (llamadas, video, SMS, messenger, redes, email, foros) | 8 | 1=Nunca … 8=Varias veces al día |

> `q4r8` contiene **una** celda de texto ("getting my information") entre los códigos 1–8.
> Conviértela con `pd.to_numeric(df["q4r8"], errors="coerce")` antes de analizar.

## Conocimiento y experiencia

| Bloque | Tema | Ítems | Escala | Rol analítico |
|---|---|---|---|---|
| `q6r1`–`q6r22` | **Familiaridad con términos** (malware, ransomware, phishing, 2FA, HTTPS, VPN, Tor, etc.) | 22 | 1=Nunca oído … 5=Sé muy bien cómo funciona | índice de **conocimiento** (candidato a VD continua o a PCA/factorial) |
| `q7r1`–`q7r9` | **Víctima de cibercrimen** (malware, phishing, ransomware, ciberacoso, fraude, etc.) | 9 | 1=Sí, 2=No (NaN si NR) | **variable binaria natural** → regresión logística (Semana 8) |
| `q8r1`–`q8r10` | Fuentes de información sobre seguridad | 10 (+texto `q8r10oer1`, 575 no nulos) | binaria 0/1 | comportamiento |

> En el CSV, `q8r1` ("no busco información") aparece **después** de `q8r10`. Selecciónalo por nombre.

## Concepciones y (mis)concepciones — baterías Likert de acuerdo

Todas en escala **1=totalmente en desacuerdo … 5=totalmente de acuerdo** (NaN = no entiende/NR).
⚠️ **Muchos ítems son afirmaciones falsas (misconceptions):** en esos, mayor acuerdo = *menor*
conocimiento real. **Identifica e invierte** los ítems inversos antes de construir índices.

| Bloque | Tema | Ítems |
|---|---|---|
| `q9r1`–`q9r9` | Cifrado extremo a extremo (E2EE, WhatsApp/Signal) | 9 |
| `q10r1`–`q10r5` | HTTPS / navegación segura | 5 |
| `q11r1`–`q11r5` | Redes WLAN públicas | 5 |
| `q12r1`–`q12r8` | VPN y red Tor | 8 |
| `q13r1`–`q13r18` | Contraseñas y procesos de login (incluye 2FA, biometría) | 18 |
| `q14r1`–`q14r9` | Seguridad de dispositivos finales | 9 |
| `q15r1`–`q15r16` | Malware y engaño en internet | 16 |
| `q16r1`–`q16r6` | Modo incógnito / navegación privada | 6 |

> **Pregunta de control:** `q13r11` **no** mide seguridad — pide marcar una opción específica
> ("la segunda opción desde la derecha / desde abajo"). En este CSV la respuesta mayoritaria
> es `4` (11.296 casos) y hay `5` (1.054) y un único `2`. Úsala para **detectar respuestas de
> baja calidad**: define tu criterio de exclusión a partir de esta distribución real (p. ej.
> conservar solo quienes marcaron el valor esperado) y **documéntalo**. No la incluyas en
> ningún índice de conocimiento.

## Importancia, preocupación y actitudes

Escalas 1–5; NaN = "no entiendo la afirmación" / NR (aplica a `q17`, `q18a/q18b` y `q19a/q19b`).

| Bloque | Tema | Ítems | Escala |
|---|---|---|---|
| `q17r1`–`q17r15` | Importancia de **prevenir** amenazas (malware, fraude, acceso no autorizado, etc.) | 15 | 1=Nada … 5=Muy importante |
| `q18ar1`–`q18ar8` (Q18A) | **Preocupación** por comunicaciones, WLAN, ubicación, biometría | 8 | 1=Nada … 5=Muy preocupado |
| `q18br9`–`q18br19` (Q18B) | **Preocupación** por contraseñas, equipo, malware, asistentes de voz | 11 | 1=Nada … 5=Muy preocupado |
| `q19ar1`–`q19ar8` (Q19A) | **Actitudes** hacia privacidad/cifrado ("nada que ocultar", etc.) | 8 | 1=Totalmente en desacuerdo … 5=Totalmente de acuerdo |
| `q19br9`–`q19br19` (Q19B) | **Actitudes**: ventajas del cifrado, fatalismo, molestia, usabilidad | 11 | 1–5 |

## Comportamiento protector y valor de los datos

| Bloque | Tema | Ítems | Escala | Rol analítico |
|---|---|---|---|---|
| `q20r1`–`q20r14` | **Medidas de protección usadas** (updates, backups, antivirus, 2FA, VPN, gestor de contraseñas, etc.) | 14 | binaria 0/1 | índice de **comportamiento protector** (suma 0–14 → VD continua) |
| `q21r1`–`q21r15` | Importancia de proteger tipos de dato (nombre, dirección, salud, biometría, contraseñas, etc.) | 15 | 1=Nada … 5=Muy importante | valor percibido |
| `q22r1`–`q22r8` | Riesgo percibido por actor (familia, colegas, gobierno propio/extranjero, empresas, criminales, hackers) | 8 | 1=Nada … 5=Muy probable | percepción de amenaza |

> En el CSV, `q20r1` ("ninguna medida") aparece **después** de `q20r14`. Selecciónalo por nombre.

## Variables de segmentación adicionales

| Variable | Descripción | Códigos |
|---|---|---|
| `q25` | Experiencia práctica en informática / TI (trabajo o formación) | 1=Sí, 2=No (NaN si NR) |
| `q26` | Trasfondo migratorio | 1=Sí, 2=No (NaN si NR) |

## Variables sugeridas por tipo de análisis

- **Comparación de grupos (Semana 6):** `Country` (12 grupos → ANOVA/Kruskal-Wallis); corte WEIRD vs. no-WEIRD, `q25`, `q26`, `Gender` (2–3 grupos → t-test/Mann-Whitney).
- **Regresión lineal múltiple (Semana 7):** VD continua = índice de conocimiento (media de `q6r1`–`q6r22`) o comportamiento protector (suma de `q20r1`–`q20r14`); predictores = demografía + `q25` + uso de internet (`q3`).
- **Regresión logística (Semana 8):** VD binaria natural = cualquier ítem de `q7` (víctima de cibercrimen Sí/No); o dicotomizar un índice con umbral justificado.
- **Multivariante / SEM / factorial (Parte 2, Opción 1):** las baterías Likert (`q6`, `q9`–`q19b`) son candidatas naturales a PCA/AFE/AFC; modelo estructural plausible: actitudes (`q19`) → comportamiento (`q20`), con conocimiento (`q6`) como antecedente.
- **Inferencia bayesiana (Parte 2, Opción 3):** reformular en PyMC cualquiera de las comparaciones o regresiones de la Parte 1.
- **Evaluación estadística de ML (Parte 2, Opción 4):** clasificación de victimización (`q7`) o de adopción de una medida (`q20`) con ≥3 clasificadores.
- **Series temporales (Parte 2, Opción 2):** **no aplicable** a este dataset, que es transversal y no tiene variable de tiempo.

---

*La redacción íntegra de cada ítem está en el `DataMap` oficial de los autores. Cualquier
decisión de recodificación (inversión de ítems, umbrales, exclusiones por la pregunta de
control) debe documentarse en el notebook.*
